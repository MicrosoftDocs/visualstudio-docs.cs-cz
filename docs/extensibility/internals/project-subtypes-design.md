---
title: Podtypy projektů návrhu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9032da4a8884c940973865016bf0bbec955ebb5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876591"
---
# <a name="project-subtypes-design"></a>Návrh podtypů projektů
Podtypy projektů umožní rozšířením VSPackages rozšířit projekty založené na Microsoft Build Engine (MSBuild). Použití agregace umožňuje znovu použít hromadné implementované v systému projektu jádra managed [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ještě dál přizpůsobit chování pro konkrétní scénář.  
  
 Následujících tématech jsou upřesněny o základním návrhu a implementace podtypů projektů:  
  
-   Návrh podtyp projektu.  
  
-   Víceúrovňové agregace.  
  
-   Podpora rozhraní.  
  
## <a name="project-subtype-design"></a>Návrh podtyp projektu  
 Inicializace podtyp projektu je dosáhnout sečtením hlavní <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objekty. Tato agregace umožňuje podtyp projektu k přepsání nebo rozšíření většinu funkcí základního projektu. Podtypy projektů získat první příležitosti ke zpracování pomocí vlastnosti <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, příkazy pomocí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>a pomocí správy položky projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Můžete také rozšířit podtypů projektů:  
  
- Objekty konfigurace projektu.  
  
- Konfigurace závislé objekty.  
  
- Nezávislé na konfiguraci procházet objekty.  
  
- Objekty automatizace projektu.  
  
- Automatizace vlastnost kolekce projektů.  
  
  Další informace o rozšíření prostřednictvím podtypů projektů, naleznete v tématu [vlastnosti a metody rozšířené prostřednictvím podtypů projektů](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Zásady souborů  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Prostředí poskytuje příklad rozšíření systému základního projektu s podtyp projektu v rámci příslušné implementace zásad souborů. Soubor zásad umožňuje tvarování z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí tím, že spravuje funkcí, které zahrnují v Průzkumníku řešení **přidat projekt** dialogovém okně **přidat novou položku** dialogové okno a  **Vlastnosti** dialogové okno. Podtyp zásady přepíše a rozšiřuje tyto funkce prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implementace.  
  
##### <a name="aggregation-mechanism"></a>Mechanismus agregace  
 Mechanismus agregace podtyp projektu prostředí podporuje několik úrovní agregace, což umožní pokročilé podtyp provádí další flavoring flavored projektu. Navíc podpůrné objekty projekt podtypu, jako například <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, jsou navržené tak, aby více úrovní vrstvení. V souladu s omezeními COM a modelu COM pravidla agregace, podtypů projektů a základní projekty musí být naprogramovány kooperativně na povolit vnitřní podtyp nebo základního projektu správně účastnit delegování volání metod a správu počty odkazů . To znamená projekt se dají agregovat musí být naprogramovány na agregace.  
  
 Následující obrázek znázorňuje schématem agregace podtyp víceúrovňových projektu.  
  
 ![Visual Studio víceúrovňové projectflavor grafika](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Podtyp víceúrovňové projektu  
  
 Agregace podtyp víceúrovňových projekt se skládá ze tří úrovní základní projekt, který je agregované podle podtyp projektu a další agregované podle podtyp pokročilé projektu. Na obrázku se zaměřuje na některé podpůrné rozhraní, které jsou k dispozici jako součást [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] architektura podtyp projektu.  
  
##### <a name="deployment-mechanisms"></a>Mechanismy nasazení  
 Mezi mnoho systému základního projektu jsou funkce vylepšit určením podtyp projektu mechanismy nasazení. Podtyp projektu ovlivňuje mechanismy nasazení prostřednictvím implementace rozhraní pro konfiguraci (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>), která se načítají pomocí volání QueryInterface u <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. Ve scénáři, kde podtyp projektu a podtyp pokročilé projektu přidejte jinou konfiguraci implementace, volá základní projekt `QueryInterface` podtypu pokročilé projektu `IUnknown`. Pokud podtyp vnitřní projekt obsahuje implementaci konfigurace, které je základní projekt žádá o pokročilé projektu podtyp delegáty pro implementaci poskytované podtyp vnitřní projektu. Jako mechanismus pro uchování stavu z jedné agregace úrovně do druhého, implementovat všechny úrovně podtypů projektů <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> k uchování jiných sestavení související XML data do souborů projektu. Další informace najdete v tématu [uchování dat v souboru projektu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> je implementován jako mechanismus pro načtení rozšiřující objekty z podtypů projektů.  
  
 Na následujícím obrázku se zaměřuje na implementaci zařízení extender automatizace, procházet objekt konfigurace projektu, zejména prostřednictvím podtypů projektů používané k rozšíření systému základního projektu.  
  
 ![Obrázek zařízení Extender automaticky Flavor projektu VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Zařízení Extender automatizace podtyp projektu.  
  
 Podtypy projektů můžete rozšířit systému základního projektu rozšíření objektového modelu automatizace. Tyto jsou definované jako součást automatizační objekt DTE a slouží k rozšíření objekt projektu `ProjectItem` objektu a `Configuration` objektu. Další informace najdete v tématu [rozšíření objektového modelu projektu Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Víceúrovňové agregace  
 Implementace podtyp projektu, která zabalí nižší úrovně projektu podtyp musí být naprogramovány kooperativně na povolit podtyp projektu vnitřní fungování. Obsahuje seznam programovacích odpovědnosti:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Provádění podtyp projektu, který zahrnuje vnitřní podtypu musí delegovat <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> provádění podtyp vnitřní projektu pro obě <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> metody.  
  
-   <xref:EnvDTE80.IInternalExtenderProvider> Provádění podtyp projektu obálky musí delegovat, jeho vnitřní projektu podtyp. Zejména provádění <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> musí získat řetězec názvů podtypem vnitřní projektu a pak je zřetězí řetězce chce přidat jako zařízení Extender.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Provádění podtyp projektu obálky musí vytvořit instanci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objekt jeho vnitřní podtyp projektu a podržte ji jako soukromý delegát, protože pouze objekt konfigurace projektu základního projektu přímo ví, obálky objekt konfigurace podtyp projektu existuje. Podtyp vnější projektu může zpočátku zvolte chce zpracovat přímo rozhraní pro konfiguraci a následně delegovat klidovém stavu a podtyp projektu vnitřní implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Podpora rozhraní  
 Základní projekt deleguje volání podporuje rozhraní přidal podtyp projektu rozšíření různé aspekty jeho implementace. To zahrnuje rozšíření objekty konfigurace projektu a různé objekty vlastnost prohlížeče. Tato rozhraní se načítají pomocí volání `QueryInterface` na `punkOuter` (ukazatel `IUnknown`) z agregátoru podtyp nejkrajnější projektu.  
  
|Rozhraní|Podtyp projektu|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Umožňuje podtyp projektu na:<br /><br /> -Zadání implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Řízení spuštění ladicího programu tím, že podtyp projektu poskytnout jejich vlastní implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />– Zakažte vyhodnocení výrazu v době návrhu řeší odpovídajícím způsobem `DBGLAUNCH_DesignTimeExprEval` případu v jeho provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Umožňuje podtyp projektu na:<br /><br /> -Rozšířit <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> projektu pro přidání nebo odebrání nezávislé vlastnosti konfigurace projektu.<br />-Rozšířit automatizační objekt projektu (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) projektu.<br /><br /> Výše uvedené hodnoty vlastností jsou převzaty z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> výčtu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Umožňuje podtyp projektu mapovat zpět <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objekt dle procházet objekt konfigurace projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Umožňuje podtyp projektu mapovat zpět <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nebo `VSITEMID` objekt dle procházet objekt konfigurace projektu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Umožňuje podtyp projektu k uchování libovolná XML strukturovaná data do souboru projektu (.vbproj nebo .csproj). Tato data se nezobrazuje na MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Umožňuje podtyp projektu na:<br /><br /> -Přidáte nové vlastnosti nástroje MSBuild natrvalo.<br />-Odeberte nepotřebné vlastnosti MSBuild.<br />-Dotazu pro aktuální hodnota vlastnosti nástroje MSBuild.<br />– Změňte aktuální hodnota vlastnosti nástroje MSBuild.|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>