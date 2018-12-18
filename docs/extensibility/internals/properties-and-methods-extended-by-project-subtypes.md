---
title: Vlastnosti a metody prodloužena podtypů projekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23510ffbb42e0c0c37c07e0ee80ae15f99e5df00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132088"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Vlastnosti a metody prodloužena podtypů projektu
Podtyp projekt obsahuje mnoho napájení, jež ovlivňují chování projektu, protože je sestavený jako agregátoru základní projektu. Tento oddíl shrnuje některé funkce, které mohou být rozšířené nebo upraveném podtypů projektu.  
  
## <a name="features-gained-by-aggregation"></a>Funkce nebyly získány prostřednictvím agregace  
 Následující tabulka shrnuje řadu metody, které agregace umožňuje podtypů projektu k přepsání v základní projekty.  
  
|Metody přepsat agregace|Podtyp projektu|  
|---------------------------------------|---------------------|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Umožňuje k podtypem projektu<br /><br /> -Změna titulku a ikonu uzel projektu.<br />-Zcela přepsat projektu `Browse` objektu.<br />-Řídit, jestli můžete přejmenovat projektu.<br />-Pořadí řazení control.<br />– Kontext uživatele ovládací prvek pro dynamické nápovědy.|  
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Umožňuje podtypem projektu k řízení, jaké kontextové služeb návrháři a editory.|  
|Z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Umožňuje k podtypem projektu<br /><br /> -Účastnit směrování příkazů pro příkazy projektu.<br />-Přidat, odebrat ani vypnout vedlejším příkazy projektu a aktivní příkazy Průzkumníku řešení.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Umožňuje dílčí projekt k filtrování, co uživatel uvidí v **přidat novou položku** dialogové okno.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Umožňuje k podtypem projektu<br /><br /> -Určete výchozí generátor danou příponu souboru.<br />-Mapovat lidského čitelný generátor název objektu COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Vlastnosti používané podtypů projektu  
 Systém projektu prostředí a základní můžete používat vlastnosti z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> a <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> výčty podrobně popsané v následující tabulce povolit podtypem projektu k ovládání různých funkcí systému projektu.  
  
|Vlastnost VSHPROPID|Podtyp projektu|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Umožňuje podtypem projektu řídit obsah **přidat položku** dialogové okno. Podtyp projektu můžete zadejte specifikaci nové šablony adresářů, přidat nové typy položek, odeberte existující položky a reorganizovat podmnožině položek v základní projektu **přidat položku** dialogové okno.|  
|`PropertyPagesCLSIDList`|Umožňuje podtypem projektu přidat nebo odebrat stránky vlastností konfigurace nezávislé.|  
|`CfgPropertyPagesCLSIDList`|Umožňuje podtypem projektu přidat nebo odebrat stránky vlastností závislá na konfiguraci.|  
|`ExtObjectCATID`|Umožňuje podtypem projektu zajistit Extender automatizace pro projekt nebo projekt položky objekty musíte znát CATID rozšiřujícího objektu. Například podtypem projektu můžete zadat vlastní `Project.Extender("<subtype>")` objektu.|  
|`BrowseObjectCATID`|Umožňuje podtypem projektu zajistit Extender automatizace pro `Browse` objektu musíte znát CATID rozšiřujícího objektu. Například podtypem projektu můžete přidat další vlastnosti, které chcete <xref:EnvDTE.Project.Properties%2A> kolekce.|  
|`CfgBrowseObjectCATID`|Umožňuje podtypem projektu zajistit Extender automatizace pro objekt procházet konfigurace projektu. Například podtypem projektu můžete přidat další vlastnosti, které chcete <xref:EnvDTE.Configuration.Properties%2A> kolekce.|  
|`CfgExtObjectCATID`|Umožňuje podtypem projektu zajistit Extender automatizace pro objekt konfigurace.|  
|`DefaultPlatformName`|Umožňuje podtypem projektu určit název platformy pro objekty konfigurace projektu.|  
  
 Základní projekt poskytuje výchozí implementaci třídy výše uvedené vlastnosti. Získá základní projekt tak, že volání `QueryInterface` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> na dílčí nejkrajnější projektu, což umožňuje dílčí projektu přepsat implementace vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)