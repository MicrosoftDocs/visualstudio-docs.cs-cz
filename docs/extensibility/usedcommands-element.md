---
title: Element UsedCommands | Microsoft Docs
description: Element UsedCommands seskupuje elementy UsedCommand a další seskupení UsedCommands. Element UsedCommands je nepovinný.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89ecd1d0f7697a38ef7318ddf93a91a4397b5d72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934061"
---
# <a name="usedcommands-element"></a>UsedCommands – element
Element UsedCommands seskupuje elementy UsedCommand a další seskupení UsedCommands.

 Element UsedCommands je nepovinný. Pokud nevoláte příkazy definované mimo váš balíček, nemusíte tento oddíl zahrnout do souboru. vsct.

## <a name="syntax"></a>Syntax

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Podmínka|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|[UsedCommand – element](../extensibility/usedcommand-element.md)|Příkaz, který je implementován jiným kódem.|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy (například položky nabídky, nabídky, panely nástrojů a pole se seznamem), které rozhraní VSPackage poskytuje integrovanému vývojovému prostředí (IDE).|

## <a name="example"></a>Příklad

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Viz také
- [UsedCommand – element](../extensibility/usedcommand-element.md)
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
