---
title: Základní komponenty modelu projektu | Microsoft Docs
description: Tento článek obsahuje popisy rozhraní a služeb identifikovaných v jádru modelu projektu a rozhraní a služby přidružené k objektům.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c6aeb24b2aee5b0abb3e5d803004ba97725bb707
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876893"
---
# <a name="project-model-core-components"></a>Základní komponenty modelu projektu
Následující tabulky se rozšiřují v modelu projektu. Tabulky obsahují stručný popis rozhraní a služeb identifikovaných v modelu a rozhraní a služby přidružené ke konkrétním objektům. Kromě toho tabulky obsahují podrobnosti o dalších rozhraních, která jsou volitelná v vytváření a údržbě projektu v závislosti na požadavcích vašeho konkrétního typu projektu.

 Další informace najdete v tématu [podpora Symbol-Browsingch nástrojů](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Objekt balíčku

|Rozhraní|Komentáře|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializuje VSPackage v integrovaném vývojovém prostředí a zpřístupní jeho služby pro IDE.|

### <a name="project-factory-object"></a>Objekt factory projektu

|Rozhraní|Komentáře|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Spravuje vytváření nových projektů a otevírání existujících projektů.|

### <a name="project-objects"></a>Objekty projektu

|Rozhraní|Komentáře|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Spravuje přidávání a odebírání položek projektu, otevírá editory a udržuje mapování mezi jednotlivými monikery dokumentu a `VSITEMID` . Dědí z `IVsProject` a `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Spravuje navigační a zobrazované vlastnosti a poskytuje události.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Povolí spuštění příkazu podobně jako `IOleCommandTarget` u příkazů pro příkazy, jako je vyjmutí a přejmenování, které platí pouze v případě, že je fokus v Průzkumník řešení.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Slouží jako cílové rozhraní primárního příkazu pro hierarchii projektu. Je to standardní rozhraní pro dotazování objektů pro svůj stav příkazu nebo stav a spouštění příkazů. K dispozici, pokud se nezaměřujete na okno projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordinuje persistenci stavu projektu. Stav projektu je obvykle uložen jako soubor projektu, ale lze jej přizpůsobit systémům úložiště, které nejsou založené na souborech.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Umožňuje projektu spravovat všechny aspekty Persistence pro své položky projektu, a to buď jako soubory na disku nebo v objektech v jiných systémech úložiště. `IVsPersistHierarchyItem2`Rozhraní se používá pro položky, které neimplementují <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> rozhraní.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordinuje interakce s ovládacím prvkem zdrojového kódu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Umožňuje projektům spravovat informace o konfiguraci.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Spravuje objekty konfigurace projektu, například konfigurace ladění a vydání. Operace sestavení, nasazení a ladění jsou koordinovány prostřednictvím objektů konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementované hierarchií pro řízení možností odstranění (destruktivní) nebo odebrání (nedestruktivní) pro položky hierarchie. Volání dotazovacího rozhraní na `IVsHierarchyDeleteHandler` rozhraní z `IVsHierarchy` rozhraní.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Poskytuje možnost implementace pro objekt, který podporuje `IVsCfgProvider2` rozhraní v jiné identitě modelu COM, než je objekt projektu, který implementuje `IVsHierarchy` rozhraní.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Volitelné rozhraní bylo implementováno, aby byl projekt rozšiřitelný jinými vývojáři. `IVsProjectStartupServices`Rozhraní umožňuje VSPackage třetí strany zaregistrovat identifikátor GUID, který zachová do souboru projektu, takže pokaždé, když se projekt načte, načteme do souboru projektu identifikátor GUID služby třetí strany a zavoláte ho `QueryService` pro identifikátor GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Je implementována zdrojovými hierarchiemi v `UIHierarchy` okně pro koordinaci operací schránky, jako je vyjmutí, kopírování a vložení. Použijte `AdviseClipboardHelperEvents` rozhraní k registraci událostí schránky.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Poskytuje informace o přetažené položce relativní ke zdroji dat během operace přetažení v okně hierarchie uživatelského rozhraní. Voláno z `IVsHierarchy` rozhraní.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Poskytuje informace o přetažené položce vzhledem k cíli přetažení během operace přetažení v okně hierarchie uživatelského rozhraní. Voláno z `IVsHierarchy` rozhraní.|

### <a name="configuration-object"></a>Objekt konfigurace

|Rozhraní|Komentáře|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Poskytuje informace o konfiguraci.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Umožňuje projektům spravovat informace o konfiguraci.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Povolí spuštění projektu pod ovládacím prvkem ladicího programu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementováno projekty nasazení, které provádějí operace nasazení pro jiné projekty.|

### <a name="configuration-builder-object"></a>Objekt tvůrce konfigurace

|Rozhraní|Komentáře|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Spravuje operaci sestavení konfigurace projektu.|

### <a name="additional-project-objects"></a>Další objekty projektu

|Rozhraní|Komentáře|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Zobrazí vlastnosti položky v okně **vlastnosti** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Zobrazí výstupy pro nasazení.|

 Následující tabulka uvádí stručný popis služeb identifikovaných v modelu projektu.

### <a name="services"></a>Služby

|Služba|Komentáře|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Používá VSPackage, které implementují typy projektů k registraci, že jejich továrna projektu existuje s rozhraním IDE. Aby bylo voláno volání metody, je nutné, aby VSPackage vyvolala `QueryService` tuto službu a zaregistrovala její objekt pro vytváření `IVsPackage::SetSite` . Pokud `SetSite` metoda není volána, projekt není vytvořen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Poskytuje přístup k internímu integrovanému pojmu aktuálního řešení v integrovaném vývojovém prostředí (IDE), jako je například možnost výčtu projektů, vytváření nových projektů, zobrazení upozornění na změny projektu a tak dále.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Voláno projekty, které chtějí být součástí správy zdrojového kódu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Udržuje tabulku otevřených dokumentů, abyste zjistili, jestli je už jedna nebo víc položek projektu otevřené.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Obsahuje rozhraní a metody volané ke skutečnému otevření položky projektu pomocí standardního editoru nebo konkrétního editoru.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Musí být volány všemi projekty při přidání, odebrání nebo přejmenování svých položek.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Spravuje změny v souboru nebo adresáři a upozorní klienty, když se na disku změnily vybrané soubory.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Musí být volány všemi projekty a editory předtím, než je nevyřízené položky nebo je uložíte.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Spravuje pořadí operací sestavení a nasazení pro konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Poskytuje přístup k ladicím službám nižší úrovně, které se používají pro většinu ovládacích prvků ladění.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Umožňuje VSPackage přistupovat k informacím o aktuálních výběrech a umožňuje komunikaci s oknem **vlastností** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Poskytuje základní funkce rozhraní IDE související s uživatelským rozhraním, jako je třeba možnost vytvořit a vytvořit výčet oken nástrojů nebo oken dokumentů nebo ohlásit chybu uživateli.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Poskytuje přístup ke stavovým pruhům IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Slouží k implementaci modelu automatizace. V modelu projektu vrátíte objekt Properties, který umožňuje vytvořit instanci tohoto objektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Slouží k implementaci událostí schránky pro objekt projektu v hierarchii. `SVsUIHierWinClipboardHelper` umožňuje správně zpracovat operace vyjmutí, kopírování a vložení.|

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Není v sestavení: použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](/previous-versions/bb166212(v=vs.100))
- [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)