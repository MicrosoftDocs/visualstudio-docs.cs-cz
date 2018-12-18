---
title: Pracovní prostory v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 0230201677fd2422817ca1fbeab6679a424e5c05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865827"
---
# <a name="workspaces"></a>Pracovní prostory

Pracovní prostor je, jak Visual Studio představuje jakoukoli kolekci souborů v [otevřít složku](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), a je reprezentována <xref:Microsoft.VisualStudio.Workspace.IWorkspace> typu. Samostatně pracovní prostor nerozumí obsah nebo funkcí týkajících se soubory ve složce. Místo toho poskytuje sadu rozhraní API pro funkce a rozšíření vytvářet a využívat data, která ostatní můžou fungovat po Obecné. Producenti jsou složené prostřednictvím [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) pomocí různých atributů exportu.

## <a name="workspace-providers-and-services"></a>Poskytovatelé pracovního prostoru a služby

Poskytovatelé pracovního prostoru a služby poskytují data a funkce, které reagují na obsah pracovního prostoru. Se může poskytovat kontextové informací o typu souboru symbolů ve zdrojových souborech, nebo integraci funkcí.

Použít obě koncepty [factory vzor](https://en.wikipedia.org/wiki/Factory_method_pattern) a importují prostřednictvím rozhraní MEF v pracovním prostoru. Implementovat všechny atributy export `IProviderMetadataBase` nebo `IWorkspaceServiceFactoryMetadata`, ale existují konkrétní typy, které by měly používat rozšíření pro exportované typy.

Jedním z rozdílů mezi poskytovatelů a službami je jejich vztah k pracovnímu prostoru. Pracovní prostor může mít mnoho poskytovatelů určitého typu, ale za jednotlivé pracovní prostory se vytvoří pouze pro jednu službu určitého typu. Například pracovní prostor obsahuje mnoho poskytovatelů skener souboru ale pracovní prostor má pouze jeden indexování za jednotlivé pracovní prostory.

Jiné klíčovým rozdílem je spotřeba dat od poskytovatelů a služby. Pracovní prostor je vstupním bodem k získání dat od poskytovatelů z několika důvodů. Nejprve poskytovatelé obvykle mít některé úzký sadu dat, který vytvoří. Data mohou být symboly pro C# zdrojového souboru nebo sestavení kontexty souborů pro _CMakeLists.txt_ souboru. Pracovní prostor bude odpovídat požadavku uživatele na zprostředkovatele, jejichž metadat zarovnat s požadavkem. Za druhé, některých scénářích povolit pro mnoho poskytovatelů přispívat na žádost, zatímco jiné scénáře použití zprostředkovatele s nejvyšší prioritou.

Rozšíření můžete naproti tomu získáte instance a pracovat přímo se službami pracovního prostoru. Rozšiřující metody na `IWorkspace` jsou k dispozici pro služby poskytovaný sadou Visual Studio, jako například <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Rozšíření můžou nabízet pracovního prostoru služby pro komponenty v rámci rozšíření nebo pro ostatní rozšíření používat. Příjemci měli používat <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> nebo metody rozšíření můžete poskytnout `IWorkspace` typu.

>[!WARNING]
> Nelze vytvářet služby, které jsou v konfliktu s Visual Studio. To může vést k neočekávaným problémům.

## <a name="disposal-on-workspace-closure"></a>Vyřazení na ukončení pracovního prostoru

V uzávěru pracovního prostoru, může být nutné zařízení Extender dispose, ale volání asynchronní kód. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Rozhraní je dostupné pro psaní tohoto kódu.

## <a name="related-types"></a>Související typy

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> je centrální entity pro otevřené pracovní prostor jako otevřené složky.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Vytvoří poskytovatele za jednotlivé pracovní prostory vytvořena instance.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Vytvoří službu za jednotlivé pracovní prostory vytvořena instance.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> by měla být implementována na poskytovatele a služby, které potřebujete ke spuštění asynchronního kódu během vyřazení.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> Poskytuje pomocné metody pro přístup k známé služby nebo libovolné služby.

## <a name="workspace-settings"></a>Nastavení pracovního prostoru

Pracovní prostory obsahují <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> služba s jednoduchou, ale výkonnou kontrolu nad pracovní prostor. Základní přehled nastavení, najdete v tématu [přizpůsobení sestavení a ladění úloh](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Nastavení pro většinu `SettingsType` typy jsou _.json_ soubory, jako například _VSWorkspaceSettings.json_ a _tasks.vs.json_.

Napájení nastavení pracovního prostoru se soustředí kolem "oborů", které jsou jednoduše cest v pracovním prostoru. Když se zavolá příjemce <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, všechny obory, které obsahují požadovaná cesta a typ nastavení naformátujete se agregují. Priorita agregace obor je následujícím způsobem:

1. "Místní nastavení", což je obvykle kořenu pracovního prostoru `.vs` adresáře.
1. Požadovaná cesta samotný.
1. Nadřazený adresář složky požadovaná cesta.
1. Dále všechny nadřazené adresáře do a včetně kořenu pracovního prostoru.
1. "Globální nastavení", což je v adresáři uživatele.

Výsledkem je instance <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Tento objekt obsahuje nastavení pro konkrétní typ a je možné zadávat dotazy klíčů názvy nastavení uložená jako `string`. <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Metody a <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> rozšiřující metody předpokládají, že volající znát typ hodnoty nastavení žádá. Protože většina nastavení souborů jsou ukládány jako _.json_ soubory, použije se mnoho volání `string`, `bool`, `int`a pole těchto typů. Typy objektů jsou také podporovány. V takových případech můžete použít `IWorkspaceSettings` samostatně jako argument typu. Příklad:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Za předpokladu, že tato nastavení se v uživatele _VSWorkspaceSettings.json_, data mohou být přístupné jako:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Tato nastavení rozhraní API jsou nemá vztah k rozhraní API dostupná v `Microsoft.VisualStudio.Settings` oboru názvů. Nastavení pracovního prostoru jsou nezávislá hostitele a použijte nastavení pro konkrétní pracovní prostor soubory nebo poskytovatelů dynamické nastavení.

### <a name="providing-dynamic-settings"></a>Zadání nastavení dynamické

Můžete zadat rozšíření <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Tito poskytovatelé v paměti povolit rozšíření přidat nastavení nebo potlačit jiné.

Export `IWorkspaceSettingsProvider` se liší od jiných poskytovatelů služeb pracovního prostoru. Objekt pro vytváření není `IWorkspaceProviderFactory` a neexistuje žádný typ speciální atribut. Místo toho implementovat <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> a používat `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Při implementaci metody, které vracejí `IWorkspaceSettingsSource` (jako je `IWorkspaceSettingsProvider.GetSingleSettings`), vracet instanci `IWorkspaceSettings` spíše než `IWorkspaceSettingsSource`. `IWorkspaceSettings` poskytuje další informace, které mohou být užitečné při některých nastavení agregace.

### <a name="settings-related-apis"></a>Nastavení rozhraní API související s

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> přečte a agreguje nastavení pro pracovní prostor.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Získá `IWorkspaceSettingsManager` pro pracovní prostor.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Získá nastavení pro daný obor agreguje všechny překrývající se rozsahy.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> obsahuje nastavení pro konkrétní obor.

## <a name="workspace-suggested-practices"></a>Pracovní prostor navrhované postupy

- Vrací objekty z `IWorkspaceProviderFactory.CreateProvider` nebo podobné rozhraní API, která mějte na paměti jejich `Workspace` kontextu při vytvoření. Zprostředkovatelé rozhraní se zapisují, očekává se, že tento objekt se ukládají na vytváření.
- Uložte nastavení v této cestě "Místní nastavení" pracovního prostoru nebo konkrétní pracovní prostor mezipaměti. Vytvořit cestu k souboru pomocí `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` v sadě Visual Studio 2017 verze 15.6 nebo novější. Pro verze starší než verze 15.6 použijte následující fragment kódu:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Události řešení a automaticky načíst balíček

Můžete implementovat načtených balíčcích `IVsSolutionEvents7` a vyvolání `IVsSolution.AdviseSolutionEvents`. Zahrnuje zpracování událostí na levé a pravé složku v sadě Visual Studio.

Kontextu uživatelského rozhraní lze použít pro automatické načtení balíčku. Hodnota je `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Poradce při potížích

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Balíček SourceExplorerPackage nebyla správně načtena.

Rozšiřitelnost pracovní prostor využívá výraznou MEF a způsobí, že chyby složení hostování otevřít složku k selhání načtení balíčku. Například, pokud rozšíření exportuje typ s `ExportFileContextProviderAttribute`, ale tento typ implementuje pouze `IWorkspaceProviderFactory<IFileContextActionProvider>`, dojde k chybě při pokusu o otevření složky v sadě Visual Studio. Podrobnosti o chybě najdete v _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Vyřešte všechny chyby pro typy, které jsou implementované pomocí rozšíření.

## <a name="next-steps"></a>Další kroky

* [Soubor kontexty](workspace-file-contexts.md) – zprostředkovatelé kontextu souborů přeneste kód intelligence pro otevřenou složku pracovní prostory. 
* [Indexování](workspace-indexing.md) – pracovní prostor indexování shromažďuje a opakuje informace o pracovním prostoru.
