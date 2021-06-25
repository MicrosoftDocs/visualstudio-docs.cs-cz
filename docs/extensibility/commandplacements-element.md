---
title: CommandPlacements – | Microsoft Docs
description: Element CommandPlacements seskupuje elementy CommandPlacement a další seskupení CommandPlacements. Element CommandPlacements je volitelný.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21e0feb3913b148b4320e69461bc5035655a392d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901887"
---
# <a name="commandplacements-element"></a>CommandPlacements – element
Element CommandPlacements seskupuje elementy CommandPlacement a další seskupení CommandPlacements.

 Element CommandPlacements je volitelný. Pokud sekundární umístění nesmí obsahovat žádné příkazy, skupiny ani nabídky, není nutné zahrnout tuto část do souboru *.vsct.*

## <a name="syntax"></a>Syntax

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|CommandPlacements|Seskupuje prvky CommandPlacement a další seskupení CommandPlacements.|
|[CommandPlacement – element](../extensibility/commandplacement-element.md)|Umožňuje zahrnout tlačítka, skupiny a nabídky do více skupin nebo nabídek.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy.|

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
- [CommandPlacement – element](../extensibility/commandplacement-element.md)
- [Visual Studio souborů tabulky příkazů (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
