---
title: Odkaz – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o elementu reference a o tom, jak určuje odkaz na sestavení, který se má přidat při přidání položky do projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fc23edf0897ca71f1b59f126987e42f9d3cb1a8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068515"
---
# <a name="reference-element-visual-studio-templates"></a>Reference – element (šablony sady Visual Studio)
Určuje odkaz na sestavení, který se má přidat při přidání položky do projektu.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>

## <a name="syntax"></a>Syntax

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Sestavení](../extensibility/assembly-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje informace o sestavení, které šablona používá k přidání odkazu na toto sestavení do projektů. `Assembly`V každém elementu musí být jeden element `Reference` .|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Reference](../extensibility/references-element-visual-studio-templates.md)|Seskupí sestavení odkazuje na to, že šablona přičítá k projektům.|

## <a name="remarks"></a>Poznámky
 `Reference` je požadovaný podřízený prvek `References` .

 `Reference`Elementy a `References` lze použít pouze v souborech *. vstemplate* , které mají `Type` hodnotu atributu `Item` .

## <a name="example"></a>Příklad
 Následující příklad ukazuje `TemplateContent` prvek šablony položky. Tento kód XML přidá odkazy na *System.dll* a *System.Data.dll* sestavení.

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
