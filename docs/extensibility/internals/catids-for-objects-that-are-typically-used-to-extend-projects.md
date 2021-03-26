---
title: CATID pro objekty, které se obvykle používají pro rozšiřování projektů
description: Seznamte se s CATID pro objekty, které se používají k rozšiřování objektů automatizace projektů a ProjectItem pro projekty Visual Basic, Visual C# a Visual C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 276e7f146858c2de166c0ba20063a0bf4d8b88a0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086089"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATID pro objekty, které se obvykle používají pro rozšiřování projektů
V následující tabulce jsou uvedeny CATID, které se používají k rozšiřování `Project` a `ProjectItem` automatizaci objektů pro [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekty, a [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Tyto CATID jsou definované v *VSLangProj. olb*.

## <a name="listing-of-catids"></a>Výpis CATID

|Name|Identifikátor GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>Visual Basic CATID
 V následující tabulce jsou uvedeny CATID, které se používají k rozšiřování [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] objektů procházení. Jsou definovány v *VSLangProj. olb*.

|Name|Identifikátor GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>Visual C# CATID
 Následující CATID lze použít k rozšiřování [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] objektů procházení. Jsou definovány v *VSLangProj. olb*.

|Name|Identifikátor GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>CATID C++
 Následující [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektový systém CATID nejsou zveřejněny v knihovnách typů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní .NET 2003 a musí být zahrnuty do kódu vždy, když chcete tyto objekty projektu zvětšit. Tyto CATID budou zahrnuty do knihoven typů v pozdějších verzích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Name|Identifikátor GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 Následující příklad kódu ukazuje, jak programovat tyto CATID ve vašem kódu.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Následující [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektové systém CATID nejsou také zveřejněny v knihovnách typů v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní .NET 2003 a musí být zahrnuty do kódu vždy, když chcete tyto objekty projektu zvětšit. Tyto CATID jsou k dispozici pouze v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní .net 2003 a nebudou dostupné v pozdějších verzích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Name|Identifikátor GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 Následující příklad kódu ukazuje, jak programovat tyto CATID v kódu:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Identifikátory GUID pro [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typy projektů a jsou uvedeny v následující tabulce.

| Typ projektu | Identifikátor GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Viz také
- [Přidat šablony projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
