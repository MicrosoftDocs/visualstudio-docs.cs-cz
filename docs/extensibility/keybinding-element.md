---
title: Element vazby elementu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703148"
---
# <a name="keybinding-element"></a>Element Binding elementu
Element vazby klíčů určuje klávesové zkratky pro příkazy.

 K příkazům můžou být přidruženy obě vazby Single i Dual Key. Příkladem vazby s jedním klíčem je **CTRL** + **S** pro příkaz **Save** . Pro aktivaci příkazu vyžadují vazby Dual Key dvě následující kombinace kláves. Příkladem vazby s duálním klíčem je <strong>CTRL *+</strong> k<strong>,</strong>CTRL <strong>+</strong> k** pro nastavení záložky.

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
|mod1|Nepovinný parametr. Libovolná kombinace **CTRL**, **ALT**a **SHIFT** oddělené mezerou.|
|key2|Nepovinný parametr. Platné hodnoty zahrnují všechny alfanumerické znaky typable a také dvoumístné hexadecimální hodnoty předcházejí 0x a [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Nepovinný parametr. Libovolná kombinace **CTRL**, **ALT**a **SHIFT** oddělené mezerou.|
|emulátor|Nepovinný parametr.|
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

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
