---
title: Prvek Sdk (MSBuild) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 8a704744032c5dea70246463a816ba8e1f5c84e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632469"
---
# <a name="sdk-element-msbuild"></a>Prvek Sdk (MSBuild)

Odkazuje na sadu SDK projektu MSBuild.

 \<Projekt \<> Sdk>

## <a name="syntax"></a>Syntaxe

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Požadovaný atribut.<br /><br /> Název projektu SDK.|
|`Version`|Nepovinný atribut.<br /><br /> Verze projektu SDK|

### <a name="child-elements"></a>Podřízené prvky

 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Požadovaný kořenový prvek souboru projektu MSBuild. |

## <a name="see-also"></a>Viz také

- [Postup: Odkaz na sadu SDK projektu MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Msbuild](../msbuild/msbuild.md)
