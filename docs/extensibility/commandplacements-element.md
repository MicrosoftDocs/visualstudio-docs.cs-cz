---
title: CommandPlacements Element | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72b087652a654b563fd4e00bacc52290a29fe1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739697"
---
# <a name="commandplacements-element"></a>Element CommandPlacements
Element CommandPlacements seskupuje elementy CommandPlacement a další seskupení CommandPlacements.

 Element CommandPlacements je volitelný. Pokud v sekundárním umístění nemusí být zahrnuty žádné příkazy, skupiny nebo nabídky, není nutné tento oddíl zahrnout do souboru *.vsct.*

## <a name="syntax"></a>Syntaxe

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Příkazy|Seskupí elementy CommandPlacement a další seskupení CommandPlacements.|
|[Element CommandPlacement](../extensibility/commandplacement-element.md)|Umožňuje zahrnutí tlačítek, skupin a nabídek do více než jedné skupiny nebo nabídky.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy.|

## <a name="example"></a>Příklad

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Viz také
- [Element CommandPlacement](../extensibility/commandplacement-element.md)
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
