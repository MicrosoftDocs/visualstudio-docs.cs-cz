---
title: Vlastnosti a metody rozšířené podtypy projektů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f5f67ac70b7ca6d5151a9115f20be88f6984d52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725348"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Vlastnosti a metody rozšířené prostřednictvím podtypů projektů
Podtyp projektu má velký výkon pro ovlivnění chování projektu, protože je vytvořen jako agregátor základního projektu. V této části jsou shrnuty některé funkce, které mohou být rozšířeny nebo upraveny podtypy projektu.

## <a name="features-gained-by-aggregation"></a>Funkce získané agregací
 Následující tabulka shrnuje mnoho metod, které agregace umožňuje přepsat podtypy projektů v základních projektech.

|Metody přepsané agregací|Podtyp projektu|
|---------------------------------------|---------------------|
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Povoluje podtyp projektu pro<br /><br /> -Změňte titulek a ikonu uzlu projektu.<br />-Kompletně přepíše objekt `Browse` projektu.<br />-Určuje, zda lze projekt přejmenovat.<br />– Řízení pořadí řazení.<br />-Control kontext uživatele pro dynamickou nápovědu.|
|Z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Umožňuje dílčímu typu projektu řídit, které kontextové služby jsou k dispozici pro návrháře a editory.|
|Z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Povoluje podtyp projektu pro<br /><br /> – Je součástí směrování příkazů pro příkazy projektu.<br />– Přidejte, odeberte nebo zakažte jak příkazy okolí projektu, tak Průzkumník řešení aktivní příkazy.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Umožňuje, aby podtyp projektu vyfiltroval, co uživatel uvidí v dialogovém okně **Přidat novou položku** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Povoluje podtyp projektu pro<br /><br /> – Určení výchozího generátoru pro danou příponu souboru.<br />– Namapujte název generátoru pro lidské čtení na objekt COM.|

## <a name="properties-used-by-project-subtypes"></a>Vlastnosti používané podtypy projektu
 Prostředí a základní projektový systém mohou používat vlastnosti z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> a <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> výčty, které jsou popsány v následující tabulce, pro povolení podtypu projektu pro řízení různých funkcí systému projektu.

|Vlastnost VSHPROPID|Podtyp projektu|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Umožňuje podtypům projektu řídit obsah dialogového okna **Přidat položku** . Podtyp projektu může poskytnout novou specifikaci adresářů šablon, přidat nové druhy položek, odebrat existující položky a změnit uspořádání podmnožiny položek v dialogovém okně **Přidat položku** základního projektu.|
|`PropertyPagesCLSIDList`|Umožňuje dílčímu typu projektu přidat nebo odebrat stránky vlastností nezávislé na konfiguraci.|
|`CfgPropertyPagesCLSIDList`|Umožňuje dílčímu typu projektu přidat nebo odebrat stránky vlastností závislé na konfiguraci.|
|`ExtObjectCATID`|Umožňuje podtypu projektu poskytnout objekt pro automatizaci automatizace pro objekty projektu nebo položky projektu tím, že bude vědět CATID. Například podtyp projektu může poskytnout vlastní objekt `Project.Extender("<subtype>")`.|
|`BrowseObjectCATID`|Umožňuje dílčímu typu projektu poskytnout objekt pro `Browse` pro automatizaci automatizace tím, že bude vědět, že rozšiřuje CATID. Například podtyp projektu může přidat do kolekce <xref:EnvDTE.Project.Properties%2A> další vlastnosti.|
|`CfgBrowseObjectCATID`|Umožňuje dílčímu typu projektu poskytnout pro objekt procházení konfigurace projektu rozšířenou automatizaci. Například podtyp projektu může přidat do kolekce <xref:EnvDTE.Configuration.Properties%2A> další vlastnosti.|
|`CfgExtObjectCATID`|Umožňuje dílčímu typu projektu poskytnout pro objekt konfigurace rozšířenou automatizaci.|
|`DefaultPlatformName`|Umožňuje podtypu projektu určit název platformy pro objekty konfigurace projektu.|

 Základní projekt poskytuje výchozí implementaci výše uvedených vlastností. Základní projekt je získá voláním `QueryInterface` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> na vnějším typu projektu, čímž umožní podtyp projektu přepsat implementaci vlastností.

## <a name="see-also"></a>Viz také:
- [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)