---
title: Strings – | Microsoft Docs
description: Element Strings obsahuje podřízený prvek ButtonText a další volitelné podřízené elementy. Ampersand v textovém řetězci určuje klávesovou zkratku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27a649c7d3a8bb808153c280921d2304de59c379
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899404"
---
# <a name="strings-element"></a>Strings – element
Element Strings musí obsahovat alespoň podřízený prvek **ButtonText.** Všechny ostatní podřízené prvky jsou volitelné. Neplatné znaky XML, například & a <, musí být kódované jako entity (' a &amp; &lt; ' atd.).

 Ampersand v textovém řetězci určuje klávesovou zkratku pro příkaz.

## <a name="syntax"></a>Syntax

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
|language|Nepovinný parametr. Language=".".|

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|Text tlačítka|Toto pole a pět následujících textových polí v definici příkazu umožňují zadat text, který se zobrazí v různých nabídkách. Ve výchozím nastavení se `ButtonText` pole zobrazí v kontrolerů nabídek. Pole `ButtonText` se také stane výchozím polem, pokud jsou ostatní textová pole prázdná. Pole `ButtonText` nemůže být prázdné, ani když jsou zadána ostatní textová pole.|
|Tooltiptext|Pole `ToolTipText` určuje text, který se zobrazí v popisu položky nabídky.<br /><br /> Pokud `ToolTipText` je pole prázdné, `ButtonText` použije se toto pole.|
|Text nabídky|Pole určuje text, který se zobrazí pro příkaz, pokud se nachází v hlavní nabídce, panelu nástrojů, v místní nabídce nebo v `MenuText` podnabídce. Pokud je `MenuText` pole prázdné, integrované vývojové prostředí (IDE) pole `ButtonText` použije. Pole `MenuText` lze použít také pro lokalizaci.<br /><br /> U místních nabídek je pole název, který se zobrazí na panelu nástrojů Místní nabídky, který umožňuje přizpůsobení místních nabídek v integrovaném `MenuText` vývojovém prostředí. Proto buďte v místní nabídce konkrétní. Použijte například místní nabídku balíčku widgetu místo zástupce.<br /><br /> Pokud `MenuText` pole nezadáte, `ButtonText` použije se.|
|Commandname|Pole určuje text, který se zobrazí v kategorii klávesnice na kartě Příkazy v dialogovém okně Přizpůsobit (k dispozici kliknutím na `CommandName` Přizpůsobit v  **nabídce** Nástroje).  |
|CanonicalName|Pole Angličtina určuje název příkazu v anglickém textu, který lze zadat do okna Příkaz pro `CanonicalName` spuštění položky nabídky.  Integrované vývojové prostředí (IDE) odsune všechny znaky, které nejsou písmeny, číslicemi, podtržítka nebo vloženými tečkami. Tento text se pak zřetězuje s `ButtonText` polem a definuje příkaz . Například nový **projekt v** nabídce **Soubor** se stane příkazem File.NewProject.<br /><br /> Pokud není zadané pole pro angličtinu, integrované vývojové prostředí (IDE) použije pole a odsune všechna kromě `CanonicalName` písmen, číslic, podtržítka a vložených `ButtonText` teček. Například text tlačítka "&příkazy..." se stane DefineCommands, kde se odebere ampersand, mezera a tři tečky.<br /><br /> Pokud je zadaný příznak a změní se text příkazu, odpovídající příkaz rozpoznaný příkazem se nezmění. Zůstane v kanonickém tvaru původních nebo `TextChanges`  `ButtonText` anglických `CanonicalName` polí.|
|LocCanonicalName|Pole `LocCanonicalName` se chová stejně jako anglické `CanonicalName` pole, ale umožňuje zadání lokalizovaného textu příkazu. Je možné zadat obě kanonická pole. Vzhledem k tomu, že integrované  vývojové prostředí (IDE) pouze parsuje text zadaný v okně Příkaz a přidruží ho k příkazu, může být ke stejnému příkazu přidružen anglický i ne english text.|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[Button – element](../extensibility/button-element.md)|Definuje prvek, se kterými může uživatel pracovat.|
|[Menu – element](../extensibility/menu-element.md)|Definuje jednu položku nabídky.|
|[Combo – element](../extensibility/combo-element.md)|Definuje příkazy, které se zobrazí v poli se seznamem.|

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
