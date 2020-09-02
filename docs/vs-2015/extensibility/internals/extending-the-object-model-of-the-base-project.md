---
title: Rozšíření objektového modelu základního projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187167"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Rozšíření objektového modelu základního projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projektu může v následujících umístěních zvětšit objektový model automatizace základního projektu:  
  
- Project. Extender (" \<ProjectSubtypeName> ") – to umožňuje podtypům projektu nabízet objekt s vlastními metodami z <xref:EnvDTE.Project> . Podtyp projektu může použít rozšířené automatizaci k vystavení `Project` objektu. <xref:EnvDTE80.IInternalExtenderProvider>Rozhraní implementované v Agregátoru podtypu hlavního projektu by mělo nabízet svůj objekt pro `VSHPROPID_ExtObjectCATID` od <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (odpovídající `itemid` hodnotě VSITEMID_ROOT, od `VSITEMID` ) CATID.  
  
- ProjectItem. Extender (" \<ProjectSubtypeName> ") – to umožňuje podtypům projektu nabízet objekt s vlastními metodami z konkrétního <xref:EnvDTE.ProjectItem> objektu v rámci projektu. Podtyp projektu může použít rozšířené automatizaci k vystavení tohoto objektu. <xref:EnvDTE80.IInternalExtenderProvider>Rozhraní implementované v hlavním Agregátoru podtypu projektu musí nabízet svůj objekt pro `VSHPROPID_ExtObjectCATID` od <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpovídající požadovanému `VSITEMID` ) CATID.  
  
- Project. Properties – Tato kolekce zpřístupňuje vlastnosti nezávislé na konfiguraci `Project` objektu. Další informace o vlastnostech projektu naleznete v tématu <xref:EnvDTE.Project.Properties%2A> . Podtyp projektu může pomocí zařízení pro automatizaci automatizace přidat své vlastnosti do této kolekce. <xref:EnvDTE80.IInternalExtenderProvider>Rozhraní implementované v hlavním Agregátoru podtypu projektu musí nabízet svůj objekt pro `VSHPROPID_BrowseObjectCATID` VSHPROPID2 (odpovídající `itemid` hodnotě VSITEMID_ROOT, od <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ) CATID.  
  
- Configuration. Properties – Tato kolekce zpřístupňuje vlastnosti závislé na konfiguraci projektu pro konkrétní konfiguraci (například ladění). Další informace najdete v tématu <xref:EnvDTE.Configuration>. Podtyp projektu může pomocí zařízení pro automatizaci automatizace přidat své vlastnosti do této kolekce. <xref:EnvDTE80.IInternalExtenderProvider>Rozhraní implementované v Agregátoru podtypu hlavní projekt nabízí svůj objekt pro CATID `VSHPROPID_CfgBrowseObjectCATID` (odpovídající `itemid` hodnotě <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Rozhraní se používá k rozlišení jednoho objektu pro procházení konfigurace od druhého.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
