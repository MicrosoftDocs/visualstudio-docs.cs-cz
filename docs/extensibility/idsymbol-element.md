---
title: Element IDSymbol | Microsoft Docs
description: 'Element IDSymbol obsahuje ID páru identifikátorů GUID: ID, který představuje nabídku, skupinu nebo příkaz.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f59089ab981bc97100386b3e1907ef903ede3bd0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069839"
---
# <a name="idsymbol-element"></a>Element IDSymbol
`IDSymbol`Element obsahuje ID páru identifikátorů GUID: ID, který představuje nabídku, skupinu nebo příkaz. Identifikátor GUID pochází z nadřazeného `GuidSymbol` elementu. `IDSymbol`Element má `name` atribut, který poskytuje popisný název pro ID, který je obsažen v `value` atributu.

## <a name="syntax"></a>Syntax

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|name|Povinná hodnota. Název symbolu ID.|
|hodnota|Povinná hodnota. Hodnota číselného ID symbolu ID.|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element GuidSymbol](../extensibility/guidsymbol-element.md)|Obsahuje identifikátor GUID páru identifikátorů GUID: ID, který představuje nabídku, skupinu nebo příkaz. Seskupuje `IDSymbol` prvky.|

## <a name="remarks"></a>Poznámky
 Každý `IDSymbol` prvek v daném `GuidSymbol` elementu musí mít jedinečný `value` . Nicméně `IDSymbol` prvky, které mají stejné hodnoty, mohou existovat v balíčku, pokud mají různé nadřazené položky.

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
