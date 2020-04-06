---
title: Referenční prvek (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701628"
---
# <a name="reference-element-visual-studio-templates"></a>Referenční prvek (šablony sady Visual Studio)
Určuje odkaz na sestavení, který má být přidán při přidání položky do projektu.

 \<VSTemplate \<> TemplateContent \<> \<odkazy> referenční>

## <a name="syntax"></a>Syntaxe

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Sestavení](../extensibility/assembly-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje informace o sestavení, které šablona používá k přidání odkazu na toto sestavení do projektů. V každém `Reference` `Assembly` prvku musí být jeden prvek.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Odkazy](../extensibility/references-element-visual-studio-templates.md)|Seskupí odkazy na sestavení, které šablona přidá k projektům.|

## <a name="remarks"></a>Poznámky
 `Reference`je povinnýpodřízený `References`prvek .

 `Reference` Prvky `References` a lze použít pouze v souborech `Type` *.vstemplate,* které mají hodnotu atributu `Item`.

## <a name="example"></a>Příklad
 Následující příklad ilustruje `TemplateContent` prvek šablony položky. Tento jazyk XML přidává odkazy na sestavení *System.dll* a *System.Data.dll.*

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
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
