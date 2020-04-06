---
title: 'Postup: Použití balíčku AsyncPackage k načtení balíčků VSPackages na pozadí | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710619"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Postup: Použití balíčku AsyncPackage k načtení balíčků VSPackages na pozadí
Načítání a inicializace balíčku VS může mít za následek vstupně-tuč. Pokud takové vstupně-va se stane ve vlákně uživatelského rozhraní, může vést k problémům s odezvou. Chcete-li tento problém vyřešit, Visual <xref:Microsoft.VisualStudio.Shell.AsyncPackage> Studio 2015 představil třídu, která umožňuje načítání balíčku na podprocesu na pozadí.

## <a name="create-an-asyncpackage"></a>Vytvoření balíčku AsyncPackage
 Můžete začít vytvořením projektu VSIX **(File** > **New** > **Project** > Visual**C#** > **Rozšiřitelnost** > **VSIX Project)** a přidáním VSPackage do projektu (klikněte pravým tlačítkem myši na projekt a **přidat** > novou**položku** > **C# položky** > **Rozšiřitelnost** > Visual Studio**balíček).** Poté můžete vytvořit služby a přidat tyto služby do balíčku.

1. Odvodit <xref:Microsoft.VisualStudio.Shell.AsyncPackage>balíček z .

2. Pokud poskytujete služby, jejichž dotazování může způsobit načtení balíčku:

    Chcete-li označit Visual Studio, že váš balíček je bezpečné <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> pro načítání na pozadí a opt-up toto chování, by měl nastavit **AllowsBackgroundLoading** vlastnost true v konstruktoru atributu.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Chcete-li označit Visual Studio, že je bezpečné vytvořit instanci služby <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> na pozadí <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> vlákno, měli byste nastavit vlastnost true v konstruktoru.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Pokud načítáte prostřednictvím kontextů uživatelského prostředí, pak byste měli <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> zadat **PackageAutoLoadFlags.BackgroundLoad** pro HODNOTU OR hodnotu (0x2) do příznaků zapsaných jako hodnota položky automatického načítání balíčku.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Pokud máte asynchronní inicializační práce, měli <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>byste přepsat . Odeberte metodu `Initialize()` poskytnutou šablonou VSIX. (Metoda `Initialize()` v **AsyncPackage** je zapečetěna). Můžete použít některou <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> z metod přidat asynchronní služby do balíčku.

    Poznámka: Chcete-li volat `base.InitializeAsync()`, můžete změnit zdrojový kód na:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Je třeba dbát na to, aby neprovádět RPC (vzdálené volání procedur) z asynchronního inicializačního kódu (v **InitializeAsync).** K těmto může <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> dojít při volání přímo nebo nepřímo.  Pokud je vyžadováno synchronizační zatížení, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>vlákno uživatelského rozhraní bude blokovat pomocí . Výchozí blokovací model zakáže rpc. To znamená, že pokud se pokusíte použít vzdálené volání procedur z asynchronních úloh, dojde k zablokování, pokud vlákno uživatelského rozhraní sám čeká na načtení balíčku. Obecnou alternativou je zařazovat kód do vlákna uživatelského rozhraní <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> v případě potřeby pomocí něco jako **joinable Task Factory**nebo nějaký jiný mechanismus, který nepoužívá Vzdálené volání procedur.  Nepoužívejte **ThreadHelper.Generic.Invoke** nebo obecně blokovat volající vlákno čeká na přístup do vlákna uživatelského rozhraní.

    Poznámka: Měli byste se vyhnout použití `InitializeAsync` **GetService** nebo **QueryService** ve vaší metodě. Pokud je musíte použít, budete muset nejprve přepnout do vlákna uživatelského rozhraní. Alternativou je <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> použití z **asyncPackage** (odléváním do <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)

   C#: Vytvořte asyncPackage:

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Převést existující balíček VSPackage na asyncpackage
 Většina práce je stejná jako vytvoření nového **balíčku AsyncPackage**. Postupujte podle kroků 1 až 5 výše. Je také třeba dbát zvýšené opatrnosti s následujícími doporučeními:

1. Nezapomeňte odebrat `Initialize` přepsání, které jste měli v balíčku.

2. Vyhněte se zablokování: V kódu mohou být skryté rpc. které se nyní dějí na pozadí závitu. Ujistěte se, že pokud vytváříte RPC (například **GetService**), musíte buď (1) přepnout do hlavního vlákna, nebo (2) použít asynchronní verzi rozhraní API, pokud existuje (například **GetServiceAsync**).

3. Nepřepínejte mezi vlákny příliš často. Pokuste se lokalizovat práci, která se může stát ve vlákně na pozadí, abyste zkrátili dobu načítání.

## <a name="querying-services-from-asyncpackage"></a>Dotazování služeb z asyncpackage
 **AsyncPackage** může nebo nemusí načíst asynchronně v závislosti na volajícím. Například

- Pokud volající volal **GetService** nebo **QueryService** (obě synchronní API) nebo

- Pokud volající volal **IVsShell::LoadPackage** (nebo **IVsShell5::LoadPackageWithContext)** nebo

- Zatížení je spuštěno kontextem uznatého, ale nezadali jste mechanismus kontextu ui, který vás může načíst asynchronně.

  pak se váš balíček načte synchronně.

  Váš balíček má stále příležitost (ve fázi asynchronní inicializace) k práci mimo vlákno uživatelského rozhraní, i když vlákno uživatelského rozhraní bude blokováno pro dokončení této práce. Pokud volající používá **IAsyncServiceProvider** asynchronně dotaz pro vaši službu, pak vaše zatížení a inicializace bude provedeno asynchronně za předpokladu, že nejsou okamžitě blokovat na výsledný objekt úlohy.

  C#: Jak dotazovat službu asynchronně:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
