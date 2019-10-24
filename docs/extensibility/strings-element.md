---
title: Element Strings | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c91a8ea07daee77855017d641a569a892612c3e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719435"
---
# <a name="strings-element"></a>Strings – element
Element Strings musí obsahovat alespoň **ButtonText** podřízený element. Všechny ostatní podřízené prvky jsou volitelné. Neplatné znaky XML, například ' & ' a ' < ', musí být kódovány jako entity (' &amp; ' a ' &lt; ' atd.).

 Ampersand v textovém řetězci Určuje klávesovou zkratku pro příkaz.

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
|jazyk|Volitelné. Jazyk = ".".|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|ButtonText|Toto pole a pět následujících textových polí v definici příkazu vám umožní určit text, který se zobrazí v různých nabídkách. Ve výchozím nastavení se pole `ButtonText` zobrazuje v řadičích nabídek. Pole `ButtonText` se také stávají výchozím nastavením, pokud jsou ostatní textová pole prázdná. Pole `ButtonText` nemůže být prázdné, i když jsou uvedena další textová pole.|
|ToolTipText|Pole `ToolTipText` Určuje text, který se zobrazí v popisku pro položku nabídky.<br /><br /> Pokud je pole `ToolTipText` prázdné, použije se pole `ButtonText`.|
|MenuText|Pole `MenuText` Určuje text, který se zobrazí pro příkaz, pokud je v hlavní nabídce, panelu nástrojů, v místní nabídce nebo v podnabídce. Pokud je pole `MenuText` prázdné, integrované vývojové prostředí (IDE) používá pole `ButtonText`. Pole `MenuText` lze také použít k lokalizaci.<br /><br /> U místních nabídek je pole `MenuText` název, který se zobrazí na panelu nástrojů místní nabídky, který umožňuje přizpůsobení místních nabídek v integrovaném vývojovém prostředí (IDE). Proto je nutné, aby byla v místní nabídce pojmenovaná. použijte například zkratku balíčku widget "místo" zástupce ".<br /><br /> Pokud pole `MenuText` není zadáno, použije se pole `ButtonText`.|
|CommandName|Pole `CommandName` Určuje text, který se zobrazí v kategorii klávesnice na kartě **příkazy** v dialogovém okně **přizpůsobit** (k dispozici kliknutím na **přizpůsobit** v nabídce **nástroje** ).|
|Kanonický tvar|Pole English `CanonicalName` Určuje název příkazu v anglickém textu, který lze zadat do **příkazového** okna pro provedení položky nabídky. IDE vyříznout všechny znaky, které nejsou písmena, číslice, podtržítka nebo vložená tečky. Tento text se pak zřetězí do pole `ButtonText` k definování příkazu. Například **Nový projekt** v nabídce **soubor** se zobrazí jako příkaz soubor. NewProject.<br /><br /> Pokud pole `CanonicalName` v angličtině není zadáno, rozhraní IDE použije pole `ButtonText` a odstraní všechny kromě písmen, číslic, podtržítka a vložených teček. Například text tlačítka "& definovat příkazy..." dojde k DefineCommands, kde se odeberou ampersand, místo a tři tečky.<br /><br /> Pokud je zadán příznak `TextChanges` a text příkazu je změněn, odpovídající příkaz rozpoznaný **příkazovým** oknem se nezmění. zůstane v kanonickém tvaru původní `ButtonText` nebo anglických `CanonicalName`ch polí.|
|LocCanonicalName|Pole `LocCanonicalName` se chová stejně jako anglické `CanonicalName` pole, ale umožňuje zadání lokalizovaného textu příkazu. Lze zadat jak kanonická pole. Vzhledem k tomu, že IDE jenom analyzuje text zadaný v **příkazovém** okně a přidruží ho k příkazu, může být ke stejnému příkazu přidružená angličtina i jiný text než angličtina.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[Button – element](../extensibility/button-element.md)|Definuje prvek, se kterým může uživatel pracovat.|
|[Menu – element](../extensibility/menu-element.md)|Definuje jednu položku nabídky.|
|[Combo – element](../extensibility/combo-element.md)|Definuje příkazy, které se zobrazí v poli se seznamem.|

## <a name="see-also"></a>Viz také:
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)