---
title: Řetězec Element | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699720"
---
# <a name="strings-element"></a>Strings – element
Strings Element musí obsahovat alespoň Podřízený prvek **ButtonText.** Všechny ostatní podřízené prvky jsou volitelné. Neplatné znaky XML, například & a <, musí být&amp;kódovány&lt;jako entity (' ' a ' ' a tak dále).

 Ampersand v textovém řetězci určuje klávesovou zkratku pro příkaz.

## <a name="syntax"></a>Syntaxe

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|language|Nepovinný parametr. Jazyk=""..|

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|ButtonText|Toto pole a pět následujících textových polí v definici příkazu umožňují určit text, který se zobrazí v různých nabídkách. Ve výchozím `ButtonText` nastavení se pole zobrazí v řadičích nabídek. Pole `ButtonText` se také stane výchozím, pokud jsou ostatní textová pole prázdná. Pole `ButtonText` nemůže být prázdné ani v případě, že jsou zadána ostatní textová pole.|
|Tooltiptext|Toto `ToolTipText` pole určuje text, který se zobrazí v popisku položky nabídky.<br /><br /> Pokud `ToolTipText` je pole prázdné, `ButtonText` bude použito.|
|Text nabídky|Toto `MenuText` pole určuje text, který je zobrazen pro příkaz, pokud je v hlavní nabídce, na panelu nástrojů, v místní nabídce nebo v podnabídce. Pokud `MenuText` je pole prázdné, použije `ButtonText` toto pole integrované vývojové prostředí (IDE). Toto `MenuText` pole lze také použít pro lokalizaci.<br /><br /> U místních nabídek `MenuText` je pole název, který je zobrazen na panelu nástrojů Místní nabídky, který umožňuje přizpůsobení místních nabídek v rozhraní IDE. Proto buďte konkrétní v tom, co pojmenujete místní nabídku; použijte například "Widget Balíček Zástupce menu" místo "Zástupce".<br /><br /> Pokud `MenuText` toto pole není `ButtonText` zadáno, bude použito.|
|Commandname|Pole `CommandName` určuje text, který se zobrazí v kategorii klávesnice na kartě **Příkazy** v dialogovém okně **Přizpůsobit** (k dispozici klepnutím na **tlačítko Přizpůsobit** v nabídce **Nástroje).**|
|Název kanonýr|Anglické `CanonicalName` pole určuje název příkazu v anglickém textu, který lze zadat do okna **Příkaz** pro spuštění položky nabídky. IDE odstraní všechny znaky, které nejsou písmena, číslice, podtržítka nebo vložené tečky. Tento text je pak zřetězen s polem `ButtonText` a definuje příkaz. Například **Nový projekt** v nabídce **Soubor** se stane příkazem File.NewProject.<br /><br /> Pokud není `CanonicalName` zadáno anglické pole, ide používá `ButtonText` pole a odstraní všechna kromě písmen, číslic, podtržítk a vložených období. Například text tlačítka "&Definovat příkazy..." stane DefineCommands, kde ampersand, prostor a tři tečky jsou odstraněny.<br /><br /> Pokud `TextChanges` je zadán příznak a text příkazu se změní, odpovídající příkaz rozpoznaný **příkazem** se nezmění; zůstává kanonickou formou původního `ButtonText` `CanonicalName` nebo anglického pole.|
|LocCanonicalName|Pole `LocCanonicalName` se chová stejně jako `CanonicalName` anglické pole, ale umožňuje zadat lokalizovaný text příkazu. Lze zadat obě kanonická pole. Vzhledem k tomu, že ide pouze analyzuje text zadaný v okně **Příkaz** a přidruží jej k příkazu, anglický i neanglický text může být přidružen ke stejnému příkazu.|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[Button – element](../extensibility/button-element.md)|Definuje prvek, se kterým může uživatel pracovat.|
|[Menu – element](../extensibility/menu-element.md)|Definuje jednu položku nabídky.|
|[Combo – element](../extensibility/combo-element.md)|Definuje příkazy, které se zobrazují v poli se seznamem.|

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
