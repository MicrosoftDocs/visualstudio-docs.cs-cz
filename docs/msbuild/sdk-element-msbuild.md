---
title: Element sady SDK (MSBuild) | Microsoft Docs
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c65bafd9183c97efa7595c10d7bdb3641c5f75f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595134"
---
# <a name="sdk-element-msbuild"></a>Element sady SDK (MSBuild)
Odkazuje na sadu SDK [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu.

 \<Project > \<SDK >

## <a name="syntax"></a>Syntaxe

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Požadovaný atribut.<br /><br /> Název sady SDK projektu.|
|`Version`|Nepovinný atribut.<br /><br /> Verze sady SDK projektu|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="see-also"></a>Viz také:
- [Postupy: odkazování na sadu SDK projektu MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
