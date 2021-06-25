---
title: Podmíněné atributy schématu XML VSCT | Microsoft Docs
description: Zjistěte, jak použít podmíněné atributy na seznamy a položky schématu XML VSCT. Atributy se vyhodnotí jako true nebo false a řídí výsledný výstup.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e91207016ed6e1baab80b323680d10a40e0331d8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905251"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Podmíněné atributy schématu XML VSCT
Podmíněné atributy můžete použít u všech seznamů a položek. Logické operátory a výrazy rozšíření symbolů se vyhodnotí jako true nebo false. Pokud je true, přidružený seznam nebo položka je součástí výsledného výstupu.

 Rozšíření tokenu můžete testovat proti ostatním rozšířením tokenů nebo konstantám. Funkce `Defined()` testuje, zda byl definován konkrétní název, i když nemá žádnou hodnotu.

 Když se na seznam použije atribut Podmínky, podmínka se použije na každý podřízený prvek v seznamu. Pokud samotný podřízený prvek obsahuje atribut Condition, zkombinuje se jeho podmínka s nadřazeným výrazem pomocí operace AND.

 Hodnoty 1, 1 a true se vyhodnotí jako true a 0, 0 a false se vyhodnotí jako false.

## <a name="operators"></a>Operátory
 K vyhodnocení podmíněných výrazů použijte následující operátory.

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
- [Visual Studio příkazové tabulky (. Vsct) – soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
