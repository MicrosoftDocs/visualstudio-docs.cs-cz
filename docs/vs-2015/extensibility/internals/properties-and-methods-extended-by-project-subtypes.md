---
title: Vlastnosti a metody rozšířené prostřednictvím podtypů projektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f74f1f4a88fb01e09b30e7987f1bcec1d450571a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765130"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Vlastnosti a metody rozšířené prostřednictvím podtypů projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projekt obsahuje velké možnosti, jež ovlivňují chování projektu, protože je vytvořen jako agregátoru základního projektu. Tento oddíl shrnuje některé z funkcí, které mohou být rozšířeného nebo změnit prostřednictvím podtypů projektů.  
  
## <a name="features-gained-by-aggregation"></a>Díky agregační funkce  
 Následující tabulka shrnuje mnoho metod, které umožňuje podtypů projektů k přepsání v projektech pro základní agregace.  
  
|Metody přepsat agregace|Podtyp projektu|  
|---------------------------------------|---------------------|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Umožňuje podtyp projektu do<br /><br /> -Změna titulků a ikona uzel projektu.<br />– Kompletně přepsat projektu `Browse` objektu.<br />-Řízení, zda lze přejmenovat projekt.<br />– Pořadí řazení ovládací prvek.<br />– Kontext uživatele ovládací prvek pro dynamická Nápověda.|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Umožňuje řídit, jaké kontextové služby jsou k dispozici na návrháři a editory podtyp projektu.|  
|Z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Umožňuje podtyp projektu do<br /><br /> -Součástí směrování příkazů pro příkazy projektu.<br />-Přidat, odebrat nebo zakázat příkazy okolí projektu a aktivní příkazy Průzkumníka řešení.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Umožňuje podtyp projektu k filtrování, se uživateli zobrazí v **přidat novou položku** dialogové okno.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Umožňuje podtyp projektu do<br /><br /> – Určení výchozí generátor zadané přípony souboru.<br />-Mapování názvu lidské čitelné generátoru na objekt modelu COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Vlastnosti používané prostřednictvím podtypů projektů  
 Vlastnosti z lze použít systém projektu prostředí a základní <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> a <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> výčty, které jsou podrobně popsané v následující tabulce umožňující podtyp projektu k ovládání různých funkcí systému projektu.  
  
|Vlastnost VSHPROPID|Podtyp projektu|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Umožňuje řídit obsah podtyp projektu **přidat položku** dialogové okno. Podtyp projektu můžete zadat novou specifikaci šablony adresářů, přidat nové typy položek, odebrání existující položky a reorganizovat podmnožině položek v základní projekt **přidat položku** dialogové okno.|  
|`PropertyPagesCLSIDList`|Umožňuje podtyp projektu pro přidání nebo odebrání stránky vlastností nezávislé na konfiguraci.|  
|`CfgPropertyPagesCLSIDList`|Umožňuje přidání nebo odebrání stránky vlastností závislé na konfiguraci podtyp projektu.|  
|`ExtObjectCATID`|Umožňuje poskytnout rozšiřující objekt automatizace pro projekt nebo projektu objektu položky musíte znát CATID rozšiřujícího objektu podtyp projektu. Například podtyp projektu můžete zadat vlastní `Project.Extender("<subtype>")` objektu.|  
|`BrowseObjectCATID`|Umožňuje poskytnout rozšiřující objekt automatizace pro podtyp projektu `Browse` znalost CATID rozšiřujícího objektu. Například podtyp projektu můžete přidat další vlastnosti <xref:EnvDTE.Project.Properties%2A> kolekce.|  
|`CfgBrowseObjectCATID`|Umožňuje poskytnout rozšiřující objekt automatizace pro procházení objekt konfigurace projektu podtyp projektu. Například podtyp projektu můžete přidat další vlastnosti <xref:EnvDTE.Configuration.Properties%2A> kolekce.|  
|`CfgExtObjectCATID`|Umožňuje poskytnout rozšiřující objekt automatizace pro objekt konfigurace podtyp projektu.|  
|`DefaultPlatformName`|Umožňuje určit název platformy pro objekty konfigurace projektu podtyp projektu.|  
  
 Základní projekt poskytuje výchozí implementaci třídy výše uvedené vlastnosti. Základní projekt získá tyto voláním `QueryInterface` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> podtypu nejkrajnější projektu, což umožní podtyp projektu přepsat implementaci vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)

