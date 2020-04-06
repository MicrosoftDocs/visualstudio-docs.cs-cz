---
title: Kombinovaný prvek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739816"
---
# <a name="combo-element"></a>Kombinovaný prvek
Definuje příkazy, které se zobrazují v poli se seznamem. Existují čtyři druhy polí se seznamem, a to následovně: DropDownCombo, DynamicCombo, IndexCombo a MRUCombo.

## <a name="syntax"></a>Syntaxe

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|
|defaultWidth|Povinná hodnota. Celé číslo, které určuje šířku obrazového bodu pro pole se seznamem.|
|idCommandList|Povinná hodnota. ID, které je odesláno do cíle aktivního příkazu k načtení seznamu položek, které mají být zobrazeny v poli se seznamem. ID bude ve stejném oboru GUID jako ovládací prvek.|
|Prioritou|Nepovinný parametr. Číselná hodnota, která určuje prioritu.|
|type|Nepovinný parametr. Výčet hodnoty, která určuje typ tlačítka.<br /><br /> Pokud není uveden, používá Button.<br /><br /> DropDownCombo<br /> VSPackage je zodpovědný za vyplnění obsahu pro toto pole se seznamem. Uživatel nemůže zadat nic do textového pole tohoto rozevíracího souboru.<br /><br /> DynamicCombo<br /> VSPackage je zodpovědný za vyplnění obsahu tohoto pole se seznamem. Uživatel může upravit toto kombo a také vybrat položky v něm.<br /><br /> IndexCombo<br /> Stejné jako DynamicCombo s tím rozdílem, že vyvolává index položky spíše než jeho text.<br /><br /> MRUCombo<br /> Vyplněno integrovaným vývojového prostředí (IDE) jménem VSPackage.  Uživatel může upravovat v tomto poli se seznamem. IDE si pamatuje až do posledních 16 položek na pole se seznamem.<br /><br /> Když uživatel vybere něco v poli se seznamem nebo zadá něco nového, ide upozorní příslušné VSPackage.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený|Nepovinný parametr. Nadřazený prvek tlačítka.|
|Příkaz Ový příznak|Povinná hodnota. Viz [Element command flag](../extensibility/command-flag-element.md). Platné commandflag hodnoty pro Button jsou následující.<br /><br /> - Malá a velká písmena<br /><br /> - Pouze velitel<br /><br /> - Výchozí zakázáno<br /><br /> - DefaultInvisible<br /><br /> - Dynamická viditelnost<br /><br /> - Funkce FilterKeys<br /><br /> - IconandText<br /><br /> - NoAutocomplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - RoztáhnoutVodorovně|
|Řetězce|Povinná hodnota. Viz [Strings element](../extensibility/strings-element.md). Podřízený prvek ButtonText musí být definován.|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element příkazy](../extensibility/commands-element.md)|Představuje kolekci příkazů na panelu nástrojů VSPackage.|

## <a name="example"></a>Příklad

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
