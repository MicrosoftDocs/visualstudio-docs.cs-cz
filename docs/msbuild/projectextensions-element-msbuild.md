---
title: ProjectExtensions – – element (MSBuild) | Microsoft Docs
description: Přečtěte si o prvku MSBuildProjectExtensions, který umožňuje souborům projektu MSBuild obsahovat informace jiné než MSBuild.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7b186fa1d7a5ecb8297045d4b0bbb111d136d1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905281"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions – – element (MSBuild)

Povoluje souborům projektu MSBuild, aby obsahovaly informace, které nejsou v MSBuild. Nástroj `ProjectExtensions` MSBuild bude ignorovat cokoli uvnitř elementu.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Syntax

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

 Žádné

### <a name="child-elements"></a>Podřízené prvky

 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Požadovaný kořenový element souboru projektu MSBuild. |

## <a name="remarks"></a>Poznámky

 `ProjectExtensions`V projektu MSBuild může být použit pouze jeden element.

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje informace z integrovaného vývojového prostředí, které je uloženo v `ProjectExtensions` prvku.

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
