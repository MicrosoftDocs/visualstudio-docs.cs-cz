---
title: Šablony návrhu podtypů | Microsoft Docs
description: Zjistěte, jak podtypy projektů umožňují rozšíření projektů VSPackage na základě Microsoft Build Engine (MSBuild).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c04c8e681646aed6816c645defe7ffd87ac7033c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899690"
---
# <a name="project-subtypes-design"></a>Návrh podtypů projektů

Podtypy projektů umožňují rozšíření projektů VSPackage na základě Microsoft Build Engine (MSBuild). Použití agregace umožňuje opakovaně používat většinu základního spravovaného projektového systému implementované v , ale přesto přizpůsobit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chování pro konkrétní scénář.

 Následující témata podrobně popisují základní návrh a implementaci podtypů projektů:

- Návrh podtypu projektu.

- Agregace na více úrovních.

- Podpůrná rozhraní.

## <a name="project-subtype-design"></a>Návrh podtypu projektu

Inicializace podtypu projektu se dosahuje agregací hlavních objektů a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Tato agregace umožňuje, aby podtyp projektu přepíše nebo vylepšuje většinu možností základního projektu. Podtypy projektů získání první šanci na zpracování vlastností pomocí příkazů , pomocí příkazů a a správy <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> položek projektu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Podtypy projektů rozšiřují také:

- Objekty konfigurace projektu.

- Objekty závislé na konfiguraci.

- Objekty procházení nezávislé na konfiguraci.

- Objekty automatizace projektu.

- Kolekce vlastností automatizace projektu.

