---
title: 'Postupy: poskytování asynchronní služby | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e57de7ca683678441b4e0908110e8e651930b64
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061618"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Postupy: poskytovat služby asynchronní aplikace Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete získat službu bez blokování vlákna uživatelského rozhraní, by měl vytvořit asynchronní služby a načíst balíček ve vlákně na pozadí. K tomuto účelu můžete použít <xref:Microsoft.VisualStudio.Shell.AsyncPackage> spíše než <xref:Microsoft.VisualStudio.Shell.Package>a přidejte službu s asynchronní balíček speciální asynchronní metody

 Informace o poskytování služeb synchronní sady Visual Studio najdete v tématu [postupy: poskytování služby](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Implementace asynchronní služby

1.  Vytvořte projekt VSIX (**soubor / nový / Project / Visual C# / Extensiblity / projekt VSIX**). Pojmenujte projekt **TestAsync**.

2.  Přidejte do projektu VSPackage. Vyberte uzel projektu v **Průzkumníka řešení** a klikněte na tlačítko **přidat / nová položku / položky Visual C# / rozšiřitelnost / balíček Visual Studio**. Název tohoto souboru **TestAsyncPackage.cs**.

3.  V TestAsyncPackage.cs změňte balíček, který má Zdědit z AsyncPackage spíše než balíček:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4.  K implementaci služby, je potřeba vytvořit tři typy:

    -   Rozhraní, který popisuje službu. Mnohé z těchto rozhraní jsou prázdné, to znamená, že mají žádné metody.

    -   Rozhraní, které popisují rozhraní služby. Toto rozhraní obsahuje metody k implementaci.

    -   Třída, která implementuje služba a služba rozhraní.

5.  Následující příklad ukazuje velmi základní implementaci ze tří typů. Konstruktor třídy služeb, musíte nastavit poskytovatele služeb. V tomto příkladu pouze přidáme služby v kódu souboru balíčku.

6.  Přidejte následující příkazy using do souboru balíčku:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7.  Tady je implementace asynchronní služby. Všimněte si, že je potřeba nastavit asynchronní poskytovatele místo synchronní poskytovatele v konstruktoru:

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>Registrace služby
 Chcete-li zaregistrovat služby, přidejte <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do balíčku, který poskytuje služby. Existují dva rozdíly v registraci synchronní služby:

- Pokud jste autoloading balíček, je nutné přidat <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad hodnotu atributu. Další informace o rozšíření VSPackages autoloading najdete v tématu [načítání rozšíření VSPackages](../extensibility/loading-vspackages.md).

- Je nutné přidat **AllowsBackgroundLoading = true** pole <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Další informace o PackageRegistrationAttribute najdete v tématu [registrace a zrušení registrace rozšíření VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

  Tady je příklad z AsyncPackage registraci asynchronní služby::

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Přidání služeb

1.  V TestAsyncPackage.cs, odeberte `Initialize()` metoda a přepsání `InitializeAsync()` metody. Přidání služby a přidejte metodu zpětného volání pro vytvoření služeb. Tady je příklad asynchronní inicializátoru pro přidání služby:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2.  Přidejte odkaz na Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.

3.  Jako asynchronní metodu, která vytvoří a vrátí službu implementujte metodu zpětného volání.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>Pomocí služby
 Nyní můžete získat službu a použijte její metody.

1.  Ukážeme to v inicializátoru, ale můžete získat službu kamkoli chcete používat službu.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Nezapomeňte změnit  *\<userpath >* název souboru a cestu, která dává smysl ve vašem počítači!

2.  Sestavte a spusťte kód. Když se objeví experimentální instanci sady Visual Studio, otevřete řešení. To způsobí, že AsyncPackage k autoload. Po spuštění inicializátoru, měli byste najít soubor v zadaném umístění.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Použití asynchronního služby v obslužná rutina příkazu
 Tady je příklad toho, jak použít asynchronní služby v příkazu nabídky. Můžete použít k používání služby v jiné jiné asynchronní metody zde zobrazená procedura.

1.  Přidání příkazu nabídky do projektu. (V **Průzkumníku řešení**, vyberte uzel projektu, klikněte pravým tlačítkem a vyberte **Add / nová položka / rozšiřitelnost / vlastní příkaz**.) Název souboru příkazů **TestAsyncCommand.cs.**

2.  Šablona vlastního příkazu znovu přidá `Initialize()` metody do souboru TestAsyncPackage.cs abyste inicializovali příkazu. V metodě Initialize() zkopírujte řádek, který inicializuje příkazu. By měl vypadat nějak takto:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Přesunutí tohoto řádku `InitializeAsync()` metody v souboru AsyncPackageForService.cs. Protože jde o asynchronní inicializace, před inicializací pomocí příkazu, je nutné přepnout do hlavního vlákna <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. To by teď měl vypadat takto:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3.  Odstranit `Initialize()` metody.

4.  V souboru TestAsyncCommand.cs vyhledejte `MenuItemCallback()` metody. Odstranění těla metody.

5.  Přidat sadu pomocí příkazu:

    ```
    using System.IO;
    ```

6.  Přidat metodu s názvem `GetAsyncService()`, který získá službu a používá jeho metody:

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7.  Volejte tuto metodu z `MenuItemCallback()` metody:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8.  Sestavte řešení a spusťte ladění. Když se objeví experimentální instanci sady Visual Studio, přejděte na **nástroje** nabídky a vyhledat **vyvolat TestAsyncCommand** položky nabídky. Po kliknutí na to, TextWriterService zapíše do souboru, který jste zadali. (Není nutné pro otevření řešení, protože volání příkazu zároveň způsobí, že balíček, který má načíst.)

## <a name="see-also"></a>Viz také
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)
