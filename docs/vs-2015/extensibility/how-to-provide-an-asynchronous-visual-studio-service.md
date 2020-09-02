---
title: 'Postupy: poskytnutí asynchronní služby | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204106"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Postupy: Poskytování asynchronní služby sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete získat službu bez blokování vlákna uživatelského rozhraní, měli byste vytvořit asynchronní službu a načíst balíček do vlákna na pozadí. Pro tento účel můžete použít <xref:Microsoft.VisualStudio.Shell.AsyncPackage> spíše než a <xref:Microsoft.VisualStudio.Shell.Package> a přidat službu s speciálními asynchronními metodami pro asynchronní balíčky.

 Informace o tom, jak zajistit synchronní služby sady Visual Studio, naleznete v tématu [How to: Service](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Implementace asynchronní služby

1. Vytvořte projekt VSIX (**soubor/nový/projekt/Visual C#/Extensiblity/VSIX projekt**). Pojmenujte projekt **TestAsync**.

2. Přidejte do projektu VSPackage. Vyberte uzel projektu v **Průzkumník řešení** a klikněte na **přidat/nová položka/Visual C# položky/rozšiřitelnost/balíček sady Visual Studio**. Pojmenujte tento soubor **TestAsyncPackage.cs**.

3. V TestAsyncPackage.cs změňte balíček tak, aby dědil z AsyncPackage namísto balíčku:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Chcete-li implementovat službu, je nutné vytvořit tři typy:

    - Rozhraní, které popisuje službu. Mnohé z těchto rozhraní jsou prázdné, to znamená, že nemají žádné metody.

    - Rozhraní, které popisuje rozhraní služby. Toto rozhraní zahrnuje metody, které mají být implementovány.

    - Třída, která implementuje službu i rozhraní služby.

5. Následující příklad ukazuje velmi základní implementaci tří typů. Konstruktor třídy služby musí nastavit poskytovatele služby. V tomto příkladu stačí přidat službu do souboru s kódem balíčku.

6. Přidejte následující příkazy using do souboru balíčku:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. Tady je implementace asynchronní služby. Všimněte si, že musíte nastavit asynchronního poskytovatele služeb, nikoli synchronního poskytovatele služeb v konstruktoru:

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
 Chcete-li zaregistrovat službu, přidejte do <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> balíčku, který poskytuje službu. Existují dva rozdíly od registrace synchronní služby:

- Pokud zadáváte automatické načítání balíčku, musíte <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> do atributu přidat hodnotu BackgroundLoad. Další informace o automatickém načítání VSPackage naleznete v tématu [načítání VSPackage](../extensibility/loading-vspackages.md).

- Je nutné přidat pole **AllowsBackgroundLoading = true** do <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . Další informace o PackageRegistrationAttribute najdete v tématu [registrace a zrušení registrace VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

  Tady je příklad AsyncPackage s asynchronní registrací služby:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Přidání služby

1. V TestAsyncPackage.cs odeberte `Initialize()` metodu a přepište `InitializeAsync()` metodu. Přidejte službu a přidejte metodu zpětného volání, která vytvoří služby. Tady je příklad asynchronního inicializátoru, který přidává službu:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Přidejte odkaz na Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.

3. Implementujte metodu zpětného volání jako asynchronní metodu, která vytvoří a vrátí službu.

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

## <a name="using-a-service"></a>Používání služby
 Nyní můžete získat službu a použít její metody.

1. Tato možnost se zobrazí v inicializátoru, ale můžete ji získat kdekoli, kde chcete službu používat.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Nezapomeňte změnit *\<userpath>* na název souboru a cestu, která dává smysl na vašem počítači.

2. Sestavte a spusťte kód. Po zobrazení experimentální instance aplikace Visual Studio otevřete řešení. Tím dojde k automatickému načtení AsyncPackage. Po spuštění inicializátoru byste měli najít soubor v zadaném umístění.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Použití asynchronní služby v obslužné rutině příkazu
 Tady je příklad použití asynchronní služby v příkazu nabídky. Můžete použít postup, který je zde uveden, chcete-li službu použít v jiných neasynchronních metodách.

1. Přidejte do projektu příkaz nabídky. (V **Průzkumník řešení**vyberte uzel projektu, klikněte pravým tlačítkem myši a vyberte **přidat/nová položka/rozšiřitelnost/vlastní příkaz**.) Pojmenujte soubor příkazů **TestAsyncCommand.cs.**

2. Vlastní šablona příkazu znovu přidá `Initialize()` metodu do souboru TestAsyncPackage.cs, aby bylo možné příkaz inicializovat. V metodě Initialize () zkopírujte řádek, který inicializuje příkaz. Měl by vypadat takto:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Přesune tento řádek do `InitializeAsync()` metody v souboru AsyncPackageForService.cs. Vzhledem k tomu, že se jedná o asynchronní inicializaci, je nutné přepnout do hlavního vlákna před inicializací příkazu pomocí <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Teď by měl vypadat takto:

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

3. Odstraňte `Initialize()` metodu.

4. V souboru TestAsyncCommand.cs vyhledejte `MenuItemCallback()` metodu. Odstraňte tělo metody.

5. Přidejte příkaz using:

    ```
    using System.IO;
    ```

6. Přidejte asynchronní metodu s názvem `GetAsyncService()` , která získá službu a použije její metody:

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

7. Zavolejte tuto metodu z `MenuItemCallback()` metody:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. Sestavte řešení a spusťte ladění. Po zobrazení experimentální instance sady Visual Studio přejděte do nabídky **nástroje** a vyhledejte položku nabídky **vyvolání TestAsyncCommand** . Když na něj kliknete, TextWriterService zapíše do souboru, který jste zadali. (Nemusíte otevřít řešení, protože vyvolání příkazu také způsobí, že se balíček načte.)

## <a name="see-also"></a>Viz také
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)
