---
title: Element CommandPlacements | Microsoft Docs
description: Element CommandPlacements seskupuje elementy CommandPlacement a další seskupení CommandPlacements. Element CommandPlacements je nepovinný.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c43f2063062d96b8ab635e3d9786aead4b4c150
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889041"
---
# <a name="commandplacements-element"></a>Element CommandPlacements
Element CommandPlacements seskupuje elementy CommandPlacement a další seskupení CommandPlacements.

 Element CommandPlacements je nepovinný. Pokud žádné příkazy, skupiny nebo nabídky nesmí být zahrnuté do sekundárního umístění, nemusíte tento oddíl zahrnout do souboru *. vsct* .

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
|Podmínka|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|CommandPlacements|Seskupí prvky CommandPlacement a další skupiny CommandPlacements.|
|[Element CommandPlacement](../extensibility/commandplacement-element.md)|Povoluje zahrnutí tlačítek, skupin a nabídek do více než jedné skupiny nebo nabídky.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element v příkazu](../extensibility/commandtable-element.md)|Definuje všechny prvky, které reprezentují příkazy.|

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
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
