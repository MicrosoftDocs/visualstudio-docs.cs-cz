---
title: Assembly – element (šablony sady Visual Studio) | Microsoft Docs
titleSuffix: ''
description: Přečtěte si o elementu sestavení a o tom, jak určuje informace o sestavení, které šablona používá k přidání odkazu na toto sestavení do projektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4115e999cc061be53ba437a090f207046f71ef8
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671643"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly – element (šablony sady Visual Studio)
Určuje informace o sestavení, které šablona používá k přidání odkazu na toto sestavení do projektů.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>
 \<Assembly>

## <a name="syntax"></a>Syntax

```
<Assembly> AssemblyName </Assembly>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Odkaz](../extensibility/reference-element-visual-studio-templates.md)|Určuje odkaz na sestavení, který se má přidat při přidání položky do projektu.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Tento text určuje sestavení, které se má přidat do projektu při vytvoření instance šablony položky. Tento název sestavení musí být zadán v jednom z následujících způsobů:

- Jako úplný název sestavení. Například:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Jako jednoduchý textový odkaz. Například:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Poznámky
 `Assembly` je požadovaný podřízený prvek `Reference` .

 `Reference` `References,` `Assembly` Elementy a lze použít pouze v souborech *. vstemplate* , které mají `Type` hodnotu atributu `Item` .

## <a name="example"></a>Příklad
 Následující příklad ukazuje `TemplateContent` prvek šablony položky. Tento kód XML přidá odkazy na *System.dll* a *System.Data.dll* sestavení.

```
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
