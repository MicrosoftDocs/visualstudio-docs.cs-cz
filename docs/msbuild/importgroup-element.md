---
title: Import elementu | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4480442577ccb321d66ad65f94a7c86cdae62ae
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574003"
---
# <a name="importgroup-element"></a>Import – element
Obsahuje kolekci `Import` prvků, které jsou seskupeny pod volitelnou podmínkou. Další informace naleznete v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

 \<Project> \<ImportGroup>

## <a name="syntax"></a>Syntaxe

```xml
<ImportGroup Condition="'String A' == 'String B'">
    <Import ... />
    <Import ... />
</ImportGroup>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Import](../msbuild/import-element-msbuild.md)|Importuje obsah jednoho souboru projektu do jiného souboru projektu.|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje prvek `ImportGroup`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ImportGroup>
        <Import Project="$(Targets1.targets)" />
        <Import Project="$(Targets2.targets)" />
    </ImportGroup>
...
</Project>
```

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Položky](../msbuild/msbuild-items.md)
