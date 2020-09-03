---
title: Element GuidSymbol | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711131"
---
# <a name="guidsymbol-element"></a>Element GuidSymbol
`GuidSymbol`Element obsahuje identifikátor GUID páru identifikátorů GUID: ID, který představuje nabídku, skupinu nebo příkaz. ID pochází z `IDSymbol` prvku v `GuidSymbol` elementu. `GuidSymbol`Element má `name` atribut, který poskytuje popisný název identifikátoru GUID, který je obsažen v `value` atributu.

## <a name="syntax"></a>Syntax

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|name|Povinná hodnota. Název symbolu GUID|
|value|Povinná hodnota. Identifikátor GUID symbolu GUID|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Element IDSymbol](../extensibility/idsymbol-element.md)|Obsahuje ID páru identifikátorů GUID: ID, který představuje nabídku, skupinu nebo příkaz.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[SYMBOLS – element](../extensibility/symbols-element.md)|Seskupí `GuidSymbol` elementy v souboru *. vsct* .|

## <a name="remarks"></a>Poznámky
 Soubor *. vsct* obvykle obsahuje tři `GuidSymbol` prvky v jeho `Symbols` části, jednu pro samotný balíček, jednu pro sadu příkazů (kolekci nabídek, skupin a příkazů, které balíček zpřístupňuje), a jeden pro rastrové obrázky, které poskytují ikony pro tlačítka a další vizuální komponenty. Každý `IDSymbol` prvek v daném `GuidSymbol` elementu musí mít jedinečný `value` . Nicméně `IDSymbol` prvky, které mají stejné hodnoty, mohou existovat v balíčku, pokud mají různé nadřazené položky.

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
