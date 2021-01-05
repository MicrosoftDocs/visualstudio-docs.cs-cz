---
title: Podmíněné atributy schématu XML VSCT | Microsoft Docs
description: Naučte se, jak použít podmíněné atributy pro VSCT seznamů schémat XML a položek. Atributy se vyhodnotí jako true nebo false a řídí výsledný výstup.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e5f9f51e9380585d4191c5969d96fbb3a93ea42a
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863709"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Podmíněné atributy schématu VSCT XML
U všech seznamů a položek můžete použít podmíněné atributy. Logické operátory a rozšiřovací výrazy se vyhodnotí jako true nebo false. Pokud je nastaveno na true, je přidružený seznam nebo položka součástí výsledného výstupu.

 Můžete testovat rozšíření tokenů s jinými rozšířeními tokenů nebo konstantami. Funkce `Defined()` testuje, zda byl zadán konkrétní název, a to i v případě, že nemá žádnou hodnotu.

 Při použití atributu Condition na seznam se podmínka použije na všechny podřízené prvky v seznamu. Pokud podřízený element sám obsahuje atribut podmínky, pak je jeho podmínka kombinována s nadřazeným výrazem operací a.

 Hodnoty 1, 1 a true se vyhodnotí jako true a 0, 0 a false se vyhodnotí jako false.

## <a name="operators"></a>Operátory
 Pomocí následujících operátorů můžete vyhodnotit podmíněné výrazy.

|Operátor|Definice|
|--------------|----------------|
|(,)|Seskupování|
|!|Logický operátor not|
|\<, >, \<=, >=, ==, !=|Relační a rovnost|
|a|Logická hodnota|
|nebo|Logická hodnota|

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
- [Příkazová tabulka sady Visual Studio (. Soubory vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
