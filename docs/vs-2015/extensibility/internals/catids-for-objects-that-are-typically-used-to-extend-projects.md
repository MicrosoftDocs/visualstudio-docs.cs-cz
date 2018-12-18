---
title: Identifikátory CatID pro objekty, které se obvykle používají k rozšíření projektů | Dokumentace Microsoftu
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
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57af657c888963dc9f33fc729678c0d8c82e0f0a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798505"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>Identifikátory CATID pro objekty používané obvykle k rozšíření projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující tabulka uvádí identifikátory CatID, které se používají k rozšíření `Project` a `ProjectItem` objekty automatizace pro [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], a [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projekty. Tyto identifikátory CatID jsou definovány v VSLangProj.olb.  
  
## <a name="listing-of-catids"></a>Seznam identifikátory CatID  
  
|Název|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|  
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|  
  
## <a name="visual-basic-catids"></a>Identifikátory CatID jazyka Visual Basic  
 Následující tabulka uvádí identifikátory CatID, které se používají k rozšíření [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] procházet objekty. Všechny jsou definovány v VSLangProj.olb.  
  
|Název|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|  
  
## <a name="visual-c-catids"></a>Identifikátory CatID Visual C#  
 Následující identifikátory CatID je možné rozšířit [!INCLUDE[csprcs](../../includes/csprcs-md.md)] procházet objekty. Všechny jsou definovány v VSLangProj.olb.  
  
|Název|GUID|  
|----------|----------|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|  
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|  
  
## <a name="c-catids"></a>Identifikátory CatID C++  
 Následující [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] systému identifikátory CatID nejsou zveřejněné v knihovnách typů v projektu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET 2003 a mají být zahrnuty ve vašem kódu pokaždé, když chcete rozšířit tyto objekty projektu. Do knihovny typů v pozdějších verzích se zahrnou tyto identifikátory CatID [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Název|GUID|  
|----------|----------|  
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
  
 Následující příklad kódu ukazuje, jak program tyto identifikátory CatID ve vašem kódu.  
  
```  
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Následující [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] systému identifikátory CatID nezveřejňují také v knihovnách typů v projektu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET 2003 a mají být zahrnuty ve vašem kódu pokaždé, když chcete rozšířit tyto objekty projektu. Tyto identifikátory CatID jsou k dispozici pouze v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET 2003 a nebude k dispozici v pozdějších verzích [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Název|GUID|  
|----------|----------|  
|`CVCAssemblyReferenceNode` **:**|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|  
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|  
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|  
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|  
  
 Následující příklad kódu ukazuje, jak program tyto identifikátory CatID ve vašem kódu:  
  
```  
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";  
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";  
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";  
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";  
```  
  
 Identifikátory GUID pro [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] v následující tabulce jsou uvedeny typy projektů.  
  
|Typ projektu|GUID|  
|------------------|----------|  
|[!INCLUDE[csprcs](../../includes/csprcs-md.md)]|{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}|  
|[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]|{F184B08F-C81C-45F6-A57F-5ABD9991F28F}|  
  
## <a name="see-also"></a>Viz také  
 [Přidání projektu a šablony položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)

