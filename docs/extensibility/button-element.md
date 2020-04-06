---
title: Prvek tlačítka | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739937"
---
# <a name="button-element"></a>Prvek tlačítka
Definuje prvek, se kterým může uživatel pracovat. Tlačítka mohou být různých druhů: Button, MenuButton a SplitDropDown.

## <a name="syntax"></a>Syntaxe

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|
|Prioritou|Nepovinný parametr. Číselná hodnota, která určuje prioritu.|
|type|Nepovinný parametr. Výčet hodnoty, která určuje druh tlačítka.<br /><br /> Pokud není uveden, používá Button.<br /><br /> Tlačítko<br /> Standardní příkaz, který se zobrazí na panelech nástrojů (obvykle jako ikonické tlačítko), nabídkách a kontextových nabídkách.<br /><br /> Tlačítko Menu<br /> Položka nabídky, která neprovede příkaz, ale vytvoří jinou nabídku.<br /><br /> Rozdělení rozevírací<br /> Ovládací prvky, například tlačítka Vrátit a znovu na standardním panelu nástrojů v aplikaci Microsoft Word.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|[Nadřazený prvek](../extensibility/parent-element.md)|Nepovinný parametr. Nadřazený prvek tlačítka.|
|[Prvek ikony](../extensibility/icon-element.md)|Nepovinný parametr. Ikona přidružená k tlačítku.|
|[Element příkazového příznaku](../extensibility/command-flag-element.md)|Povinná hodnota. Platné commandflag hodnoty pro Button jsou následující.<br /><br /> - AllowParams<br /><br /> - Pouze velitel<br /><br /> - Výchozí zakázáno<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - Dynamická viditelnost<br /><br /> - FixMenuController<br /><br /> - IconandText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowonMenuController<br /><br /> - Pict<br /><br /> - PostExec<br /><br /> - NabízenoCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextZměny<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - Pouze text|
|[Řetězec, prvek](../extensibility/strings-element.md)|Povinná hodnota. Podřízený [prvek ButtonText](../extensibility/buttontext-element.md) musí být definován.|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Prvek tlačítek](../extensibility/buttons-element.md)|Seskupí prvky tlačítka.|

## <a name="example"></a>Příklad
 Následující příklad definuje tlačítko v souboru *.vsct.*

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
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
