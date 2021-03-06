---
title: Nadřazený element | Microsoft Docs
description: Nadřazený prvek určuje, že element je nadřazený pro tlačítko, pole se seznamem, nabídku nebo skupinu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3dbf7202ac7fb94762ea132a2620625fae97ddfb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901549"
---
# <a name="parent-element"></a>Nadřazený element
Nadřazený prvek tlačítka nebo pole se seznamem může být pouze skupina. Nadřazeným objektem nabídky nebo skupiny může být jakákoli jiná nabídka nebo skupina. V [elementu CommandPlacement](../extensibility/commandplacement-element.md)je tento element povinný; ve všech ostatních případech je volitelná. Pokud je tento prvek vynechán, bude odvozen nadřazený objekt `Group_Undefined:0` .

## <a name="syntax"></a>Syntax

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID|

### <a name="child-elements"></a>Podřízené prvky
 Žádná

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element v příkazu](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy, které VSPackage poskytuje integrovanému vývojovému prostředí (IDE). Například položky nabídky, nabídky, panely nástrojů a pole se seznamem.|
|[Buttons – Element](../extensibility/buttons-element.md)|Prvky [prvku tlačítka](../extensibility/button-element.md) skupiny.|
|[Menu – element](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje VSPackage.|
|[Groups – element](../extensibility/groups-element.md)|Obsahuje položky, které definují skupiny příkazů VSPackage.|

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
