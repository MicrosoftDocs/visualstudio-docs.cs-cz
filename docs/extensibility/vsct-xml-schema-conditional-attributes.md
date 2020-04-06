---
title: Podmíněné atributy schématu XML VSCT | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697950"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Podmíněné atributy schématu XML VSCT
Podmíněné atributy můžete použít na všechny seznamy a položky. Logické operátory a výrazy rozšíření symbolu jsou vyhodnoceny jako pravdivé nebo nepravdivé. Pokud true, přidružený seznam nebo položka je zahrnuta ve výsledném výstupu.

 Můžete otestovat rozšíření tokenu proti jiné rozšíření tokenu nebo konstanty. Funkce `Defined()` testuje, zda byl definován určitý název, i když nemá žádnou hodnotu.

 Pokud je atribut Condition použit na seznam, podmínka je použita pro každý podřízený prvek v seznamu. Pokud podřízený prvek sám obsahuje Condition atribut, pak jeho podmínka je kombinován s nadřazený výraz and operace.

 Hodnoty 1, "1" a "true" jsou vyhodnoceny jako pravdivé a 0, '0' a 'false' jsou vyhodnoceny jako false.

## <a name="operators"></a>Operátory
 K vyhodnocení podmíněných výrazů použijte následující operátory.

|Operátor|Definice|
|--------------|----------------|
|(,)|Seskupování|
|!|Logický operátor not|
|\<, >, \<=, >=, ==, !=|Relační a rovnost|
|a|Logická hodnota|
|– nebo –|Logická hodnota|

## <a name="examples"></a>Příklady

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>Viz také
- [Visual Studio příkaz tabulky (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
