---
title: Návrh podtypů projektu | Microsoft Docs
description: Přečtěte si, jak podtypy projektů umožňují, aby VSPackage rozšířily projekty na základě Microsoft Build Engine (MSBuild).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9342d8f9f045eec2036c65a3ed2d823dfb4a7e42
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877426"
---
# <a name="project-subtypes-design"></a>Návrh podtypů projektů

Podtypy projektů umožňují, aby VSPackage rozšířily projekty na základě Microsoft Build Engine (MSBuild). Použití agregace umožňuje znovu použít hromadně implementované jádro spravovaného projektového systému, ale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stále ještě přizpůsobuje chování pro konkrétní scénář.

 Následující témata podrobně popisují základní návrh a implementaci podtypů projektu:

- Návrh podtypu projektu.

- Agregace na více úrovních.

- Podpora rozhraní.

## <a name="project-subtype-design"></a>Návrh podtypu projektu

Inicializace podtypu projektu je dosaženo agregací <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objektů Main a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Tato agregace umožňuje podtypu projektu přepsat nebo zlepšit většinu schopností základního projektu. Podtypy projektů získají první možnost zpracovávat vlastnosti pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> příkazů, příkazy using a a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> řízení položek projektu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Podtypy projektů můžou také rozšířily:

- Objekty konfigurace projektu.

- Objekty závislé na konfiguraci.

- Objekty procházení nezávislé na konfiguraci.

- Objekty automatizace projektu.

- Kolekce vlastností automatizace projektu

