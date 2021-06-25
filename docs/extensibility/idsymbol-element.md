---
title: IDSymbol – element | Microsoft Docs
description: Element IDSymbol obsahuje ID páru GUID:ID, který představuje nabídku, skupinu nebo příkaz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5158b16fb2d12a7d1a93c0296126e915a138269
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904939"
---
# <a name="idsymbol-element"></a>IDSymbol – element
Element `IDSymbol` obsahuje ID dvojice GUID:ID, která představuje nabídku, skupinu nebo příkaz. Identifikátor GUID pochází z nadřazeného `GuidSymbol` elementu. Element `IDSymbol` má atribut , který poskytuje `name` popisný název ID, který je obsažen v `value` atributu .

## <a name="syntax"></a>Syntax

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|name|Povinná hodnota. Název symbolu ID|
|hodnota|Povinná hodnota. Číselná hodnota ID symbolu ID|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[GuidSymbol – element](../extensibility/guidsymbol-element.md)|Obsahuje identifikátor GUID páru GUID:ID, který představuje nabídku, skupinu nebo příkaz. `IDSymbol`Seskupí prvky.|

## <a name="remarks"></a>Poznámky
 Každý `IDSymbol` prvek v daném prvku musí mít `GuidSymbol` jedinečnou hodnotu `value` . Prvky, které mají identické hodnoty, však mohou v balíčku existovat, pokud `IDSymbol` mají různé podřízené prvky.

## <a name="see-also"></a>Viz také
- [Visual Studio souborů tabulky příkazů (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
