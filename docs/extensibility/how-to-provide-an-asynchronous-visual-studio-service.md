---
title: 'Postupy: asynchronní Visual Studio Service poskytují | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c022f1a039aacee3599dd680adfa92a9404b34b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915669"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Postupy: poskytování asynchronní služby sady Visual Studio
Pokud chcete získat službu bez blokování vlákna uživatelského rozhraní, by měl vytvořit asynchronní služby a načíst balíček ve vlákně na pozadí. K tomuto účelu můžete použít <xref:Microsoft.VisualStudio.Shell.AsyncPackage> spíše než <xref:Microsoft.VisualStudio.Shell.Package>a přidejte službu s asynchronní balíček speciální asynchronní metody.
  
 Informace o poskytování služeb synchronní sady Visual Studio najdete v tématu [postupy: poskytování služby](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implement-an-asynchronous-service"></a>Implementace asynchronní služby  
  
1.  Vytvořte projekt VSIX (**souboru** > **nový** > **projektu** > **Visual C#**  >  **Extensiblity** > **projekt VSIX**). Pojmenujte projekt **TestAsync**.  
  
2.  Přidejte do projektu VSPackage. Vyberte uzel projektu v **Průzkumníka řešení** a klikněte na tlačítko **přidat** > **nová položka** > **položky Visual C#**  >  **Rozšiřitelnost** > **balíčku sady Visual Studio**. Název tohoto souboru *TestAsyncPackage.cs*.  
  
3.  V *TestAsyncPackage.cs*, změňte balíček, který má Zdědit `AsyncPackage` spíše než `Package`:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  K implementaci služby, je potřeba vytvořit tři typy:  
  
    -   Rozhraní, která identifikuje službu. Mnohé z těchto rozhraní jsou prázdné, to znamená, mají žádné metody, jak se používají pouze pro dotazování na službu.
  
    -   Rozhraní, které popisují rozhraní služby. Toto rozhraní obsahuje metody k implementaci.  
  
    -   Třída, která implementuje služba a služba rozhraní.  
  
5.  Následující příklad ukazuje velmi základní implementaci ze tří typů. Konstruktor třídy služeb, musíte nastavit poskytovatele služeb. V tomto příkladu pouze přidáme služby v kódu souboru balíčku.  
  
6.  Přidejte následující příkazy using do souboru balíčku:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  Tady je implementace asynchronní služby. Všimněte si, že je potřeba nastavit asynchronní poskytovatele místo synchronní poskytovatele v konstruktoru:  
  
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

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);               
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
 Chcete-li zaregistrovat služby, přidejte <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do balíčku, který poskytuje služby. Různé registraci synchronní služby, je nutné Ujistěte se, že balíček a služba podporuje asynchronní načítání:
  
- Je nutné přidat **AllowsBackgroundLoading = true** pole <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> k zajištění balíčku můžete pro další informace o PackageRegistrationAttribute inicializují asynchronně, naleznete v tématu [zaregistrovat a zrušení registrace rozšíření VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
- Je nutné přidat **IsAsyncQueryable = true** pole <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> zajistit instance služby mohou být inicializovány asynchronně.

  Tady je příklad `AsyncPackage` s registrací asynchronní služby:
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="add-a-service"></a>Přidat službu  
  
1.  V *TestAsyncPackage.cs*, odeberte `Initialize()` metoda a přepsání `InitializeAsync()` metody. Přidání služby a přidejte metodu zpětného volání pro vytvoření služeb. Tady je příklad asynchronní inicializátoru pro přidání služby:  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  Přidejte odkaz na *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.  
  
3.  Jako asynchronní metodu, která vytvoří a vrátí službu implementujte metodu zpětného volání.  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="use-a-service"></a>Použít službu  
 Nyní můžete získat službu a použijte její metody.  
  
1.  Ukážeme to v inicializátoru, ale můžete získat službu kamkoli chcete používat službu.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
    }  
  
    ```  
  
     Nezapomeňte změnit  *\<userpath >* název souboru a cestu, která dává smysl ve vašem počítači!  
  
2.  Sestavte a spusťte kód. Když se objeví experimentální instanci sady Visual Studio, otevřete řešení. To způsobí, že `AsyncPackage` chcete automaticky načíst. Po spuštění inicializátoru, měli byste najít soubor v zadaném umístění.  
  
## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Použít službu pro asynchronní v obslužná rutina příkazu  
 Tady je příklad toho, jak použít asynchronní služby v příkazu nabídky. Můžete použít k používání služby v jiné jiné asynchronní metody zde zobrazená procedura.  
  
1.  Přidání příkazu nabídky do projektu. (V **Průzkumníka řešení**, vyberte uzel projektu, klikněte pravým tlačítkem a vyberte **přidat** > **nová položka**  >   **Rozšiřitelnost** > **vlastní příkaz**.) Název souboru příkazů *TestAsyncCommand.cs*.  
  
2.  Šablona vlastního příkazu znovu přidá `Initialize()` metodu *TestAsyncPackage.cs* souboru, aby bylo možné inicializovat příkazu. V `Initialize()` metoda, zkopírovat řádek, který inicializuje příkazu. By měl vypadat nějak takto:  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Přesunutí tohoto řádku `InitializeAsync()` metodu *AsyncPackageForService.cs* souboru. Protože jde o asynchronní inicializace, před inicializací pomocí příkazu, je nutné přepnout do hlavního vlákna <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. To by teď měl vypadat takto:  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  

        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);  
        TestAsyncCommand.Initialize(this);
    }  
  
    ```  
  
3.  Odstranit `Initialize()` metody.  
  
4.  V *TestAsyncCommand.cs* souboru, vyhledejte `MenuItemCallback()` metody. Odstranění těla metody.  
  
5.  Přidat sadu pomocí příkazu:  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  Přidat metodu s názvem `UseTextWriterAsync()`, který získá službu a používá jeho metody:  
  
    ```csharp  
    private async System.Threading.Tasks.Task UseTextWriterAsync()  
    {  
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =   
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))  
              as ITextWriterService;  

        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Volejte tuto metodu z `MenuItemCallback()` metody:  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  Sestavte řešení a spusťte ladění. Když se objeví experimentální instanci sady Visual Studio, přejděte na **nástroje** nabídky a vyhledat **vyvolat TestAsyncCommand** položky nabídky. Po kliknutí na to, TextWriterService zapíše do souboru, který jste zadali. (Není nutné pro otevření řešení, protože volání příkazu zároveň způsobí, že balíček, který má načíst.)  
  
## <a name="see-also"></a>Viz také:  
 [Použít a poskytování služeb](../extensibility/using-and-providing-services.md)
