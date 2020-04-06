---
title: Uživatelské rozhraní vlastností projektu | Dokumenty společnosti Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706388"
---
# <a name="project-property-user-interface"></a>Uživatelské rozhraní vlastností projektu

Podtyp projektu může použít položky v dialogovém okně **Stránky vlastností** projektu tak, jak jsou dodávány základním projektem, skrýt nebo vytvořit ovládací prvky jen pro čtení a celé stránky tak, jak jsou dodány, nebo přidat stránky specifické pro podtyp projektu do dialogového okna **Stránky vlastností.**

## <a name="extending-the-project-property-dialog-box"></a>Rozšíření dialogového okna Vlastnost projektu

Podtyp projektu implementuje rozšiřující zařízení automatizace a objekty procházení konfigurace projektu. Tyto extendery <xref:EnvDTE.IFilterProperties> implementovat rozhraní, aby určité vlastnosti skryté nebo jen pro čtení. Dialogové okno **Stránky vlastností** základního projektu implementované základním projektem respektuje filtrování prováděné zařízeními Automation Extender.

Proces rozšíření dialogového okna **Vlastnost projektu** je popsán níže:

- Základní projekt načte extendery z podtypu projektu <xref:EnvDTE80.IInternalExtenderProvider> implementací rozhraní. Procházet, automatizace projektu a konfigurace projektu procházet objekty základního projektu všechny implementovat toto rozhraní.

- Implementace <xref:EnvDTE80.IInternalExtenderProvider> pro objekt procházení projektu a objekt automatizace <xref:EnvDTE80.IInternalExtenderProvider> projektu delegovat na implementaci agregátoru `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> podtypu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projektu (to znamená, že pro objekt projektu).

- Objekt procházení konfigurace základního <xref:EnvDTE80.IInternalExtenderProvider> projektu také implementuje přímo drátv automation extender z objektu konfigurace podtypu projektu. Jeho implementace deleguje <xref:EnvDTE80.IInternalExtenderProvider> rozhraní implementované agregátorem podtypu projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementovaný objektem procházení konfigurace <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projektu, vrátí objekt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, také implementována objektem procházení <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> konfigurace projektu, vrátí objekt.

- Podtyp projektu můžete určit příslušné CATID pro různé rozšiřitelné objekty základního projektu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> v době běhu načtením následujícíhodnoty:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Chcete-li zjistit CATIDpro rozsah projektu, podtyp projektu načte výše uvedené vlastnosti pro [VSITEMID. Kořen](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) z `VSITEMID typedef`. Podtyp projektu může také chtít určit, které stránky dialogového **okna Stránky vlastností** jsou zobrazeny pro projekt, jak závislé na konfiguraci, tak nezávislé na konfiguraci. Některé podtypy projektu může být nutné odebrat předdefinované stránky a přidat stránky specifické pro podtyp projektu. Chcete-li to povolit, projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> spravovaného klienta volá metodu pro následující vlastnosti:

- `VSHPROPID_PropertyPagesCLSIDList`— seznam clsidů nezávislých na konfiguraci oddělených středníkem.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`seznam clsidů závislých na konfiguraci oddělených středníkem.

Vzhledem k tomu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> že podtyp projektu agreguje objekt, může přepsat definici těchto vlastností a určit, která dialogová okna **Stránek vlastností** se zobrazí. Podtyp projektu můžete načíst tyto vlastnosti z vnitřní základní projekt a potom přidat nebo odebrat CLSIDpodle podle potřeby.

Nové stránky vlastností přidané podtypem projektu jsou předány objektu procházení konfigurace projektu z implementace základního projektu. Tento objekt procházení konfigurace projektu podporuje zařízení Automation Extender. Další informace o automationextendery naleznete [v tématu implementace a použití rozšíření automatizace](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Stránky vlastností implementované podtypem projektu volají <xref:EnvDTE.Project.Extender%2A> k načtení vlastního objektu procházení konfigurace podtypu projektu, který rozšiřuje objekt procházení konfigurace základního projektu.

## <a name="see-also"></a>Viz také

- <xref:EnvDTE.IFilterProperties>
- [Dialogové okno Stránky vlastností](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
