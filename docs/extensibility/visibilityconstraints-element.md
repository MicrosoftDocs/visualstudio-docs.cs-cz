---
title: VisibilityConstraints – | Microsoft Docs
description: Element VisibilityConstraints určuje statickou viditelnost skupin příkazů a panelů nástrojů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 160a3950e31567aafc2d675971fd7263adb2ad5b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905459"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints – element
Element VisibilityConstraints určuje statickou viditelnost skupin příkazů a panelů nástrojů. Viditelnost je nejprve řízena integrovaným [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vývojovém prostředím (IDE) bez načtení balíčku VSPackage.

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
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[VisibilityItem – element](../extensibility/visibilityitem-element.md)|Určuje statickou viditelnost příkazů a panelů nástrojů.|
|[ViditelnostKonstrainty](../extensibility/visibilityconstraints-element.md)|Určuje statickou viditelnost skupin příkazů a panelů nástrojů.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy (například položky nabídky, nabídky, panely nástrojů a pole se seznamem), které balíček VSPackage poskytuje integrovanému vývojovému prostředí (IDE).|

## <a name="example"></a>Příklad

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Viz také
- [VisibilityItem – element](../extensibility/visibilityitem-element.md)
- [Visual Studio příkazové tabulky (. Vsct) – soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
