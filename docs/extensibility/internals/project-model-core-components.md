---
title: Základní součásti modelu projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706539"
---
# <a name="project-model-core-components"></a>Základní komponenty modelu projektu
Následující tabulky rozbalí model projektu. Tabulky obsahují stručný popis rozhraní a služeb identifikovaných v modelu a rozhraní a služby spojené s konkrétními objekty. Tabulky navíc podrobně popisují další rozhraní, která jsou volitelná při vytváření a údržbě projektu v závislosti na požadavcích konkrétního typu projektu.

 Další informace naleznete v [tématu Supporting Symbol-Browsing Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Objekt balíčku

|Rozhraní|Komentáře|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializuje VSPackage v rozhraní IDE a zpřístupní jeho služby pro rozhraní IDE.|

### <a name="project-factory-object"></a>Objekt Factory projektu

|Rozhraní|Komentáře|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Spravuje vytváření nových projektů a otevírání existujících projektů.|

### <a name="project-objects"></a>Objekty projektu

|Rozhraní|Komentáře|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Spravuje sčítání a odebírání položek projektu, otevírá editory a udržuje mapování `VSITEMID`mezi jednotlivými zástupci dokumentu a . Dědí `IVsProject` z `IVsProject2`a .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Spravuje navigační a zobrazované vlastnosti a poskytuje události.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Umožňuje provádění příkazů podobné `IOleCommandTarget` příkazu pro příkazy, jako je například Vyjmout a Přejmenovat, které platí pouze v případě, že fokus je v Průzkumníku řešení.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Slouží jako primární rozhraní cíle příkazu pro hierarchii projektu. Jedná se o standardní rozhraní pro dotazování objektů pro jejich stav příkazu nebo stav a spuštěné příkazy. K dispozici, pokud nejste zaměřeni v okně projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordinuje trvalost stavu projektu. Stav projektu je obvykle uložen jako soubor projektu, ale může být přizpůsoben pro systémy úložiště, které nejsou založeny na souboru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Umožňuje projektu spravovat všechny aspekty trvalosti pro jeho položky projektu, buď jako soubory na disku nebo objekty v jiných systémech úložiště. Rozhraní `IVsPersistHierarchyItem2` se používá pro položky, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> které neimplementují rozhraní.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordinuje interakce se sohledem zdrojového kódu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Umožňuje projektům spravovat informace o konfiguraci.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Spravuje objekty konfigurace projektu, jako jsou konfigurace ladění/vydání. Operace sestavení, nasazení a ladění jsou koordinovány prostřednictvím objektů konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementována hierarchiemi pro řízení možností odstranění (destruktivní) nebo odebrání (nedestruktivní) možnosti pro položky hierarchie. Volání rozhraní dotazu `IVsHierarchyDeleteHandler` na `IVsHierarchy` rozhraní z rozhraní.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Poskytuje možnost implementace s objektem, `IVsCfgProvider2` který podporuje rozhraní na jiné identity COM `IVsHierarchy` než objekt projektu, který implementuje rozhraní.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Volitelné rozhraní implementované, aby váš projekt rozšiřitelný jinými vývojáři. Rozhraní `IVsProjectStartupServices` umožňuje třetí straně VSPackage zaregistrovat identifikátor GUID, který přetrvává do souboru projektu tak, aby při každém načtení projektu `QueryService` načíst guid služby jiného výrobce do souboru projektu a volání tohoto identifikátoru GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementována zdrojovými `UIHierarchy` hierarchiemi v okně pro koordinaci operací schránky, jako je vyjmutí, kopírování a vkládání. Pomocí `AdviseClipboardHelperEvents` rozhraní můžete zaregistrovat události schránky.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Obsahuje informace o přetažené položce vzhledem ke zdroji dat během operace přetažení v okně hierarchie rozhraní. Voláno `IVsHierarchy` z rozhraní.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Obsahuje informace o přetažené položce vzhledem k jejímu cíli přetažení během operace přetažení v okně hierarchie rozhraní. Voláno `IVsHierarchy` z rozhraní.|

### <a name="configuration-object"></a>Konfigurační objekt

|Rozhraní|Komentáře|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Obsahuje informace o konfiguraci.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Umožňuje projektům spravovat informace o konfiguraci.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Umožňuje spuštění projektu pod kontrolou ladicího programu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementováno projekty nasazení, které provádějí operace nasazení pro jiné projekty.|

### <a name="configuration-builder-object"></a>Objekt Tvůrce konfigurace

|Rozhraní|Komentáře|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Spravuje operaci sestavení konfigurace projektu.|

### <a name="additional-project-objects"></a>Další objekty projektu

|Rozhraní|Komentáře|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Zobrazí vlastnosti položky v okně **Vlastnosti.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Zobrazí výstupy pro nasazení.|

 V následující tabulce jsou uvedeny stručné popisy služeb uvedených v modelu projektu.

### <a name="services"></a>Služby

|Služba|Komentáře|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Používá VSPackages, které implementují typy projektů zaregistrovat, že jejich továrna projektu existuje s IDE. Vaše VSPackage `QueryService` musí volat pro tuto službu a zaregistrovat jeho továrny projektu při `IVsPackage::SetSite` volání metody. Pokud `SetSite` metoda není volána, projekt není vytvořena instance.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Poskytuje přístup k interní, integrované pojetí ide aktuální řešení, jako je například možnost výčet projektů, vytvářet nové projekty, všímat změny projektu a tak dále.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Volat projekty, které se chtějí účastnit správy zdrojového kódu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Udržuje tabulku otevřených dokumentů k určení, zda je již otevřena jedna nebo více položek projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Obsahuje rozhraní a metody volané skutečně otevřít položku projektu pomocí standardní editor nebo konkrétní editor.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Vyžaduje se, aby byly volány všemi projekty při přidávání, odebírat nebo přejmenovávat jejich položky.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Spravuje změny v souboru nebo adresáři a upozorní klienty na změnu vybraných souborů na disku.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Vyžaduje, aby byly volány všemi projekty a editory před tím, než znečištěné položky nebo je uložit.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Spravuje pořadí operací sestavení a nasazení pro konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Poskytuje přístup ke službám ladicího programu nižší úrovně používaným pro většinu ladicích ovládacích prvků.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Umožňuje VSPackages přístup k informacím o aktuálnívýběry a umožňuje komunikaci s **vlastnosti** okna.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Poskytuje základní funkce rozhraní IDE související s uživatelským rozhraním, jako je například možnost vytvářet a výčet oken nástrojů nebo oken dokumentů nebo hlásit chybu uživateli.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Poskytuje přístup k stavovému řádku ide.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Slouží k implementaci modelu automatizace. V modelu projektu vrátíte objekt vlastností, který umožňuje vytvořit instanci tohoto objektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Slouží k implementaci událostí schránky na objekt projektu v hierarchii. `SVsUIHierWinClipboardHelper`umožňuje správně zpracovat operace vyjmutí, kopírování a vložení.|

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Není v sestavení: Použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)