Další informace o rozšiřitelnosti podle podtypů projektů naleznete v tématu [vlastnosti a metody rozšířené podle podtypů projektu](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Soubory zásad

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Prostředí poskytuje příklad rozšíření základního projektového systému s podtypem projektu ve své implementaci souborů zásad. Soubor zásad umožňuje tvarování [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí správou funkcí, které zahrnují Průzkumník řešení, dialogové okno **Přidat projekt** , dialogové okno **Přidat novou položku** a dialogové okno **vlastnosti** . Podtyp zásad Přepisuje a vylepšuje tyto funkce prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementace.

### <a name="aggregation-mechanism"></a>Agregační mechanizmus

Agregační mechanizmus pro projekt prostředí podporuje více úrovní agregace. díky tomu může být pokročilý podtyp implementován pomocí dalšího upřesnění typu projektu. Podpůrné objekty podtypu projektu, jako například <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> , jsou také navrženy tak, aby umožňovaly více úrovní vrstvení. V souladu s omezeními pravidel agregace modelu COM a modelu COM, musí být podtypy projektů a základní projekty společně naprogramovány, aby umožnily vnitřnímu typu nebo základnímu projektu být správně zapojeny do delegování volání metod a ke správě počtů odkazů. To znamená, že projekt, který se má agregovat, musí být naprogramován pro podporu agregace.

Na následujícím obrázku je znázorněno schéma agregace víceúrovňového typu projektu.

![Projectflavor grafika pro víceúrovňové navýšení sady Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Agregace podtypu projektu na více úrovních se skládá ze tří úrovní – základního projektu, který je agregovaný podtypem projektu, pak dále agregovaný podle typu pokročilého projektu. Obrázek se zaměřuje na některá z podpůrných rozhraní, která jsou k dispozici jako součást [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] architektury podtypu projektu.

### <a name="deployment-mechanisms"></a>Mechanismy nasazení

Mezi mnohé základní funkce systému projektu, které jsou rozšířeny podtypem projektu, jsou mechanismy nasazení. Podtyp projektu ovlivňuje mechanismy nasazení implementací konfiguračních rozhraní (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ), která jsou načtena voláním funkce QueryInterface na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . Ve scénáři, kdy dílčí typ projektu i pokročilý podtyp projektu přidávají jiné implementace konfigurace, základní projekt volá `QueryInterface` v rozšířeném podtypu projektu `IUnknown` . Pokud podtyp vnitřního projektu obsahuje implementaci konfigurace, kterou požaduje základní projekt, pokročilý delegát dílčího typu projektu k implementaci poskytované podtypem vnitřního projektu. Jako mechanismus pro zachování stavu z jedné agregační úrovně na jiný, všechny úrovně podtypů projektu implementují <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pro uchovávání dat XML nesouvisejících s sestavením do souborů projektu. Další informace naleznete v tématu [trvalá data v souboru projektu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> je implementován jako mechanismus pro načtení zařízení se zařízením pro automatizaci z podtypů projektu.

Následující ilustrace se zaměřuje na implementaci rozšířené služby Automation, konkrétně na objekt pro procházení konfigurace projektu, který se používá v podtypůch projektů k rozšiřování základního projektového systému.

![Obrázek automatického natažení obrázku VS – charakter projektu](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Podtypy projektů mohou dále rozšiřovat základní systém projektu rozšířením modelu automatizačních objektů. Tyto jsou definovány jako součást automatizačního objektu DTE a slouží k rozšiřování objektu projektu, `ProjectItem` objektu a `Configuration` objektu. Další informace naleznete v tématu [rozšíření objektu modelu základního projektu](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregace na více úrovních

Implementace podtypu projektu, která obaluje dílčí typ projektu nižší úrovně, musí být naprogramována v družstvu, aby mohl podtyp interního projektu správně fungovat. Seznam odpovědností při programování zahrnuje:

- Implementace podtypu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> projektu, který je zabalení vnitřního podtypu, musí delegovat na <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementaci podtypu vnitřního projektu pro obě <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metody a.

- <xref:EnvDTE80.IInternalExtenderProvider>Implementace podtypu projektu obálky musí delegovat na jeho vnitřní typ projektu. Konkrétně implementace <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> potřebuje získat řetězec názvů z interního typu projektu a pak zřetězit řetězce, které chce přidat jako rozšířené.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>Implementace podtypu projektu obálky musí vytvořit instanci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objektu jeho interního typu projektu a umístit jej jako privátního delegáta, protože pouze objekt konfigurace projektu základní projekt přímo ví, že existuje objekt konfigurace podtypu projektu obálky. Vnější typ projektu může zpočátku zvolit konfigurační rozhraní, které chce zpracovat přímo, a poté delegovat zbytek na implementaci dílčího typu vnitřního projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Podpůrná rozhraní

Základní projekt deleguje volání k podpoře rozhraní přidaných podtypem projektu pro rozšiřování různých aspektů jeho implementace. To zahrnuje rozšíření objektů konfigurace projektu a různých objektů prohlížeče vlastností. Tato rozhraní jsou načtena voláním metody `QueryInterface` `punkOuter` (ukazatele na `IUnknown` ) Agregátoru podtypu vnějšího projektu.

|Rozhraní|Podtyp projektu|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umožňuje podtypemu projektu:<br /><br /> – Poskytněte implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />– Řízení spuštění ladicího programu umožněním podtypu projektu poskytnout jeho vlastní implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />– Zakažte vyhodnocení výrazu v době návrhu odpovídajícím způsobem `DBGLAUNCH_DesignTimeExprEval` při jeho implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Umožňuje podtypemu projektu:<br /><br /> – Rozšíříte-li <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> projekt pro přidání nebo odebrání vlastností nezávisle na konfiguraci projektu.<br />– Rozšíříte objekt automatizace projektu ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) projektu.<br /><br /> Výše uvedené hodnoty vlastností jsou odebírány od <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> výčtu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umožňuje, aby podtyp projektu namapoval zpátky na <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objekt podle objektu procházení konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umožňuje, aby podtyp projektu namapoval zpátky na <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> `VSITEMID` objekt nebo, a to s ohledem na objekt procházení konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umožňuje dílčímu typu projektu uchovat libovolná strukturovaná data XML do souboru projektu (. vbproj nebo. csproj). Tato data nejsou viditelná pro MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umožňuje podtypemu projektu:<br /><br /> – Přidejte nové vlastnosti MSBuild, které se mají zachovat.<br />-Odebrání zbytečných vlastností z MSBuild.<br />-Dotaz na aktuální hodnotu vlastnosti MSBuild.<br />– Změna aktuální hodnoty vlastnosti MSBuild|

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
