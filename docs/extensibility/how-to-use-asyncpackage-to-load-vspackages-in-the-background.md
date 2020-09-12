---
title: Použití AsyncPackage k načtení VSPackage na pozadí
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: fef717ba7ec135038dcb35348eff870d9eeb3e33
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037286"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Postupy: použití AsyncPackage k načtení VSPackage na pozadí
Načtení a inicializace balíčku VS může mít za následek I/O disku. Pokud takové vstupně-výstupní operace proběhne ve vlákně uživatelského rozhraní, může to vést k potížím s odezvou. Pro vyřešení této sady sada Visual Studio 2015 zavedla  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> třídu, která umožňuje načtení balíčku do vlákna na pozadí.

## <a name="create-an-asyncpackage"></a>Vytvoření AsyncPackage
 Můžete začít vytvořením projektu VSIX (**soubor**  >  **Nový**  >  **projekt**  >  **Visual C#**  >  **rozšíření**  >  **VSIX**Visual C#) a přidáním VSPackage do projektu (klikněte pravým tlačítkem myši na projekt a **přidejte**  >  **novou položku**  >  **C# item**  >  **rozšiřitelný**  >  **balíček sady Visual Studio**pro položku C#). Pak můžete vytvořit své služby a přidat tyto služby do balíčku.

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

4. Pokud máte práci s asynchronní inicializací, měli byste přepsat <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . Odeberte `Initialize()` metodu poskytnutou šablonou VSIX. ( `Initialize()` Metoda v **AsyncPackage** je zapečetěná). K <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> Přidání asynchronních služeb do balíčku můžete použít kteroukoli z těchto metod.

    Poznámka: pro volání `base.InitializeAsync()` můžete změnit zdrojový kód na:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Je nutné se ujistit, že neprovedete vzdálené volání procedur (RPC) z asynchronního inicializačního kódu (v **InitializeAsync**). Tato situace může nastat, pokud voláte <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> přímo nebo nepřímo.  Pokud jsou vyžadovány synchronní zatížení, vlákno uživatelského rozhraní bude blokovat pomocí <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Výchozí blokující model zakáže funkci RPCSS. To znamená, že pokud se pokusíte použít RPC z asynchronních úloh, bude zablokováno, pokud vlákno uživatelského rozhraní čeká na načtení balíčku. Obecně platí, že pokud je to potřeba, můžete do vlákna uživatelského rozhraní v případě potřeby použít něco, co je třeba připojit k objektu pro **vytváření úloh** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> nebo nějaký jiný mechanismus, který nepoužívá RPC.  Nepoužívejte **ThreadHelper. Generic. Invoke** nebo obecně zablokovat volající vlákno, které čeká na načtení do vlákna uživatelského rozhraní.

    Poznámka: v metodě byste se měli vyhnout použití metody **GetService** nebo **QueryService** `InitializeAsync` . Pokud je budete muset použít, budete muset nejdřív přepnout do vlákna uživatelského rozhraní. Alternativou je použití <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> z **AsyncPackage** (přetypováním na <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> .)

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
 Většina práce je stejná jako vytvoření nového **AsyncPackage**. Postupujte podle kroků 1 až 5 výše. Také je třeba vzít v úvahu další upozornění s následujícími doporučeními:

1. Nezapomeňte odebrat `Initialize` přepsání, které jste měli v balíčku.

2. Vyhnout se zablokování: v kódu může být skryté vzdálené volání procedur. který se nyní stane ve vlákně na pozadí. Ujistěte se, že pokud provádíte RPC (například **GetService**), musíte (1) přepnout do hlavního vlákna nebo (2) použít asynchronní verzi rozhraní API, pokud existuje (například **GetServiceAsync**).

3. Neprovádějte přepínání mezi vlákny příliš často. Zkuste lokalizovat práci, která se může stát ve vlákně na pozadí, aby se snížila doba načítání.

## <a name="querying-services-from-asyncpackage"></a>Dotazování služeb z AsyncPackage
 **AsyncPackage** může nebo nemusí být načten asynchronně v závislosti na volajícím. Příklad:

- Pokud se jedná o volajícího s názvem **GetService** nebo **QueryService** (synchronní rozhraní API) nebo

- Pokud volající s názvem **IVsShell:: LoadPackage** (nebo **IVsShell5:: LoadPackageWithContext**) nebo

- Zatížení se aktivuje kontextem uživatelského rozhraní, ale nezadali jste kontextový mechanizmus uživatelského rozhraní, který můžete asynchronně načíst.

  balíček se pak načte synchronně.

  Váš balíček má stále příležitost (ve své asynchronní inicializační fázi), aby fungoval mimo vlákno uživatelského rozhraní, i když je vlákno uživatelského rozhraní pro dokončení této práce blokované. Pokud volající používá **IAsyncServiceProvider** k asynchronnímu dotazování na vaši službu, pak se vaše zatížení a inicializace provede asynchronně za předpokladu, že se na výsledný objekt úkolu okamžitě neblokují.

  C#: postup asynchronního dotazování služby:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
