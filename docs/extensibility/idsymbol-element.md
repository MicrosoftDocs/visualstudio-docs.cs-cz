---
title: Prvek IDSymbol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710378"
---
# <a name="idsymbol-element"></a>Prvek IDSymbol
Prvek `IDSymbol` obsahuje ID dvojice GUID:ID, která představuje nabídku, skupinu nebo příkaz. Identifikátor GUID pochází `GuidSymbol` z nadřazeného prvku. Prvek `IDSymbol` má `name` atribut, který poskytuje popisný název pro ID, `value` který je obsažen v atributu.

## <a name="syntax"></a>Syntaxe

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|jméno|Povinná hodnota. Název symbolu ID.|
|value|Povinná hodnota. Číselná hodnota ID symbolu ID.|

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element GuidSymbol](../extensibility/guidsymbol-element.md)|Obsahuje identifikátor GUID dvojice GUID:ID, která představuje nabídku, skupinu nebo příkaz. Seskupí `IDSymbol` prvky.|

## <a name="remarks"></a>Poznámky
 Každý `IDSymbol` prvek v `GuidSymbol` daném prvku `value`musí mít jedinečný . Prvky, které mají stejné hodnoty však mohou existovat v balíčku tak dlouho, `IDSymbol` dokud mají různé rodiče.

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
