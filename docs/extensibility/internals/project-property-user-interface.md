---
title: Uživatelské rozhraní vlastnosti projektu | Microsoft Docs
description: Přečtěte si, jak mohou podtypy projektů upravovat dialogové okno stránky vlastností projektu, jak je zadáno v základním projektu.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77e3554f2a3fd3b0dc1d608bb7d0a1198116a4e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903586"
---
# <a name="project-property-user-interface"></a>Uživatelské rozhraní vlastností projektu

Podtyp projektu může použít položky v dialogovém okně **stránky vlastností** projektu, protože jsou dodány základním projektem, skrývat nebo provádět ovládací prvky jen pro čtení a celé stránky jako dodané nebo přidat stránky pro konkrétní projekt v dialogovém okně **stránky vlastností** .

## <a name="extending-the-project-property-dialog-box"></a>Rozšíření dialogového okna vlastností projektu

Podtyp projektu implementuje objekty pro automatizaci automatizace a objekty pro procházení konfigurace projektu. Tyto rozšířené implementace implementují <xref:EnvDTE.IFilterProperties> rozhraní, aby určité vlastnosti byly skryté nebo jen pro čtení. Dialogové okno **stránky vlastností** základního projektu implementovaného základním projektem respektuje filtrování prováděné pomocí rozšířených objektů automatizace.

Následující postup je popsaný v části proces rozšíření **vlastností projektu** :

- Základní projekt načte rozšířené typy z podtypu projektu implementací <xref:EnvDTE80.IInternalExtenderProvider> rozhraní. Všechny objekty základního projektu, které implementují toto rozhraní, jsou v procházení, automatizaci projektů a v konfiguraci projektu.

- Implementace <xref:EnvDTE80.IInternalExtenderProvider> pro objekt procházení projektu a delegáta objektu automatizace projektu pro <xref:EnvDTE80.IInternalExtenderProvider> implementaci Agregátoru podtypu projektu (to znamená `QueryInterface` pro <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objekt projektu).

- Základní objekt pro procházení konfigurace projektu také implementuje <xref:EnvDTE80.IInternalExtenderProvider> přímý přenos z objektu konfigurace podtypu projektu přímo do zařízení. Jeho implementace deleguje <xref:EnvDTE80.IInternalExtenderProvider> rozhraní implementované Agregátorem podtypu projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementované objektem procházení konfigurace projektu, vrátí <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objekt.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, který je implementován také objektem procházení konfigurace projektu, vrátí <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objekt.

- Podtyp projektu může určit vhodné CATID pro různé objekty, které mají základní projekt v době běhu, načtením následujících <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> hodnot:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Pro určení CATID pro rozsah projektu načte podtyp projektu výše uvedené vlastnosti pro [VSITEMID. Kořen](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) z `VSITEMID typedef` . Podtyp projektu může také chtít určit, které stránky **vlastností** dialogového okna se zobrazí pro projekt, jak závislé na konfiguraci, tak i na nezávisle na konfiguraci. Některé podtypy projektů mohou potřebovat odebrat předdefinované stránky a přidat konkrétní stránky podtypu projektu. Aby to bylo možné povolit, projekt spravovaného klienta volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodu pro následující vlastnosti:

- `VSHPROPID_PropertyPagesCLSIDList` – středníkem oddělený seznam identifikátorů CLSID na stránkách vlastností nezávislých na konfiguraci.

- `VSHPROPID_CfgPropertyPagesCLSIDList —` středníkem oddělený seznam identifikátorů CLSID na stránkách vlastností závislých na konfiguraci.

Vzhledem k tomu, že podtyp projektu agreguje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objekt, může přepsat definici těchto vlastností, aby bylo možné určit, které dialogová okna **stránky vlastností** budou zobrazena. Podtyp projektu může načíst tyto vlastnosti z vnitřního základního projektu a pak podle potřeby přidávat nebo odebírat identifikátory CLSID.

Nové stránky vlastností přidané podtypu projektu jsou předány objektem pro procházení konfigurace projektu ze základní implementace projektu. Tento objekt pro procházení konfigurace projektu podporuje rozšířené služby automatizace. Další informace o AutomationExtenders najdete v tématu [implementace a používání zařízení s rozšířenými automatizace](/previous-versions/0y92k2w2(v=vs.140)). Stránky vlastností implementované voláním podtypu projektu <xref:EnvDTE.Project.Extender%2A> pro načtení vlastního objektu pro procházení konfigurace podtypu projektu, který rozšiřuje objekt procházení Konfigurace základního projektu.

## <a name="see-also"></a>Viz také

- <xref:EnvDTE.IFilterProperties>
- [Dialogové okno stránky vlastností](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))