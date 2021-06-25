---
title: Combo – | Microsoft Docs
description: 'Element Combo definuje příkazy, které se zobrazí v poli se seznamem. Existují čtyři druhy: DropDownCombo, DynamicCombo, IndexCombo a MRUCombo.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 431d68b6e545506f5fc90cc5a98a52dd4f1c33ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904951"
---
# <a name="combo-element"></a>Combo – element
Definuje příkazy, které se zobrazí v poli se seznamem. Existují čtyři druhy polí se seznamem: DropDownCombo, DynamicCombo, IndexCombo a MRUCombo.

## <a name="syntax"></a>Syntax

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
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|
|defaultWidth|Povinná hodnota. Celé číslo, které určuje šířku pixelů pole se seznamem.|
|idCommandList|Povinná hodnota. ID odeslané do aktivního cíle příkazu, aby se načítá seznam položek, které se mají zobrazit v poli se seznamem. ID bude ve stejném oboru GUID jako ovládací prvek.|
|Prioritou|Nepovinný parametr. Číselná hodnota, která určuje prioritu.|
|typ|Nepovinný parametr. Výčtová hodnota, která určuje typ tlačítka.<br /><br /> Pokud není daný, použije Button.<br /><br /> DropDownCombo<br /> Balíček VSPackage zodpovídá za vyplnění obsahu tohoto pole se seznamem. Uživatel nemůže do textového pole tohoto rozevíracího seznamu nic zadat.<br /><br /> DynamicCombo<br /> Balíček VSPackage zodpovídá za vyplnění obsahu tohoto pole se seznamem. Uživatel může tuto kombinaci upravit a také vybrat položky, které obsahuje.<br /><br /> IndexCombo<br /> Stejné jako DynamicCombo s tím rozdílem, že místo jejího textu vyvolává index položky.<br /><br /> MRUCombo<br /> Je vyplněné integrovaným vývojovým prostředím (IDE) jménem balíčku VSPackage.  Uživatel může v tomto poli se seznamem upravit. Integrované vývojové prostředí si pamatuje až posledních 16 položek na pole se seznamem.<br /><br /> Když uživatel vybere něco v poli se seznamem nebo zadá něco nového, integrované vývojové prostředí (IDE) upozorní příslušný balíček VSPackage.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený|Nepovinný parametr. Nadřazený prvek tlačítka.|
|Prodleva příkazu|Povinná hodnota. Viz [Command flag element](../extensibility/command-flag-element.md). Platné hodnoty CommandFlag pro Tlačítko jsou následující.<br /><br /> – Malá a velká písmena<br /><br /> – CommandWellOnly<br /><br /> – DefaultDisabled<br /><br /> – DefaultInvisible<br /><br /> – Dynamickávisitelnost<br /><br /> – FilterKeys<br /><br /> - IconAndText<br /><br /> – NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> – NoCustomize<br /><br /> – NoKeyCustomize<br /><br /> – StretchHorizontally|
|Řetězce|Povinná hodnota. Podívejte [se na element Strings .](../extensibility/strings-element.md) Musí být definován podřízený element ButtonText.|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Commands – element](../extensibility/commands-element.md)|Představuje kolekci příkazů na panelu nástrojů VSPackage.|

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
- [Visual Studio souborů tabulky příkazů (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
