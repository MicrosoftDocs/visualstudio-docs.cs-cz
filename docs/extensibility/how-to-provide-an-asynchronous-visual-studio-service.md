---
title: 'Postupy: poskytnutí asynchronní služby sady Visual Studio | Microsoft Docs'
description: Přečtěte si, jak poskytnout asynchronní službu sady Visual Studio. Tento přístup umožňuje získat službu bez blokování vlákna uživatelského rozhraní.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9973bb86296442f4b936ddb54ff645d74d7ab74
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074935"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Postupy: poskytnutí asynchronní služby sady Visual Studio
Pokud chcete získat službu bez blokování vlákna uživatelského rozhraní, měli byste vytvořit asynchronní službu a načíst balíček do vlákna na pozadí. Pro tento účel můžete použít <xref:Microsoft.VisualStudio.Shell.AsyncPackage> spíše než a <xref:Microsoft.VisualStudio.Shell.Package> a přidat službu s speciálními asynchronními metodami pro asynchronní balíčky.

 Informace o tom, jak zajistit synchronní služby sady Visual Studio, naleznete v tématu [How to: Service](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementace asynchronní služby

1. Vytvořte projekt VSIX (**soubor**  >  **Nový**  >  **projekt** projektu  >  **VSIX Visual C#**  >  **Extensiblity**  >  ). Pojmenujte projekt **TestAsync**.

2. Přidejte do projektu VSPackage. Vyberte uzel projektu v **Průzkumník řešení** a klikněte na tlačítko **Přidat**  >  **novou položku**  >  **Visual C# položky**  >  **rozšiřitelný**  >  **balíček sady Visual Studio**. Pojmenujte tento soubor *TestAsyncPackage. cs*.

3. V *TestAsyncPackage. cs* změňte balíček tak, aby byl zděděný, a `AsyncPackage` ne `Package` :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Chcete-li implementovat službu, je nutné vytvořit tři typy:

    - Rozhraní, které identifikuje službu. Mnohé z těchto rozhraní jsou prázdné, to znamená, že nemají žádné metody, protože se používají pouze k dotazování služby.

    - Rozhraní, které popisuje rozhraní služby. Toto rozhraní zahrnuje metody, které mají být implementovány.

    - Třída, která implementuje službu i rozhraní služby.

5. Následující příklad ukazuje velmi základní implementaci tří typů. Konstruktor třídy služby musí nastavit poskytovatele služby. V tomto příkladu stačí přidat službu do souboru s kódem balíčku.

6. Do souboru balíčku přidejte následující direktivy using:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Tady je implementace asynchronní služby. Všimněte si, že musíte nastavit asynchronního poskytovatele služeb, nikoli synchronního poskytovatele služeb v konstruktoru:

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
 Chcete-li zaregistrovat službu, přidejte do <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> balíčku, který poskytuje službu. Rozdíl od registrace synchronní služby je nutné zajistit, aby balíček i služba podporovaly asynchronní načítání:

- Chcete-li zajistit asynchronní inicializaci balíčku pro další informace o PackageRegistrationAttribute, je nutné přidat do pole **AllowsBackgroundLoading = true** <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . Další informace o naleznete v tématu [Register and Unregistering VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Abyste mohli zajistit asynchronní inicializaci instance služby, musíte do ní přidat pole **IsAsyncQueryable = true** <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .

  Tady je příklad `AsyncPackage` s asynchronní registrací služby:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Přidat službu

1. V *TestAsyncPackage. cs* odeberte `Initialize()` metodu a přepište `InitializeAsync()` metodu. Přidejte službu a přidejte metodu zpětného volání, která vytvoří služby. Tady je příklad asynchronního inicializátoru, který přidává službu:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Chcete-li tuto službu zviditelnit mimo tento balíček, nastavte jako poslední parametr hodnotu příznak zvýšení na hodnotu *true* :  `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Přidejte odkaz na *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

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
 Nyní můžete získat službu a použít její metody.

1. Tato možnost se zobrazí v inicializátoru, ale můžete ji získat kdekoli, kde chcete službu používat.

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

     Nezapomeňte změnit `userpath` na název souboru a cestu, která dává smysl na vašem počítači.

2. Sestavte a spusťte kód. Po zobrazení experimentální instance aplikace Visual Studio otevřete řešení. Tím dojde `AsyncPackage` k automatickému načtení. Po spuštění inicializátoru byste měli najít soubor v zadaném umístění.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Použít asynchronní službu v obslužné rutině příkazu
 Tady je příklad použití asynchronní služby v příkazu nabídky. Můžete použít postup, který je zde uveden, chcete-li službu použít v jiných neasynchronních metodách.

1. Přidejte do projektu příkaz nabídky. (V **Průzkumník řešení** vyberte uzel projektu, klikněte pravým tlačítkem myši a vyberte Přidat.   >  **Nová položka**  >  **Rozšiřitelnost**  >  **Vlastní příkaz**.) Pojmenujte soubor příkazů *TestAsyncCommand. cs*.

2. Vlastní šablona příkazu znovu přidá `Initialize()` metodu do souboru *TestAsyncPackage. cs* , aby bylo možné příkaz inicializovat. V `Initialize()` metodě zkopírujte řádek, který inicializuje příkaz. Měl by vypadat takto:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Přesune tento řádek do `InitializeAsync()` metody v souboru *AsyncPackageForService. cs* . Vzhledem k tomu, že se jedná o asynchronní inicializaci, je nutné přepnout do hlavního vlákna před inicializací příkazu pomocí <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Teď by měl vypadat takto:

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

4. V souboru *TestAsyncCommand. cs* Najděte `MenuItemCallback()` metodu. Odstraňte tělo metody.

5. Přidat direktivu using:

    ```csharp
    using System.IO;
    ```

6. Přidejte asynchronní metodu s názvem `UseTextWriterAsync()` , která získá službu a použije její metody:

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

7. Zavolejte tuto metodu z `MenuItemCallback()` metody:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Sestavte řešení a spusťte ladění. Po zobrazení experimentální instance sady Visual Studio přejděte do nabídky **nástroje** a vyhledejte položku nabídky **vyvolání TestAsyncCommand** . Když na něj kliknete, TextWriterService zapíše do souboru, který jste zadali. (Nemusíte otevřít řešení, protože vyvolání příkazu také způsobí, že se balíček načte.)

## <a name="see-also"></a>Viz také
- [Použití a poskytování služeb](../extensibility/using-and-providing-services.md)
