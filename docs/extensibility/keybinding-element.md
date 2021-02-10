---
title: Element vazby elementu | Microsoft Docs
description: Element vazby klíčů určuje klávesové zkratky pro příkazy. K příkazům můžou být přidruženy obě vazby Single i Dual Key.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ce96da36a8c6eff0fda71d8a5d077721876ab8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943345"
---
# <a name="keybinding-element"></a>Element Binding elementu
Element vazby klíčů určuje klávesové zkratky pro příkazy.

 K příkazům můžou být přidruženy obě vazby Single i Dual Key. Příkladem vazby s jedním klíčem je **CTRL** + **S** pro příkaz **Save** . Pro aktivaci příkazu vyžadují vazby Dual Key dvě následující kombinace kláves. Příkladem vazby s duálním klíčem je <strong>CTRL *+</strong> k <strong>,</strong>CTRL <strong>+</strong> k** pro nastavení záložky.

## <a name="syntax"></a>Syntax

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota.|
|id|Povinná hodnota.|
|editor|Povinná hodnota. Identifikátor GUID editoru určuje kontext úprav, pro který bude tato klávesová zkratka aktivní. Hodnota oboru globálních vazeb je "guidVSStd97".|
|key1|Povinná hodnota. Platné hodnoty zahrnují všechny alfanumerické znaky typable a také dvoumístné hexadecimální hodnoty předcházejí 0x a [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Nepovinný parametr. Libovolná kombinace **CTRL**, **ALT** a **SHIFT** oddělené mezerou.|
|key2|Nepovinný parametr. Platné hodnoty zahrnují všechny alfanumerické znaky typable a také dvoumístné hexadecimální hodnoty předcházejí 0x a [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Nepovinný parametr. Libovolná kombinace **CTRL**, **ALT** a **SHIFT** oddělené mezerou.|
|emulátor|Nepovinný parametr.|
|Podmínka|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený||
|Poznámka||

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element Bindings elementu](../extensibility/keybindings-element.md)|Seskupuje prvky vazby klíčů a další seskupení klíčů.|

## <a name="example"></a>Příklad

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Viz také
- [Element Bindings elementu](../extensibility/keybindings-element.md)
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
