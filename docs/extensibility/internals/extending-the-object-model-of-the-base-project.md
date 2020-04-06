---
title: Rozšíření objektového modelu základního projektu | Dokumenty společnosti Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708399"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Rozšíření objektového modelu základního projektu

Podtyp projektu může rozšířit objektový model automatizace základního projektu na následující místa:

- Project.Extender("\<ProjectSubtypeName>"): To umožňuje podtypu projektu nabídnout objekt <xref:EnvDTE.Project> s vlastními metodami z objektu. Podtyp projektu můžete použít automation extendery vystavit objekt. `Project` Rozhraní <xref:EnvDTE80.IInternalExtenderProvider> implementované na hlavním projektu podtyp agregátor by `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> měl nabídnout `itemid` svůj objekt pro od (odpovídající hodnotě [VSITEMID. Kořen](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): To umožňuje podtypu projektu nabídnout objekt <xref:EnvDTE.ProjectItem> s vlastními metodami z určitého objektu v rámci projektu. Podtyp projektu můžete použít automatizace extendery vystavit tento objekt. Rozhraní <xref:EnvDTE80.IInternalExtenderProvider> implementované na hlavním projektu podtyp agregátor musí `VSHPROPID_ExtObjectCATID` nabídnout <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> svůj objekt <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>pro od (odpovídající požadované ) CATID.

- Project.Properties: Tato kolekce zpřístupňuje vlastnosti `Project` objektu nezávislé na konfiguraci. Další informace `Project` o vlastnostech naleznete v tématu <xref:EnvDTE.Project.Properties%2A>. Podtyp projektu můžete použít automation extendery přidat své vlastnosti do této kolekce. Rozhraní <xref:EnvDTE80.IInternalExtenderProvider> implementované na hlavním projektu podtyp agregátor musí `VSHPROPID_BrowseObjectCATID` nabídnout <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> svůj objekt `itemid` pro od (odpovídající hodnotě [VSITEMID. Kořen](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Tato kolekce zpřístupňuje vlastnosti projektu závislé na konfiguraci pro určitou konfiguraci (například ladění). Další informace naleznete v tématu <xref:EnvDTE.Configuration>. Podtyp projektu můžete použít automation extendery přidat své vlastnosti do této kolekce. Rozhraní <xref:EnvDTE80.IInternalExtenderProvider> implementované na hlavním agregátoru podtypu projektu nabízí `VSHPROPID_CfgBrowseObjectCATID` svůj objekt `itemid` pro CATID (odpovídající hodnotě [VSITEMID. Kořen](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> se používá k rozlišení jednoho objektu procházení konfigurace od jiného.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
