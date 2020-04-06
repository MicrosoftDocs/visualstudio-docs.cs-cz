---
title: Vlastnosti a metody rozšířené podle podtypů projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706200"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Vlastnosti a metody rozšířené prostřednictvím podtypů projektů
Podtyp projektu má velkou moc ovlivnit chování projektu, protože je konstruován jako agregátor základního projektu. Tato část shrnuje některé funkce, které lze vylepšit nebo upravit podtypy projektu.

## <a name="features-gained-by-aggregation"></a>Funkce získané agregací
 Následující tabulka shrnuje mnoho metod, které agregace umožňuje podtypy projektu přepsat v základních projektech.

|Metody přepsané agregací|Podtyp projektu|
|---------------------------------------|---------------------|
|Od <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Umožňuje podtyp projektu<br /><br /> - Změna titulku a ikony uzlu projektu.<br />- Zcela přepsat `Browse` objekt projektu.<br />- Řízení, zda lze projekt přejmenovat.<br />- Řídit pořadí řazení.<br />- Ovládejte kontext uživatele pro dynamickou nápovědu.|
|Od <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Umožňuje podtypu projektu řídit, jaké kontextové služby jsou poskytovány návrhářům a editorům.|
|Od <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Umožňuje podtyp projektu<br /><br /> - Podílet se na příkaz směrování pro příkazy projektu.<br />- Přidat, odebrat, nebo zakázat oba příkazy okolního projektu a Průzkumník řešení aktivní příkazy.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Umožňuje podtypu projektu filtrovat, co se uživateli zobrazí v dialogovém okně **Přidat novou položku.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Umožňuje podtyp projektu<br /><br /> - Určete výchozí generátor dané přípona souboru.<br />- Mapujte jméno generátoru čitelného pro člověka na objekt COM.|

## <a name="properties-used-by-project-subtypes"></a>Vlastnosti používané podtypy projektu
 Systém prostředí a základního projektu <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> může <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> použít vlastnosti z a výčty popsané v následující tabulce k povolení podtypu projektu k řízení různých funkcí systému projektu.

|Vlastnost VSHPROPID|Podtyp projektu|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Umožňuje podtypu projektu řídit obsah dialogového okna **Přidat položku.** Podtyp projektu může poskytnout novou specifikaci adresářů šablon, přidat nové druhy položek, odebrat existující položky a reorganizovat podmnožinu položek v dialogovém okně **Přidat položku** v základním projektu.|
|`PropertyPagesCLSIDList`|Umožňuje podtypu projektu přidávat nebo odebírat stránky vlastností nezávislé na konfiguraci.|
|`CfgPropertyPagesCLSIDList`|Umožňuje podtypu projektu přidávat nebo odebírat stránky vlastností závislé na konfiguraci.|
|`ExtObjectCATID`|Umožňuje podtypu projektu poskytnout rozšíření automatizace pro objekty projektu nebo položky projektu znalostí zařízení CATID zařízení Extender. Podtyp projektu může například poskytnout `Project.Extender("<subtype>")` vlastní objekt.|
|`BrowseObjectCATID`|Umožňuje podtypu projektu poskytnout rozšíření automatizace `Browse` pro objekt znalostí zařízení CATID zařízení Extender. Například podtyp projektu můžete přidat další <xref:EnvDTE.Project.Properties%2A> vlastnosti do kolekce.|
|`CfgBrowseObjectCATID`|Umožňuje podtypu projektu poskytnout zařízení Automation Extender pro objekt procházení konfigurace projektu. Například podtyp projektu můžete přidat další <xref:EnvDTE.Configuration.Properties%2A> vlastnosti do kolekce.|
|`CfgExtObjectCATID`|Umožňuje podtypu projektu poskytnout zařízení Automation Extender pro konfigurační objekt.|
|`DefaultPlatformName`|Umožňuje podtypu projektu určit název platformy pro objekty konfigurace projektu.|

 Základní projekt poskytuje výchozí implementaci výše uvedených vlastností. Základní projekt získá tyto `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> voláním na nejvzdálenější podtyp projektu, což umožňuje podtyp projektu přepsat implementaci vlastností.

## <a name="see-also"></a>Viz také
- [Návrh podtypů projektů](../../extensibility/internals/project-subtypes-design.md)
