---
title: Vlastnosti a metody rozšířené podtypy projektů | Microsoft Docs
description: Přečtěte si o funkcích, které mohou podtypy projektů zvýšit nebo upravit, což vám umožní přizpůsobit chování projektových systémů sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d5d81135a2571db3c84b67acb2fa08e4f83f57d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970059"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Vlastnosti a metody rozšířené prostřednictvím podtypů projektů
Podtyp projektu má velký výkon pro ovlivnění chování projektu, protože je vytvořen jako agregátor základního projektu. V této části jsou shrnuty některé funkce, které mohou být rozšířeny nebo upraveny podtypy projektu.

## <a name="features-gained-by-aggregation"></a>Funkce získané agregací
 Následující tabulka shrnuje mnoho metod, které agregace umožňuje přepsat podtypy projektů v základních projektech.

|Metody přepsané agregací|Podtyp projektu|
|---------------------------------------|---------------------|
|Od <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Povoluje podtyp projektu pro<br /><br /> -Změňte titulek a ikonu uzlu projektu.<br />-Zcela přepsat `Browse` objekt projektu.<br />-Určuje, zda lze projekt přejmenovat.<br />– Řízení pořadí řazení.<br />-Control kontext uživatele pro dynamickou nápovědu.|
|Od <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Umožňuje dílčímu typu projektu řídit, které kontextové služby jsou k dispozici pro návrháře a editory.|
|Od <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Povoluje podtyp projektu pro<br /><br /> – Je součástí směrování příkazů pro příkazy projektu.<br />– Přidejte, odeberte nebo zakažte jak příkazy okolí projektu, tak Průzkumník řešení aktivní příkazy.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Umožňuje, aby podtyp projektu vyfiltroval, co uživatel uvidí v dialogovém okně **Přidat novou položku** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Povoluje podtyp projektu pro<br /><br /> – Určení výchozího generátoru pro danou příponu souboru.<br />– Namapujte název generátoru pro lidské čtení na objekt COM.|

## <a name="properties-used-by-project-subtypes"></a>Vlastnosti používané podtypy projektu
 Prostředí a základní projektový systém mohou použít vlastnosti z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> a <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> výčty, které jsou popsány v následující tabulce, pro povolení podtypu projektu pro řízení různých funkcí systému projektu.

|Vlastnost VSHPROPID|Podtyp projektu|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Umožňuje podtypům projektu řídit obsah dialogového okna **Přidat položku** . Podtyp projektu může poskytnout novou specifikaci adresářů šablon, přidat nové druhy položek, odebrat existující položky a změnit uspořádání podmnožiny položek v dialogovém okně **Přidat položku** základního projektu.|
|`PropertyPagesCLSIDList`|Umožňuje dílčímu typu projektu přidat nebo odebrat stránky vlastností nezávislé na konfiguraci.|
|`CfgPropertyPagesCLSIDList`|Umožňuje dílčímu typu projektu přidat nebo odebrat stránky vlastností závislé na konfiguraci.|
|`ExtObjectCATID`|Umožňuje podtypu projektu poskytnout objekt pro automatizaci automatizace pro objekty projektu nebo položky projektu tím, že bude vědět CATID. Například podtyp projektu může poskytnout vlastní `Project.Extender("<subtype>")` objekt.|
|`BrowseObjectCATID`|Umožňuje dílčímu typu projektu poskytnout objekt pro automatizaci automatizace pro `Browse` objekt tím, že bude vědět CATID. Například podtyp projektu může do kolekce přidat další vlastnosti <xref:EnvDTE.Project.Properties%2A> .|
|`CfgBrowseObjectCATID`|Umožňuje dílčímu typu projektu poskytnout pro objekt procházení konfigurace projektu rozšířenou automatizaci. Například podtyp projektu může do kolekce přidat další vlastnosti <xref:EnvDTE.Configuration.Properties%2A> .|
|`CfgExtObjectCATID`|Umožňuje dílčímu typu projektu poskytnout pro objekt konfigurace rozšířenou automatizaci.|
|`DefaultPlatformName`|Umožňuje podtypu projektu určit název platformy pro objekty konfigurace projektu.|

 Základní projekt poskytuje výchozí implementaci výše uvedených vlastností. Základní projekt je načte zavoláním `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> na podtyp na vnějším projektu, čímž umožní podtypu projektu přepsat implementaci vlastností.

## <a name="see-also"></a>Viz také
- [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)
