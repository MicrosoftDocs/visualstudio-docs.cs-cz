---
title: 'Postup: Poskytnutí asynchronní služby Visual Studio | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710756"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Postup: Poskytnutí asynchronní služby sady Visual Studio
Pokud chcete získat službu bez blokování vlákna uživatelského rozhraní, měli byste vytvořit asynchronní službu a načíst balíček ve vlákně na pozadí. Pro tento účel můžete <xref:Microsoft.VisualStudio.Shell.AsyncPackage> použít <xref:Microsoft.VisualStudio.Shell.Package>spíše než a , a přidat službu s asynchronní balíček speciální asynchronní metody.

 Informace o poskytování synchronních služeb sady Visual Studio naleznete v [tématu How to: Provide a service](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementace asynchronní služby

1. Vytvořte projekt VSIX **(Soubor** > **nového** > **projektu** > Visual**C#** > **Extensiblity** > **VSIX Project).** Název projektu **TestAsync**.

2. Přidejte VSPackage do projektu. V průzkumníku **řešení** vyberte uzel projektu a klepněte na tlačítko **Přidat** > **novou položku** > **Visual C# Položky** > **rozšiřitelnost** > **visual studio balíček**. Pojmenujte tento soubor *TestAsyncPackage.cs*.

3. V *TestAsyncPackage.cs*změňte balíček `AsyncPackage` dědit z spíše než `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Chcete-li implementovat službu, musíte vytvořit tři typy:

    - Rozhraní, které identifikuje službu. Mnoho z těchto rozhraní jsou prázdné, to znamená, že nemají žádné metody, protože se používají pouze pro dotazování služby.

    - Rozhraní, které popisuje rozhraní služby. Toto rozhraní zahrnuje metody, které mají být implementovány.

    - Třída, která implementuje službu a rozhraní služby.

5. Následující příklad ukazuje velmi základní implementaci těchto tří typů. Konstruktor třídy služby musí nastavit poskytovatele služeb. V tomto příkladu budeme jen přidat službu do souboru kódu balíčku.

6. Do souboru balíčku přidejte následující direktivy pomocí:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Zde je implementace asynchronní služby. Všimněte si, že je třeba nastavit asynchronního poskytovatele služeb, nikoli synchronního poskytovatele služeb v konstruktoru:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Registrace služby
 Chcete-li zaregistrovat <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> službu, přidejte balíček, který poskytuje službu. Liší se od registrace synchronní služby, musíte se ujistit, že balíček i služba podporují asynchronní načítání:

- Je nutné přidat **AllowsBackgroundLoading =** <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> true pole zajistit balíček lze inicializovat asynchronně Pro další informace o PackageRegistrationAttribute, naleznete v [tématu Registrovat a zrušit registraci VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Je nutné přidat **IsAsyncQueryable =** <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> true pole, abyste zajistili, že instance služby může být inicializována asynchronně.

  Zde je příklad `AsyncPackage` s asynchronní registrace služby:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Přidat službu

1. V *TestAsyncPackage.cs*metodu `Initialize()` odeberte `InitializeAsync()` a přepište metodu. Přidejte službu a přidejte metodu zpětného volání k vytvoření služeb. Zde je příklad asynchronníinizátor přidání služby:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Chcete-li, aby tato služba byla viditelná mimo tento balíček, nastavte hodnotu příznaku povýšení na *hodnotu true* jako poslední parametr:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Přidejte odkaz na *soubor Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Implementujte metodu zpětného volání jako asynchronní metodu, která vytvoří a vrátí službu.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Použití služby
 Nyní můžete získat službu a používat její metody.

1. Ukážeme to v inicializátoru, ale můžete získat službu kdekoli chcete službu používat.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     Nezapomeňte změnit `userpath` název souboru a cestu, která dává smysl na vašem počítači!

2. Sestavení a spuštění kódu. Když se zobrazí experimentální instance sady Visual Studio, otevřete řešení. To způsobí, `AsyncPackage` že automatické načtení. Po spuštění inicializátoru byste měli najít soubor v zadaném umístění.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Použití asynchronní služby v obslužné rutině příkazu
 Tady je příklad použití asynchronní služby v příkazu nabídky. Zde uvedený postup můžete použít k použití služby v jiných neasynchronních metodách.

1. Přidejte příkaz nabídky do projektu. (V **Průzkumníku řešení**vyberte uzel projektu, klepněte pravým tlačítkem myši a vyberte **přidat** > vlastní příkaz Přidat**novou** > položku**rozšiřitelnost** > **.)** Pojmenujte soubor příkazu *TestAsyncCommand.cs*.

2. Vlastní šablona příkazu `Initialize()` znovu přidá metodu do *souboru TestAsyncPackage.cs,* aby se příkaz inicializoval. V `Initialize()` metodě zkopírujte řádek, který inicializuje příkaz. Mělo by to vypadat takto:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Přesuňte tento `InitializeAsync()` řádek na metodu v *souboru AsyncPackageForService.cs.* Vzhledem k tomu, že se jedná o asynchronní inicializaci, je <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>nutné přepnout do hlavního vlákna před inicializací příkazu pomocí příkazu . Nyní by mělo vypadat takto:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Odstraňte `Initialize()` metodu.

4. V *souboru TestAsyncCommand.cs* `MenuItemCallback()` najděte metodu. Odstraňte tělo metody.

5. Přidejte direktivu using:

    ```csharp
    using System.IO;
    ```

6. Přidejte asynchronní metodu s názvem `UseTextWriterAsync()`, která získá službu a používá její metody:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Volání této metody `MenuItemCallback()` z metody:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Sestavte řešení a začněte ladit. Když se zobrazí experimentální instance sady Visual Studio, přejděte do nabídky **Nástroje** a vyhledejte položku nabídky **Invoke TestAsyncCommand.** Po klepnutí na něj TextWriterService zapíše do souboru, který jste zadali. (Není nutné otevřít řešení, protože vyvolání příkazu také způsobí, že balíček načíst.)

## <a name="see-also"></a>Viz také
- [Využívání a poskytování služeb](../extensibility/using-and-providing-services.md)
