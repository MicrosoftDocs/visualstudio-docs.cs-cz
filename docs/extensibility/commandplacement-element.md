---
title: Element CommandPlacement | Microsoft Docs
description: Element CommandPlacement umožňuje zahrnutí tlačítek, skupin a nabídek do více než jedné skupiny nebo nabídky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73d97e32314de0b01bf26025c1fee412de7d9795
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089612"
---
# <a name="commandplacement-element"></a>Element CommandPlacement
Element CommandPlacement umožňuje zahrnutí tlačítek, skupin a nabídek do více než jedné skupiny nebo nabídky. Pomocí elementu CommandPlacement není nutné zcela předefinovat tyto položky, aby bylo možné změnit vzhled uživatelského rozhraní.

 Další informace najdete v tématu [vytvoření opakovaně použitelných skupin tlačítek](../extensibility/creating-reusable-groups-of-buttons.md).

## <a name="syntax"></a>Syntax

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID sady příkazů, jak je definováno v [elementu Symbols](../extensibility/symbols-element.md).|
|id|Povinná hodnota. ID nabídky, skupiny nebo příkazu, který se má umístit, jak je definováno v `Symbols Element` .|
|upřednostněn|Povinná hodnota. Určuje vizuální pozici položky v jejím nadřazeném prvku.|
|Podmínka|Nepovinný parametr. Viz [podmíněný Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený|Povinná hodnota. Nabídka nebo skupina, která hostuje položku, která se má umístit|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[Element CommandPlacements](../extensibility/commandplacements-element.md)|Určuje skupiny prvků CommandPlacements a CommandPlacement.|

## <a name="example"></a>Příklad

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Viz také
- [Element CommandPlacements](../extensibility/commandplacements-element.md)
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