Další informace o rozšiřitelnosti podle podtypů projektů najdete v tématu Vlastnosti a metody rozšířené [podtypy projektu](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Soubory zásad

Prostředí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje příklad rozšíření základního projektového systému s podtypem projektu v implementaci souborů zásad. Soubor zásad umožňuje tvarování prostředí pomocí správy funkcí, které zahrnují Průzkumník řešení, dialogové okno Přidat projekt, dialogové okno Přidat novou položku a dialogové okno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Vlastnosti.    Podtyp zásad přepisuje a vylepšuje tyto funkce prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> a `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementací .

### <a name="aggregation-mechanism"></a>Agregační mechanismus

Agregační mechanismus podtypu projektu prostředí podporuje více úrovní agregace, což umožňuje implementaci pokročilého podtypu dalším příchutí projektu. Podpůrné objekty podtypu projektu, například , jsou také navržené tak, aby povolují <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> více úrovní vrstvení. V souladu s omezeními agregačními pravidly modelu COM a COM je potřeba podtypy projektů a základní projekty naprogramovat v rámci spolupráce, aby se vnitřní podtyp nebo základní projekt řádně zapojily do delegování volání metod a správy počtů odkazů. To znamená, že projekt, který se má agregovat, musí být naprogramován tak, aby podporoval agregaci.

Následující obrázek znázorňuje schématickou reprezentaci agregace podtypu víceúrovňového projektu.

![Visual Studio víceúrovňového projektu](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Agregace podtypu víceúrovňového projektu se skládá ze tří úrovní– základního projektu, který se agreguje podle podtypu projektu a následně agreguje podle pokročilého podtypu projektu. Obrázek se zaměřuje na některá podpůrná rozhraní, která jsou k dispozici jako součást architektury [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podtypu projektu.

### <a name="deployment-mechanisms"></a>Mechanismy nasazení

Mezi mnoho funkcí základního projektového systému vylepšených podtypem projektu patří mechanismy nasazení. Podtyp projektu ovlivňuje mechanismy nasazení implementací konfiguračních rozhraní (například a ), která se načítá <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> voláním queryInterface v <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . Ve scénáři, kde podtyp projektu i pokročilý podtyp projektu přidávají různé implementace konfigurace, volá základní projekt na podtyp rozšířeného `QueryInterface` projektu `IUnknown` . Pokud podtyp vnitřního projektu obsahuje implementaci konfigurace, kterou základní projekt žádá, rozšířený podtyp projektu deleguje na implementaci poskytovanou podtypem vnitřního projektu. Jako mechanismus pro zachování stavu z jedné úrovně agregace na jinou implementují všechny úrovně podtypů projektu, aby se data XML nesouvisená s sestavením uchovála <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> do souborů projektu. Další informace naleznete v části [Persisting Data in the MSBuild Project File](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> je implementován jako mechanismus pro načtení rozšiřujících typů automatizace z podtypů projektu.

Následující obrázek se zaměřuje na implementaci rozšiřující automatizace, zejména objekt procházení konfigurace projektu, který používají podtypy projektu k rozšíření základního projektového systému.

![Grafické rozšíření VS Project Flavor Auto Extender](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Podtypy projektů mohou dále rozšířit základní systém projektu rozšířením objektového modelu automatizace. Ty jsou definovány jako součást objektu automatizace DTE a slouží k rozšíření objektu Project, objektu a `ProjectItem` `Configuration` objektu . Další informace najdete v tématu [Rozšíření objektového modelu základního projektu](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agregace na více úrovních

Implementace podtypu projektu, která zabalí podtyp projektu nižší úrovně, musí být naprogramovaná spolupráce, aby podtyp vnitřního projektu správně fungoval. Seznam programovacích odpovědností zahrnuje:

- Implementace podtypu projektu, který zabaluje vnitřní podtyp, musí delegovat na implementaci podtypu vnitřního projektu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pro metody i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .

- Implementace <xref:EnvDTE80.IInternalExtenderProvider> podtypu obálkového projektu musí být delegovat na podtyp vnitřního projektu. Konkrétně implementace potřebuje získat řetězec názvů z podtypu vnitřního projektu a pak zřetězit řetězce, které chce přidat <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> jako extendery.

- Implementace podtypu obálkového projektu musí vytvořit instanci objektu podtypu vnitřního projektu a uchovat ho jako privátního delegáta, protože pouze objekt konfigurace projektu základního projektu přímo ví, že objekt konfigurace podtypu projektu obálky <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> existuje. Podtyp vnějšího projektu může zpočátku zvolit konfigurační rozhraní, která chce zpracovat přímo, a potom delegovat zbytek na implementaci podtypu vnitřního projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Podpůrná rozhraní

Základní projekt deleguje volání podpůrných rozhraní přidaných podtypem projektu, aby se rozšířily různé aspekty jeho implementace. To zahrnuje rozšíření objektů konfigurace projektu a různých objektů prohlížeče vlastností. Tato rozhraní se načítá voláním metody on (ukazatel na ) vnějšího `QueryInterface` agregátoru podtypu `punkOuter` `IUnknown` projektu.

|Rozhraní|Podtyp projektu|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umožňuje podtypu projektu:<br /><br /> – Zadejte implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />– Řídí spuštění ladicího programu tím, že umožňuje, aby podtyp projektu poskytoval vlastní implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />– Zakažte vyhodnocení výrazu v době návrhu tím, že v implementaci metody odpovídajícím způsobem `DBGLAUNCH_DesignTimeExprEval` zohodnotíte <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> případ.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Umožňuje podtypu projektu:<br /><br /> – Rozšíření <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> projektu pro přidání nebo odebrání vlastností projektu nezávislých na konfiguraci<br />– Rozšiřte objekt automatizace projektu ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) projektu.<br /><br /> Hodnoty vlastností uvedené výše jsou převzaty z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> výčtu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umožňuje mapování podtypu projektu zpět na <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objekt daného objektu procházení konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umožňuje, aby se podtyp projektu mapovat zpět na objekt nebo na daný objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> `VSITEMID` procházení konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umožňuje, aby podtyp projektu uchoval libovolná strukturovaná data XML do souboru projektu (.vbproj nebo .csproj). Tato data nejsou viditelná v nástroji MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umožňuje podtypu projektu:<br /><br /> – Přidejte nové vlastnosti nástroje MSBuild, které budou zachovány.<br />– Odebrání nepotřebných vlastností z nástroje MSBuild.<br />– Dotaz na aktuální hodnotu vlastnosti MSBuild.<br />– Změňte aktuální hodnotu vlastnosti MSBuild.|

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
