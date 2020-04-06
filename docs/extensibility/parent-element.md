---
title: Nadřazený prvek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702215"
---
# <a name="parent-element"></a>Nadřazený prvek
Nadřazený tlačítka nebo pole se seznamem může být pouze skupina. Nadřazenou položkou nabídky nebo skupiny může být jakákoli jiná nabídka nebo skupina. V [Element CommandPlacement](../extensibility/commandplacement-element.md), tento prvek je povinný; ve všech ostatních případech je nepovinný. Pokud je tento prvek vynechán, `Group_Undefined:0` bude mít nadřazený prvek implicitní.

## <a name="syntax"></a>Syntaxe

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|

### <a name="child-elements"></a>Podřízené prvky
 Žádný

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy, které Poskytuje VSPackage integrované vývojové prostředí (IDE). Například položky nabídky, nabídky, panely nástrojů a pole se seznamem.|
|[Prvek tlačítek](../extensibility/buttons-element.md)|Skupiny [Button element](../extensibility/button-element.md) elementu.|
|[Prvek nabídek](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje VSPackage.|
|[Prvek Skupiny](../extensibility/groups-element.md)|Obsahuje položky, které definují skupiny příkazů VSPackage.|

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
