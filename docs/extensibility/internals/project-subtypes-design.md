---
title: Projektový podtyp Design | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706448"
---
# <a name="project-subtypes-design"></a>Návrh podtypů projektů

Podtypy projektu umožňují VSPackages rozšířit projekty na základě Modulu pro sestavení Microsoft (MSBuild). Použití agregace umožňuje znovu použít většinu základního spravovaného systému projektu implementovanév ale [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stále přizpůsobit chování pro konkrétní scénář.

 Následující témata podrobně popisují základní návrh a implementaci podtypů projektu:

- Návrh podtypu projektu.

- Víceúrovňová agregace.

- Podpůrná rozhraní.

## <a name="project-subtype-design"></a>Návrh podtypu projektu

Inicializace podtypu projektu je dosaženo agregací <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> hlavní a objekty. Tato agregace umožňuje podtypu projektu přepsat nebo vylepšit většinu možností základního projektu. Podtypy projektu získají první šanci <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>zpracovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> vlastnosti pomocí příkazů , pomocí příkazů a a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>a řízení položek projektu pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Podtypy projektu mohou také rozšířit:

- Objekty konfigurace projektu.

- Objekty závislé na konfiguraci.

- Objekty procházení nezávislé na konfiguraci.

- Objekty automatizace projektu.

- Kolekce vlastností automatizace projektu.

Další informace o rozšiřitelnosti podle podtypů projektu naleznete v [tématu Vlastnosti a metody rozšířené podtypy projektu](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Soubory zásad

Prostředí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje příklad rozšíření systému základního projektu o podtyp projektu při implementaci souborů zásad. Soubor zásad umožňuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formování prostředí správou funkcí, které zahrnují Průzkumník řešení, dialogové okno Přidat **projekt,** dialogové okno Přidat novou **položku** a dialogové okno **Vlastnosti.** Podtyp zásady přepíše a vylepšuje tyto funkce prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>a `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementace.

### <a name="aggregation-mechanism"></a>Mechanismus agregace

Mechanismus agregace podtypu projektu prostředí podporuje více úrovní agregace, což umožňuje implementaci rozšířeného podtypu dalším ochucením ochuceného projektu. Podpůrné objekty podtypu projektu, například <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, jsou také navrženy tak, aby umožňovaly více úrovní vrstvení. V souladu s omezeními pravidel agregace COM a COM je třeba podtypy projektů a základní projekty naprogramovat kooperativně, aby se vnitřní podtyp nebo základní projekt mohl správně účastnit delegování volání metod a správy počty odkazů. To znamená, že projekt, který má být agregován, musí být naprogramován tak, aby podporoval agregaci.

Následující obrázek znázorňuje schematickou reprezentaci víceúrovňové agregace podtypu projektu.

![Obrázek víceúrovňového projektu Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Víceúrovňová agregace podtypu projektu se skládá ze tří úrovní, základního projektu, který je agregován podtypem projektu, a poté dále agregován rozšířeným podtypem projektu. Obrázek se zaměřuje na některé podpůrné rozhraní, které jsou k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dispozici jako součást architektury podtypu projektu.

### <a name="deployment-mechanisms"></a>Mechanismy nasazení

Mezi mnoho funkcí systému základního projektu rozšířené podtypu projektu jsou mechanismy nasazení. Podtyp projektu ovlivňuje mechanismy nasazení implementací konfiguračních rozhraní (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) , která jsou načtena voláním rozhraní QueryInterface na . Ve scénáři, kde podtyp projektu i rozšířený podtyp projektu přidávají různé `QueryInterface` implementace konfigurace, základní projekt `IUnknown`volá podtyp rozšířeného projektu . Pokud podtyp vnitřního projektu obsahuje implementaci konfigurace, o kterou základní projekt žádá, pokročilý podtyp projektu deleguje na implementaci poskytovanou podtypem vnitřního projektu. Jako mechanismus pro zachování stavu z jedné úrovně agregace do <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> druhé, všechny úrovně podtypů projektu implementovat zachovat non-sestavení související data XML do souborů projektu. Další informace naleznete [v tématu Persisting Data in the MSBuild Project File](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>je implementována jako mechanismus pro načtení rozšíření automatizace z podtypů projektu.

Následující obrázek se zaměřuje na implementaci rozšíření automatizace, zejména objekt procházení konfigurace projektu, který používají podtypy projektu k rozšíření systému základního projektu.

![Obrázek automatického zařízení pro automatické rozšíření aplikace VS Project Flavor](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Podtypy projektu mohou dále rozšířit systém základního projektu rozšířením objektového modelu automatizace. Ty jsou definovány jako součást objektu automatizace DTE a `ProjectItem` slouží k `Configuration` rozšíření Project objektu, objektu a objektu. Další informace naleznete [v tématu Rozšíření objektového modelu základního projektu](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Víceúrovňová agregace

Implementace podtypu projektu, která zabalí podtyp projektu nižší úrovně, musí být naprogramována kooperativně, aby podtyp vnitřního projektu fungoval správně. Seznam odpovědností za programování zahrnuje:

- Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> podtypu projektu, který obtéká vnitřní podtyp, musí delegovat na <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> implementaci podtypu vnitřního projektu pro metody i <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> metody.

- Implementace <xref:EnvDTE80.IInternalExtenderProvider> podtypu projektu obálky musí delegovat na podtyp vnitřního projektu. Zejména provádění <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> potřebuje získat řetězec názvů z podtypu vnitřní projekt a potom zřetězit řetězce, které chce přidat jako extendery.

- Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> podtypu projektu obálky musí vytvořit instanci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objektu jeho vnitřního podtypu projektu a podržet jej jako soukromého delegáta, protože pouze objekt konfigurace projektu základního projektu přímo ví, že existuje objekt konfigurace podtypu obálky projektu. Vnější podtyp projektu můžete zpočátku zvolit konfigurační rozhraní, která chce přímo zpracovat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>a pak delegovat zbytek na vnitřní projekt podtyp implementace .

## <a name="supporting-interfaces"></a>Podpůrná rozhraní

Základní projekt deleguje volání na podpůrná rozhraní přidaná podtypem projektu, aby se rozšířily různé aspekty jeho implementace. To zahrnuje rozšíření objektů konfigurace projektu a různých objektů prohlížeče vlastností. Tato rozhraní jsou načteny `QueryInterface` `punkOuter` voláním na `IUnknown`(ukazatel na ) nejvzdálenější projekt agregátor podtypu.

|Rozhraní|Podtyp projektu|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umožňuje podtypu projektu:<br /><br /> - Poskytnout provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />- Ovládejte spuštění ladicího programu tím, že podtypu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>projektu poskytnete vlastní implementaci programu .<br />- Zakázat vyhodnocení vyjádření návrhu `DBGLAUNCH_DesignTimeExprEval` vhodným způsobem zpracováním případu při jeho provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Umožňuje podtypu projektu:<br /><br /> - Rozšíření <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> projektu přidat nebo odebrat konfiguraci nezávislé vlastnosti projektu.<br />- Rozšířit objekt automatizace projektu (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>) projektu.<br /><br /> Výše uvedené hodnoty <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> vlastností jsou převzaty z výčtu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umožňuje podtypu projektu mapovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> zpět na objekt daný objekt procházení konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umožňuje podtypu projektu mapovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> zpět `VSITEMID` na objekt nebo objekt, vzhledem k tomu, že objekt procházení konfigurace projektu.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umožňuje podtypu projektu zachovat libovolná strukturovaná data XML do souboru projektu (.vbproj nebo .csproj). Tato data nejsou viditelná pro MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umožňuje podtypu projektu:<br /><br /> - Přidejte nové vlastnosti MSBuild, které mají být trvalé.<br />- Odebrat nepotřebné vlastnosti z MSBuild.<br />- Dotaz na aktuální hodnotu MSBuild vlastnost.<br />- Změna aktuální hodnoty vlastnosti MSBuild.|

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
