---
title: Element Combo | Microsoft Docs
description: 'Element ComboBox definuje příkazy, které se zobrazí v poli se seznamem. Existují čtyři typy: DropDownCombo, DynamicCombo, IndexCombo a MRUCombo.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e5c16db298edb0e1fe526190531df4cb638f8e3d
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974313"
---
# <a name="combo-element"></a>Element Combo
Definuje příkazy, které se zobrazí v poli se seznamem. Existují čtyři druhy polí se seznamem, a to takto: DropDownCombo, DynamicCombo, IndexCombo a MRUCombo.

## <a name="syntax"></a>Syntaxe

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID|
|defaultWidth|Povinná hodnota. Celé číslo, které určuje šířku v pixelech pro pole se seznamem.|
|idCommandList|Povinná hodnota. ID, které je odesláno do cíle aktivního příkazu pro načtení seznamu položek, které mají být zobrazeny v poli se seznamem. ID bude ve stejném oboru identifikátorů GUID jako ovládací prvek.|
|upřednostněn|Nepovinný parametr. Číselná hodnota, která určuje prioritu.|
|typ|Nepovinný parametr. Výčtová hodnota, která určuje typ tlačítka.<br /><br /> Pokud není zadaný, použije se tlačítko.<br /><br /> DropDownCombo<br /> VSPackage je zodpovědný za vyplnění obsahu pro toto pole se seznamem. Uživatel nemůže v textovém poli tohoto rozevíracího seznamu zadávat cokoli.<br /><br /> DynamicCombo<br /> VSPackage je zodpovědný za vyplnění obsahu tohoto pole se seznamem. Uživatel může tuto položku rozevírací seznam upravit a také vybrat položky v ní.<br /><br /> IndexCombo<br /> Stejné jako DynamicCombo s tím rozdílem, že vyvolává index položky namísto jejího textu.<br /><br /> MRUCombo<br /> Vyplněný integrovaným vývojovým prostředím (IDE) jménem VSPackage.  Uživatel může v tomto poli se seznamem upravit. Rozhraní IDE se zapamatuje až do posledních 16 položek na pole se seznamem.<br /><br /> Když uživatel vybere něco v poli se seznamem nebo vloží něco nového, IDE ho upozorní na příslušný VSPackage.|
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený|Nepovinný parametr. Nadřazený element tlačítka|
|CommandFlag|Povinná hodnota. Viz [element příznak příkazu](../extensibility/command-flag-element.md). Platné hodnoty CommandFlag pro tlačítko jsou následující.<br /><br /> – CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> – Filtrování kláves<br /><br /> - IconAndText<br /><br /> -Automatické dokončování<br /><br /> - NoButtonCustomize<br /><br /> -Upravit<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Řetězce|Povinná hodnota. Viz [řetězec element](../extensibility/strings-element.md). Musí být definován podřízený element ButtonText.|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Command – element](../extensibility/commands-element.md)|Představuje kolekci příkazů na panelu nástrojů VSPackage.|

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
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
