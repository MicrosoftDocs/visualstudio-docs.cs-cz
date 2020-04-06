---
title: Element keybinding | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703148"
---
# <a name="keybinding-element"></a>Element KeyBinding
Element KeyBinding určuje klávesové zkratky pro příkazy.

 Příkazy mohou mít k nim přidružené vazby s jedním i dvěma klíči. Příkladem jedné vazby klíče je **Ctrl**+**S** pro příkaz **Uložit.** Dvouklávesové vazby vyžadují dvě po sobě jdoucí kombinace kláves pro aktivaci příkazu. Příkladem vazby s dvěma klávesami je <strong>Ctrl*+</strong>K<strong>,</strong>Ctrl<strong>+</strong>K**, chcete-li nastavit záložku.

## <a name="syntax"></a>Syntaxe

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota.|
|id|Povinná hodnota.|
|editor|Povinná hodnota. Identifikátor GUID editoru označuje kontext úprav, pro který bude tato klávesová zkratka aktivní. Hodnota oboru globální vazby je "guidVSStd97".|
|key1|Povinná hodnota. Platné hodnoty zahrnují všechny typizovatelné alfanumerické a také dvoumístné šestnáctkové hodnoty, před nimiž je 0x a [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Nepovinný parametr. Libovolná kombinace **kláves Ctrl**, **Alt**a **Shift** oddělených mezerou.|
|key2|Nepovinný parametr. Platné hodnoty zahrnují všechny typizovatelné alfanumerické a také dvoumístné šestnáctkové hodnoty, před nimiž je 0x a [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Nepovinný parametr. Libovolná kombinace **kláves Ctrl**, **Alt**a **Shift** oddělených mezerou.|
|emulátor|Nepovinný parametr.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený||
|Poznámka||

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element KeyBindings](../extensibility/keybindings-element.md)|Seskupí keybinding prvky a další keybindings seskupení.|

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
- [Element KeyBindings](../extensibility/keybindings-element.md)
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
