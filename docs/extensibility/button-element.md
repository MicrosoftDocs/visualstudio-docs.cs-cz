---
title: Element Button | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739937"
---
# <a name="button-element"></a>Element Button
Definuje prvek, se kterým může uživatel pracovat. Tlačítka mohou mít různé druhy: Button, MenuButton a SplitDropDown.

## <a name="syntax"></a>Syntax

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID|
|upřednostněn|Nepovinný parametr. Číselná hodnota, která určuje prioritu.|
|typ|Nepovinný parametr. Hodnota výčtu, která určuje druh tlačítka.<br /><br /> Pokud není zadaný, použije se tlačítko.<br /><br /> Tlačítko<br /> Standardní příkaz, který se zobrazí na panelech nástrojů (obvykle jako tlačítko ikonickým), v nabídkách a místních nabídkách.<br /><br /> MenuButton<br /> Položka nabídky, která nespustí příkaz, ale vytvoří jinou nabídku.<br /><br /> SplitDropDown<br /> Ovládací prvky, jako jsou tlačítka zpět a znovu na standardním panelu nástrojů v aplikaci Microsoft Word.|
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|[Nadřazený element](../extensibility/parent-element.md)|Nepovinný parametr. Nadřazený element tlačítka|
|[Element Icon](../extensibility/icon-element.md)|Nepovinný parametr. Ikona přidružená k tlačítku|
|[Element příznak příkazu](../extensibility/command-flag-element.md)|Povinná hodnota. Platné hodnoty CommandFlag pro tlačítko jsou následující.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> -Upravit<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> – PICT<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> -TextOnly|
|[Řetězec – element](../extensibility/strings-element.md)|Povinná hodnota. Musí být definován podřízený [element ButtonText](../extensibility/buttontext-element.md) .|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Buttons – Element](../extensibility/buttons-element.md)|Prvky tlačítka skupiny|

## <a name="example"></a>Příklad
 Následující příklad definuje tlačítko v souboru *. vsct* .

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
