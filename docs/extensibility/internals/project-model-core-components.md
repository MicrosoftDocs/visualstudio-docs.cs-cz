---
title: Základní komponenty modelu projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 863aef532e90d749f5c9c93a9d16cb2daf7f6c0b
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495983"
---
# <a name="project-model-core-components"></a>Základní komponenty modelu projektu
V následujících tabulkách doplňovat modelu projektu. Tabulky k dispozici stručné popisy rozhraní a služby určené v modelu, rozhraní a služeb přidružený k konkrétní objekty. Kromě toho v tabulkách jsou podrobně popsané jiného rozhraní, které jsou nepovinné v projektu vytváření a údržbu v závislosti na požadavcích vaší konkrétního typu projektu.  
  
 Další informace najdete v tématu [nástroje procházení symbolů podpora](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Objekt balíčku  
  
|Rozhraní|Komentáře|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializuje VSPackage v integrovaném vývojovém prostředí a zpřístupňuje jeho služeb rozhraní IDE.|  
  
### <a name="project-factory-object"></a>Objekt Factory projektu  
  
|Rozhraní|Komentáře|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Vytváření nových projektů a otevření stávajících projektů slouží ke správě.|  
  
### <a name="project-objects"></a>Objekty projektu  
  
|Rozhraní|Komentáře|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Spravuje přidávání a odebírání položek projektu, se otevře editory a udržuje mapování mezi moniker každý dokument a `VSITEMID`. Dědí z `IVsProject` a `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Řídí navigaci a zobrazení vlastností a poskytuje události.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Umožňuje spuštění podobně jako u příkazu `IOleCommandTarget` pro příkazech, jako je vyjmutí a přejmenovat, které se vztahují pouze po výběru v Průzkumníku řešení.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Slouží jako cílové rozhraní příkazu primární pro hierarchii projektu. Jedná se o standardní rozhraní pro dotazování na objekty pro jejich stavu nebo stavu a spuštění příkazů. Tato možnost je k dispozici, pokud nejsou fokus v okně projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Koordinuje trvalého stavu projektu. Obvykle stav projektu se ukládá jako soubor projektu, ale dokáže se přizpůsobit úložných systémů, které nejsou založené na souborech.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Umožňuje projektu ke správě všech aspektů trvalosti pro projektové položky, buď jako souborům na disku nebo objekty v jiných systémech úložiště. `IVsPersistHierarchyItem2` Rozhraní se používá pro položky, které neimplementují <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> rozhraní.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Koordinuje interakce s zdrojového kódu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Umožňuje projekty můžete spravovat informace o konfiguraci.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Spravuje objekty konfigurace projektu, jako jsou konfigurace ladění nebo vydání. Vytvořit, nasadit a ladit operace jsou koordinované přes objekty konfigurace projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementované hierarchie řídit (destruktivní) odstranit nebo odebrat (nedestruktivního) možnosti hierarchie položek. Volání rozhraní příkazů jazyka `IVsHierarchyDeleteHandler` rozhraní z `IVsHierarchy` rozhraní.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Poskytuje možnost implementace s objekt, který podporuje `IVsCfgProvider2` rozhraní v různých modelu COM identitu než objekt projektu, který implementuje `IVsHierarchy` rozhraní.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Volitelné rozhraní implementované jinými vývojáři extensible aby váš projekt. `IVsProjectStartupServices` Rozhraní umožňuje VSPackage třetích stran k registraci identifikátor GUID, který je uloží do souboru projektu tak, abyste pokaždé, když se načte projekt načtete identifikátor GUID služby třetích stran do vašeho souboru projektu a volání `QueryService` pro tento identifikátor GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementované ve zdrojových hierarchií `UIHierarchy` okno koordinovat operace schránky, jako je vyjmutí, kopírování a vložení. Použití `AdviseClipboardHelperEvents` rozhraní k registraci události schránky.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Poskytuje informace o přetaženou položku vzhledem ke svým zdrojem dat během operace přetažení myší v okně hierarchie uživatelského rozhraní. Volá se z `IVsHierarchy` rozhraní.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Poskytuje informace o přetaženou položku vzhledem k jeho cíl přetažení během operace přetažení myší v okně hierarchie uživatelského rozhraní. Volá se z `IVsHierarchy` rozhraní.|  
  
### <a name="configuration-object"></a>Objekt konfigurace  
  
|Rozhraní|Komentáře|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Poskytuje informace o konfiguraci.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Umožňuje projekty můžete spravovat informace o konfiguraci.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Umožňuje spustit pod kontrolu ladicího programu projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Projekty nasazení, které provádí operace nasazení pro jiné projekty implementované.|  
  
### <a name="configuration-builder-object"></a>Objekt konfigurace Tvůrce  
  
|Rozhraní|Komentáře|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Spravuje konfiguraci projektu operace sestavení.|  
  
### <a name="additional-project-objects"></a>Další objekty projektu  
  
|Rozhraní|Komentáře|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Zobrazí vlastnosti v položek **vlastnosti** okna.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Zobrazí výstupy pro nasazení.|  
  
 Následující tabulka obsahuje stručný popis služby určené v modelu projektu.  
  
### <a name="services"></a>Služby  
  
|Služba|Komentáře|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Používat rozšíření VSPackages, které implementují typy projektů k registraci, že existuje jejich objekt pro vytváření projektů pomocí integrovaného vývojového prostředí. Vaše VSPackage musí volat `QueryService` pro tuto službu a zaregistrujte tovární projektu při `IVsPackage::SetSite` metoda je volána. Pokud `SetSite` metoda není volána, váš projekt není vytvořena instance.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Poskytuje přístup k rozhraní IDE interní, integrované pojem aktuálního řešení, jako je například možnost udělat výčet projektů, vytvořit nové projekty, provést změny projektu a tak dále.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Volá se pro projekty, které chcete ve správě zdrojového kódu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Udržuje tabulku otevřené dokumenty k určení, zda jeden nebo více položek projektu jsou už otevřené.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Obsahuje rozhraní a metody volá se, aby skutečně otevřete položku projektu pomocí standardní editor nebo konkrétní editoru.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Budete muset volat všechny projekty v případě přidat či odebrat nebo přejmenovat jejich položky.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Spravuje změny do souboru nebo adresáře a oznamuje klientům, pokud vybrané soubory byly změněny na disku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Budete muset volat všechny projekty a editory před nesprávné položky nebo je uložíte.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Slouží ke správě pořadí operací sestavení a nasazení pro konfigurace projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Poskytuje přístup ke službám nízké úrovně ladicí program používá pro většinu ladění ovládacích prvků.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Rozšíření VSPackages přístup k informacím o aktuální výběr a umožňuje komunikaci s **vlastnosti** okna.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Poskytuje základní funkce související s Uživatelským rozhraním IDE, jako je například možnost vytvořit a zobrazit výčet okna nástrojů nebo okna dokumentu nebo oznámit chybu uživateli.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Poskytuje přístup k rozhraní IDE stavový řádek.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Používaný k implementaci modelu automatizace. Ve vašem projektu modelu a vrátí vlastnosti objektu, který vám umožní vytvoří instanci tohoto objektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Používaný k implementaci události schránky u projektu objektu v hierarchii. `SVsUIHierWinClipboardHelper` umožňuje správně popisovač operace vyjmutí, kopírování a vložit.|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Není v sestavení: použití HierUtil7 projektu třídy k implementaci typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)