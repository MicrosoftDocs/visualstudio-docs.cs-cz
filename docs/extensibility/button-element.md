---
title: Button – | Microsoft Docs
description: 'Element Button definuje prvek, se kterými může uživatel pracovat. Tlačítka mohou být různého druhu: Button (Tlačítko), MenuButton (Tlačítko nabídky) a SplitDropDown (Rozevírací seznam rozdělení).'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 630d848c40b13a929c3dd91b47e1c35529efaa50
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901744"
---
# <a name="button-element"></a>Button – element
Definuje prvek, se kterými může uživatel pracovat. Tlačítka mohou být různých druhů: Button (Tlačítko), MenuButton (Tlačítko Nabídky) a SplitDropDown (Rozevírací seznam).

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
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|
|Prioritou|Nepovinný parametr. Číselná hodnota, která určuje prioritu.|
|typ|Nepovinný parametr. Výčtová hodnota, která určuje druh tlačítka.<br /><br /> Pokud není daný, použije Button.<br /><br /> Tlačítko<br /> Standardní příkaz, který se zobrazí na panelech nástrojů (obvykle jako ikonické tlačítko), nabídkách a kontextových nabídkách.<br /><br /> Tlačítko nabídky<br /> Položka nabídky, která nes spustí příkaz, ale vytvoří další nabídku.<br /><br /> Rozevírací seznam SplitDropDown<br /> Ovládací prvky, jako jsou tlačítka Zpět a Znovu na standardním panelu nástrojů v Microsoft Wordu.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|[Nadřazený element](../extensibility/parent-element.md)|Nepovinný parametr. Nadřazený prvek tlačítka.|
|[Icon – element](../extensibility/icon-element.md)|Nepovinný parametr. Ikona přidružená k tlačítku|
|[Element příznaku příkazu](../extensibility/command-flag-element.md)|Povinná hodnota. Platné hodnoty CommandFlag pro Tlačítko jsou následující.<br /><br /> – AllowParams<br /><br /> – CommandWellOnly<br /><br /> – DefaultDisabled<br /><br /> – DefaultInvisible<br /><br /> – DontCache<br /><br /> – DynamicItemStart<br /><br /> – Dynamickávisitelnost<br /><br /> – FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> – NoCustomize<br /><br /> – NoKeyCustomize<br /><br /> – NoShowOnMenuController<br /><br /> - Pict<br /><br /> – PostExec<br /><br /> – ProfferedCmd<br /><br /> – RouteToDocs<br /><br /> – TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> – TextChanges<br /><br /> – TextChangesButton<br /><br /> – TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> – TextOnly|
|[Strings – element](../extensibility/strings-element.md)|Povinná hodnota. Musí být [definován podřízený element ButtonText.](../extensibility/buttontext-element.md)|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Buttons – element](../extensibility/buttons-element.md)|Seskupí prvky Tlačítka.|

## <a name="example"></a>Příklad
 Následující příklad definuje tlačítko v *souboru .vsct.*

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
- [Visual Studio souborů tabulky příkazů (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
