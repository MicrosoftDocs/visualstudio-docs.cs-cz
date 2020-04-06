---
title: Element commandplacementu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739741"
---
# <a name="commandplacement-element"></a>Element CommandPlacement
Element CommandPlacement umožňuje, aby tlačítka, skupiny a nabídky byly zahrnuty do více než jedné skupiny nebo nabídky. Pomocí CommandPlacement element, není nutné zcela předefinovat tyto položky, aby se změnit vzhled uživatelského rozhraní.

 Další informace naleznete v [tématu Vytvoření opakovaně použitelných skupin tlačítek](../extensibility/creating-reusable-groups-of-buttons.md).

## <a name="syntax"></a>Syntaxe

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID sady příkazů, jak je definován v [symboliku Symboly .](../extensibility/symbols-element.md)|
|id|Povinná hodnota. Id nabídky, skupiny nebo příkazu, který má `Symbols Element`být umístěn, jak je definováno v .|
|Prioritou|Povinná hodnota. Určuje vizuální polohu položky v nadřazeném prvku.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený|Povinná hodnota. Nabídka nebo skupina, která je hostitelem položky, která má být umístěna.|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[Element CommandPlacements](../extensibility/commandplacements-element.md)|Určuje skupiny elementů CommandPlacements a CommandPlacement.|

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
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
