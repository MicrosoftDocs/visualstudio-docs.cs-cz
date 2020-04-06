---
title: Prvek guidsymbol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711131"
---
# <a name="guidsymbol-element"></a>Element GuidSymbol
Prvek `GuidSymbol` obsahuje identifikátor GUID dvojice GUID:ID, která představuje nabídku, skupinu nebo příkaz. ID pochází z `IDSymbol` prvku `GuidSymbol` v prvku. Prvek `GuidSymbol` má `name` atribut, který poskytuje popisný název identifikátoru GUID, který je obsažen v atributu. `value`

## <a name="syntax"></a>Syntaxe

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|jméno|Povinná hodnota. Název symbolu GUID.|
|value|Povinná hodnota. IDENTIFIKÁTOR GUID symbolu GUID.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Prvek IDSymbol](../extensibility/idsymbol-element.md)|Obsahuje ID dvojice GUID:ID, která představuje nabídku, skupinu nebo příkaz.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Prvek symbolů](../extensibility/symbols-element.md)|Seskupí `GuidSymbol` prvky v souboru *.vsct.*|

## <a name="remarks"></a>Poznámky
 Soubor *.vsct* obvykle obsahuje `GuidSymbol` tři prvky ve své `Symbols` části, jeden pro samotný balíček, jeden pro sadu příkazů (kolekce nabídek, skupin a příkazů, které balíček zpřístupňuje) a jeden pro bitmapy, které poskytují ikony pro tlačítka a další vizuální součásti. Každý `IDSymbol` prvek v `GuidSymbol` daném prvku `value`musí mít jedinečný . Prvky, které mají stejné hodnoty však mohou existovat v balíčku tak dlouho, `IDSymbol` dokud mají různé rodiče.

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
