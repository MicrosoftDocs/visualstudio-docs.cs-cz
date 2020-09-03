---
title: 'Postupy: použití AsyncPackage k načtení VSPackage na pozadí | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: f59838913ed3f9bc6679336393f6db9181291e3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204024"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Postupy: Použití AsyncPackage k načtení rozšíření VSPackages na pozadí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Načtení a inicializace balíčku VS může mít za následek I/O disku. Pokud takové vstupně-výstupní operace proběhne ve vlákně uživatelského rozhraní, může to vést k potížím s odezvou. Pro vyřešení této sady sada Visual Studio 2015 zavedla  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> třídu, která umožňuje načtení balíčku do vlákna na pozadí.  
  
## <a name="creating-an-asyncpackage"></a>Vytvoření AsyncPackage  
 Můžete začít vytvořením projektu VSIX (**soubor/nový/projekt/Visual C#/rozšiřitelnost/projekt VSIX**) a přidáním VSPackage do projektu (klikněte pravým tlačítkem na projekt a **přidejte/novou položku/položku C#/rozšiřitelnost/balíček sady Visual Studio**). Pak můžete vytvořit své služby a přidat tyto služby do balíčku.  
  
1. Odvodit balíček z <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .  
  
2. Pokud poskytujete služby, jejichž dotazování může mít za následek načtení balíčku:  
  
    Chcete-li aplikaci Visual Studio označit, že balíček je bezpečný pro načítání na pozadí a že se chcete vyjádřit k tomuto chování, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> měli byste nastavit vlastnost **AllowsBackgroundLoading** na hodnotu true v konstruktoru atributu.  
  
   ```csharp  
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
   ```  
  
    Chcete-li určit aplikaci Visual Studio, že je bezpečné vytvořit instanci vaší služby ve vlákně na pozadí, měli byste nastavit <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> vlastnost na hodnotu true v <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> konstruktoru.  
  
   ```csharp  
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
   ```  
  
3. Pokud načítáte pomocí kontextů uživatelského rozhraní, pak byste měli zadat **PackageAutoLoadFlags. BackgroundLoad** pro <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> nebo hodnotu (0x2) do příznaků zapsaných jako hodnota položky automatického načítání balíčku.  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
   ```  
  
4. Pokud máte práci s asynchronní inicializací, měli byste přepsat <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . Odeberte metodu **Initialize ()** poskytnutou šablonou VSIX. (Metoda **Initialize ()** v **AsyncPackage** je zapečetěná). K <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> Přidání asynchronních služeb do balíčku můžete použít kteroukoli z těchto metod.  
  
    Poznámka: Chcete-li volat **base.InitializeAsync ()**, můžete změnit zdrojový kód na:  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. Je nutné se ujistit, že neprovedete vzdálené volání procedur (Remove Procedure Call) z asynchronního inicializačního kódu (v **InitializeAsync**). Tato situace může nastat, pokud voláte <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> přímo nebo nepřímo.  Pokud jsou vyžadovány synchronní zatížení, vlákno uživatelského rozhraní bude blokovat pomocí <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Výchozí blokující model zakáže funkci RPCSS. To znamená, že pokud se pokusíte použít RPC z asynchronních úloh, bude zablokováno, pokud vlákno uživatelského rozhraní čeká na načtení balíčku. Obecně platí, že pokud je to potřeba, můžete do vlákna uživatelského rozhraní v případě potřeby použít něco, co je třeba připojit k objektu pro **vytváření úloh** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> nebo nějaký jiný mechanismus, který nepoužívá RPC.  Nepoužívejte **ThreadHelper. Generic. Invoke** nebo obecně zablokovat volající vlákno, které čeká na načtení do vlákna uživatelského rozhraní.  
  
    Poznámka: v metodě **InitializeAsync** byste se měli vyhnout použití metody **GetService** nebo **QueryService** . Pokud je budete muset použít, budete muset nejdřív přepnout do vlákna uživatelského rozhraní. Alternativou je použití <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> z **AsyncPackage** (přetypováním na <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> .)  
  
   C#: vytvoření AsyncPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Převést existující VSPackage na AsyncPackage  
 Většina práce je stejná jako vytvoření nového **AsyncPackage**. Musíte postupovat podle kroků 1 až 5 výše. Také je nutné vzít v úvahu další upozornění na tyto skutečnosti:  
  
1. Nezapomeňte odebrat přepsání **inicializace** , které jste měli v balíčku.  
  
2. Vyhněte se zablokování: v kódu, ke kterému se nyní dochází ve vlákně na pozadí, může být skryté vzdálená volání procedur. Je nutné zajistit, aby v případě, že provádíte vzdálené volání procedur (RPC) (třeba **GetService**), bylo nutné (1) přepnout do hlavního vlákna nebo (2) použít asynchronní verzi rozhraní API, pokud existuje (např. **GetServiceAsync**).  
  
3. Neprovádějte přepínání mezi vlákny příliš často. Zkuste lokalizovat práci, ke které může dojít ve vlákně na pozadí. Tím se zkracuje doba načítání.  
  
## <a name="querying-services-from-asyncpackage"></a>Dotazování služeb z AsyncPackage  
 **AsyncPackage** může nebo nemusí být načten asynchronně v závislosti na volajícím. Příklad:  
  
- Pokud se jedná o volajícího s názvem **GetService** nebo **QueryService** (synchronní rozhraní API) nebo  
  
- Pokud volající s názvem **IVsShell:: LoadPackage** (nebo **IVsShell5:: LoadPackageWithContext**) nebo  
  
- Zatížení se aktivuje kontextem uživatelského rozhraní, ale nezadali jste kontextový mechanizmus uživatelského rozhraní, který můžete asynchronně načíst.  
  
  balíček se pak načte synchronně.  
  
  Všimněte si, že váš balíček má stále příležitost (ve své asynchronní inicializační fázi), aby fungoval mimo vlákno uživatelského rozhraní, i když je vlákno uživatelského rozhraní pro dokončení této práce blokované. Pokud volající používá **IAsyncServiceProvider** k asynchronnímu dotazování na vaši službu, pak se vaše zatížení a inicializace provede asynchronně za předpokladu, že se na výsledný objekt úkolu okamžitě neblokují.  
  
  C#: postup asynchronního dotazování služby:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
