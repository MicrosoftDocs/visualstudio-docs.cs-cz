---
title: 'Postupy: poskytnutí asynchronní služby sady Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d486aac8e990fef6b139bca989a51d74146ecb67
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826403"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Postupy: poskytnutí asynchronní služby sady Visual Studio
Pokud chcete získat službu bez blokování vlákna uživatelského rozhraní, by měl vytvořit asynchronní služby a načíst balíček ve vlákně na pozadí. Pro tento účel můžete místo <xref:Microsoft.VisualStudio.Shell.Package>použít <xref:Microsoft.VisualStudio.Shell.AsyncPackage> a službu přidat pomocí speciálních asynchronních metod pro asynchronní balíček.

 Informace o tom, jak zajistit synchronní služby sady Visual Studio, naleznete v tématu [How to: Service](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementace asynchronní služby

1. Vytvořte projekt VSIX (**soubor** > **Nový** > **projekt** > **Visual C#**  > **Extensiblity** > **VSIX**). Pojmenujte projekt **TestAsync**.

2. Přidejte do projektu VSPackage. Vyberte uzel projektu v **Průzkumník řešení** a klikněte na **Přidat** > **nové položky** > **vizuální C# položky** > **rozšíření** > **balíčku sady Visual Studio**. Název tohoto souboru *TestAsyncPackage.cs*.

3. V *TestAsyncPackage.cs*změňte balíček tak, aby dědil z `AsyncPackage` místo `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. K implementaci služby, je potřeba vytvořit tři typy:

    - Rozhraní, které identifikuje službu. Mnohé z těchto rozhraní jsou prázdné, to znamená, že nemají žádné metody, protože se používají pouze k dotazování služby.

    - Rozhraní, které popisují rozhraní služby. Toto rozhraní obsahuje metody k implementaci.

    - Třída, která implementuje služba a služba rozhraní.

5. Následující příklad ukazuje velmi základní implementaci ze tří typů. Konstruktor třídy služeb, musíte nastavit poskytovatele služeb. V tomto příkladu stačí přidat službu do souboru s kódem balíčku.

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

7. Tady je implementace asynchronní služby. Všimněte si, že je potřeba nastavit asynchronní poskytovatele místo synchronní poskytovatele v konstruktoru:

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
 Chcete-li zaregistrovat služby, přidejte <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do balíčku, který poskytuje služby. Rozdíl od registrace synchronní služby je nutné zajistit, aby balíček i služba podporovaly asynchronní načítání:

- Do <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> musíte přidat pole **AllowsBackgroundLoading = true** , abyste zajistili asynchronní inicializaci balíčku pro další informace o PackageRegistrationAttribute najdete v tématu [registrace a zrušení registrace VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

- Abyste mohli zajistit asynchronní inicializaci instance služby, musíte do <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> přidat pole **IsAsyncQueryable = true** .

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

1. V *TestAsyncPackage.cs*odeberte metodu `Initialize()` a přepište metodu `InitializeAsync()`. Přidání služby a přidejte metodu zpětného volání pro vytvoření služeb. Tady je příklad asynchronní inicializátoru pro přidání služby:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Pokud chcete tuto službu zviditelnit mimo tento balíček, jako poslední parametr nastavte hodnotu příznak zvýšení na *true* : `this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Přidejte odkaz na *Microsoft. VisualStudio. Shell. Interop. 14.0. designtime. dll*.

3. Jako asynchronní metodu, která vytvoří a vrátí službu implementujte metodu zpětného volání.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Použití služby
 Nyní můžete získat službu a použijte její metody.

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

2. Sestavte a spusťte kód. Když se objeví experimentální instanci sady Visual Studio, otevřete řešení. Tím dojde k automatickému načtení `AsyncPackage`. Po spuštění inicializátoru, měli byste najít soubor v zadaném umístění.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Použít asynchronní službu v obslužné rutině příkazu
 Tady je příklad použití asynchronní služby v příkazu nabídky. Můžete použít k používání služby v jiné jiné asynchronní metody zde zobrazená procedura.

1. Přidání příkazu nabídky do projektu. (V **Průzkumník řešení**vyberte uzel projektu, klikněte pravým tlačítkem myši a vyberte **Přidat** > **nová položka** > **rozšiřitelnost** > **vlastní příkaz**.) Pojmenujte soubor příkazů *TestAsyncCommand.cs*.

2. Vlastní šablona příkazu znovu přidá metodu `Initialize()` k souboru *TestAsyncPackage.cs* , aby mohl příkaz inicializovat. V metodě `Initialize()` zkopírujte řádek, který inicializuje příkaz. By měl vypadat nějak takto:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Přesune tento řádek do metody `InitializeAsync()` v souboru *AsyncPackageForService.cs* . Protože jde o asynchronní inicializace, před inicializací pomocí příkazu, je nutné přepnout do hlavního vlákna <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. To by teď měl vypadat takto:

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

3. Odstranit `Initialize()` metody.

4. V souboru *TestAsyncCommand.cs* vyhledejte metodu `MenuItemCallback()`. Odstranění těla metody.

5. Přidat direktivu using:

    ```csharp
    using System.IO;
    ```

6. Přidat metodu s názvem `UseTextWriterAsync()`, který získá službu a používá jeho metody:

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

7. Volejte tuto metodu z `MenuItemCallback()` metody:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Sestavte řešení a spusťte ladění. Když se objeví experimentální instanci sady Visual Studio, přejděte na **nástroje** nabídky a vyhledat **vyvolat TestAsyncCommand** položky nabídky. Po kliknutí na to, TextWriterService zapíše do souboru, který jste zadali. (Nemusíte otevřít řešení, protože vyvolání příkazu také způsobí, že se balíček načte.)

## <a name="see-also"></a>Viz také:
- [Použití a poskytování služeb](../extensibility/using-and-providing-services.md)
