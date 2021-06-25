---
title: Define – | Microsoft Docs
description: Element Define definuje název symbolu a pár hodnot. Tento symbol lze vyhodnotit pomocí podmíněných atributů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 409621410db727f933e41bae894f125dc877b4c2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898042"
---
# <a name="define-element"></a>Define – element
Definuje název symbolu a pár hodnot. Tento symbol lze vyhodnotit pomocí podmíněných atributů. Další informace najdete v tématu [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md). Viz také [element Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Syntax

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|name|Povinná hodnota. Název symbolu:<br /><br /> name="Mode"|
|hodnota|Povinná hodnota. Hodnota symbolu:<br /><br /> value="Standard"|
|Podmínka|Nepovinný parametr. Další informace najdete v tématu [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy, které balíček VSPackage poskytuje integrovanému vývojovému prostředí (IDE). Například položky nabídky, nabídky, panely nástrojů a pole se seznamem.|

## <a name="example"></a>Příklad

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Viz také
- [Visual Studio souborů tabulky příkazů (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
