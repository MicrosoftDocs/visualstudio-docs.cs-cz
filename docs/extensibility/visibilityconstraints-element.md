---
title: Element VisibilityConstraints | Microsoft Docs
description: Element VisibilityConstraints určuje statickou viditelnost skupin příkazů a panelů nástrojů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d97f72e7a29f3cbb23c775df8454952f5ffac928
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062561"
---
# <a name="visibilityconstraints-element"></a>Element VisibilityConstraints
Element VisibilityConstraints určuje statickou viditelnost skupin příkazů a panelů nástrojů. Viditelnost je nejprve ovládána [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaným vývojovým prostředím (IDE) bez načtení balíčku VSPackage.

## <a name="syntax"></a>Syntax

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
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
|[Element VisibilityItem](../extensibility/visibilityitem-element.md)|Určuje statickou viditelnost příkazů a panelů nástrojů.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Určuje statickou viditelnost skupin příkazů a panelů nástrojů.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element v příkazu](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy (například položky nabídky, nabídky, panely nástrojů a pole se seznamem), které rozhraní VSPackage poskytuje integrovanému vývojovému prostředí (IDE).|

## <a name="example"></a>Příklad

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Viz také
- [Element VisibilityItem](../extensibility/visibilityitem-element.md)
- [Příkazová tabulka sady Visual Studio (. Soubory vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
