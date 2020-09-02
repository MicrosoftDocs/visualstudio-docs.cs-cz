---
title: Pracovní prostory v aplikaci Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 011781b434c4d005e473c5f97c60a9269dc5d034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952760"
---
# <a name="workspaces"></a>Pracovní prostory

Pracovní prostor je způsob, jakým Visual Studio představuje libovolnou kolekci souborů v [otevřené složce](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)a je reprezentovaná <xref:Microsoft.VisualStudio.Workspace.IWorkspace> typem. Pracovní prostor sám o sobě nerozumí obsahu ani funkcím, které se týkají souborů v rámci této složky. Místo toho poskytuje obecnou sadu rozhraní API pro funkce a rozšíření pro vytváření a zpracování dat, na která ostatní můžou pracovat. Výrobci se skládají prostřednictvím [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) pomocí různých atributů exportu.

## <a name="workspace-providers-and-services"></a>Poskytovatelé a služby pracovního prostoru

Poskytovatelé a služby pracovního prostoru poskytují data a funkce pro reakci na obsah pracovního prostoru. Můžou poskytovat informace o kontextovém souboru, symbolech ve zdrojových souborech nebo funkcích buildu.

Obě koncepty používají [model pro vytváření](https://en.wikipedia.org/wiki/Factory_method_pattern) a jsou importovány prostřednictvím rozhraní MEF v pracovním prostoru. Všechny atributy exportu implementují `IProviderMetadataBase` nebo `IWorkspaceServiceFactoryMetadata` , ale existují konkrétní typy, které rozšíření mají použít pro exportované typy.

Jeden rozdíl mezi poskytovateli a službami je jejich vztahem k pracovnímu prostoru. Pracovní prostor může mít mnoho poskytovatelů určitého typu, ale v každém pracovním prostoru je vytvořená jenom jedna služba určitého typu. Pracovní prostor má například mnoho poskytovatelů skenerů souborů, ale pracovní prostor má v každém pracovním prostoru jenom jednu službu indexování.

Další klíčovým rozdílem je spotřeba dat od poskytovatelů a služeb. Pracovní prostor je vstupním bodem pro získání dat od poskytovatelů z několika důvodů. Nejdříve poskytovatelé mají obvykle některé úzké sady dat, které vytvářejí. Data mohou být symboly pro zdrojový soubor v jazyce C# nebo soubory kontextů sestavení pro soubor _CMakeLists.txt_ . Pracovní prostor bude odpovídat žádosti zákazníka poskytovatelům, jejichž metadata jsou v souladu s požadavkem. V druhé době některé scénáře umožňují mnoha poskytovatelům přispívat k žádosti, zatímco jiné scénáře používají poskytovatele s nejvyšší prioritou.

Naproti tomu rozšíření můžou získat instance a pracovat přímo se službami pracovního prostoru. Metody rozšíření `IWorkspace` jsou k dispozici pro služby poskytované aplikací Visual Studio, jako je například <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Vaše rozšíření může nabízet službu pracovního prostoru pro součásti v rámci rozšíření nebo pro využívání dalších rozšíření. Příjemci by měli použít <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> nebo metodu rozšíření, kterou zadáte pro `IWorkspace` typ.

>[!WARNING]
> Nevytvářejte služby, které jsou v konfliktu se sadou Visual Studio. Může to vést k neočekávaným problémům.

## <a name="disposal-on-workspace-closure"></a>Vyřazení při zavírání pracovního prostoru

Při uzavírání pracovního prostoru může být nutné uvolnit, ale volat asynchronní kód. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>Rozhraní je k dispozici, aby bylo možné tento kód snadno zapsat.

## <a name="related-types"></a>Související typy

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> je centrální entitou otevřeného pracovního prostoru, jako je otevřená složka.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> vytvoří zprostředkovatele pro vytvoření instance daného pracovního prostoru.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Vytvoří instanci služby na pracovní prostor.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> by měl být implementován na poskytovatelích a službách, které potřebují spouštět asynchronní kód při odstraňování.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> poskytuje podpůrné metody pro přístup k dobře známým službám nebo libovolným službám.

## <a name="workspace-settings"></a>Nastavení pracovního prostoru

Pracovní prostory mají <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> službu s jednoduchou, ale výkonnou kontrolu nad pracovním prostorem. Základní přehled nastavení naleznete v tématu [přizpůsobení úloh sestavení a ladění](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Nastavení pro většinu `SettingsType` typů jsou soubory _. JSON_ , například _VSWorkspaceSettings.jszapnuté_ a _tasks.vs.jsna_.

Výkon nastavení pracovního prostoru se pohybuje v oblasti "obory", které jsou v pracovním prostoru jednoduše cesty. V případě volání příjemce <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> jsou agregovány všechny obory, které obsahují požadovanou cestu a typ nastavení. Priorita agregace oboru je následující:

1. "Místní nastavení", což je obvykle adresář kořene v pracovním prostoru `.vs` .
1. Požadovaná cesta sama.
1. Nadřazený adresář požadované cesty
1. Všechny další nadřazené adresáře až do kořene pracovního prostoru a včetně.
1. Globální nastavení, která se nachází v adresáři uživatele.

Výsledkem je instance <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Tento objekt obsahuje nastavení pro konkrétní typ a lze k němu zadat dotaz pro nastavení názvů klíčů uložených jako `string` . <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>Metody a <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> metody rozšíření očekávají, že volající bude znát typ požadované hodnoty nastavení. Jelikož jsou soubory s _příponou. JSON_ trvale zachované, mnoho volání bude používat,, `string` `bool` `int` a pole těchto typů. Jsou podporovány také typy objektů. V těchto případech můžete použít `IWorkspaceSettings` sebe sama jako argument typu. Příklad:

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

Za předpokladu, že tato nastavení byla v _VSWorkspaceSettings.jsuživatele zapnutá_, mohou být k datům přistupovaná:

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
>Tato rozhraní API nastavení se nevztahují k rozhraním API dostupným v `Microsoft.VisualStudio.Settings` oboru názvů. Nastavení pracovního prostoru jsou nezávisláy hostitele a používají soubory nastavení specifické pro pracovní prostor nebo zprostředkovatele dynamického nastavení.

### <a name="providing-dynamic-settings"></a>Poskytování dynamického nastavení

Rozšíření můžou poskytovat <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> : Tito poskytovatelé v paměti umožňují rozšíření přidat nastavení nebo přepsat ostatní.

Export objektu `IWorkspaceSettingsProvider` se liší od jiných poskytovatelů pracovních prostorů. Továrna není `IWorkspaceProviderFactory` a neexistuje žádný zvláštní typ atributu. Místo toho je třeba implementovat <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> a použít `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

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
>Při implementaci metod, které vrací `IWorkspaceSettingsSource` (jako `IWorkspaceSettingsProvider.GetSingleSettings` ), vrátí instanci `IWorkspaceSettings` spíše než `IWorkspaceSettingsSource` . `IWorkspaceSettings` poskytuje další informace, které mohou být užitečné při agregacích některých nastavení.

### <a name="settings-related-apis"></a>Rozhraní API související s nastavením

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> přečte a agreguje nastavení pro pracovní prostor.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Získá `IWorkspaceSettingsManager` pro pracovní prostor.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> načte nastavení pro daný obor agregovaná napříč všemi překrývajícími se obory.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> obsahuje nastavení pro konkrétní obor.

## <a name="workspace-suggested-practices"></a>Doporučené postupy pro pracovní prostor

- Vrátí objekty z `IWorkspaceProviderFactory.CreateProvider` nebo podobných rozhraní API, která si zapamatují `Workspace` kontext při vytvoření. Poskytovatelé rozhraní se zapisují tak, že se tento objekt při vytváření udržuje.
- Ukládat mezipaměti nebo nastavení pro konkrétní pracovní prostory v rámci cesty "místní nastavení" v pracovním prostoru. Vytvořte cestu k souboru pomocí `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` sady Visual Studio 2017 verze 15,6 nebo novější. U verzí starších než verze 15,6 použijte následující fragment kódu:

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

## <a name="solution-events-and-package-auto-load"></a>Události řešení a automatické načtení balíčku

Načtené balíčky mohou implementovat `IVsSolutionEvents7` a vyvolat `IVsSolution.AdviseSolutionEvents` . Zahrnuje události při otevírání a zavírání složky v aplikaci Visual Studio.

Kontext uživatelského rozhraní lze použít k automatickému načtení balíčku. Hodnota je `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Odstraňování potíží

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Balíček SourceExplorerPackage se nenačetl správně.

Rozšiřitelnost pracovního prostoru je silně založená na rozhraní MEF a chyby složení způsobí selhání načtení otevřené složky hostování balíčku. Například pokud rozšíření exportuje typ s `ExportFileContextProviderAttribute` , ale pouze implementuje typ `IWorkspaceProviderFactory<IFileContextActionProvider>` , dojde k chybě při pokusu o otevření složky v aplikaci Visual Studio.

::: moniker range="vs-2017"

Podrobnosti o chybě najdete v _%localappdata%\microsoft\visualstudio\15.0_id \componentmodelcache\microsoft.VisualStudio.default.err_. Vyřešte všechny chyby pro typy implementované vaším rozšířením.

::: moniker-end

::: moniker range=">=vs-2019"

Podrobnosti o chybě najdete v _%localappdata%\microsoft\visualstudio\16.0_id \componentmodelcache\microsoft.VisualStudio.default.err_. Vyřešte všechny chyby pro typy implementované vaším rozšířením.

::: moniker-end

## <a name="next-steps"></a>Další kroky

* Kontexty [souborů](workspace-file-contexts.md) – poskytovatelé kontextu souborů přinášejí funkce Code Intelligence pro pracovní prostory otevřené složky.
* [Indexování](workspace-indexing.md) – indexování pracovních prostorů shromažďuje a uchovává informace o pracovním prostoru.
