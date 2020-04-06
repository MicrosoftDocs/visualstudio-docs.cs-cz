---
title: Element sestavení (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740042"
---
# <a name="assembly-element-visual-studio-templates"></a>Element sestavení (šablony sady Visual Studio)
Určuje informace o sestavení, které šablona používá k přidání odkazu na toto sestavení do projektů.

 \<VSTemplate \<> TemplateContent \<> \<odkazy \<> reference>> sestavení

## <a name="syntax"></a>Syntaxe

```
<Assembly> AssemblyName </Assembly>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Referenční informace](../extensibility/reference-element-visual-studio-templates.md)|Určuje odkaz na sestavení, který má být přidán při přidání položky do projektu.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Tento text určuje sestavení, které má být při vytváření instancí vytvořena šablona položky. Tento název sestavení musí být zadán jedním z následujících způsobů:

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
 `Assembly`je povinnýpodřízený `Reference`prvek .

 `Reference`Prvky `References,` `Assembly` , a lze použít pouze v souborech `Type` *.vstemplate,* které mají hodnotu atributu `Item`.

## <a name="example"></a>Příklad
 Následující příklad ilustruje `TemplateContent` prvek šablony položky. Tento jazyk XML přidává odkazy na sestavení *System.dll* a *System.Data.dll.*

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
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
