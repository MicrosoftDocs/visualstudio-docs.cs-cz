---
title: Element Strings | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0eae2fd7490269d713beb9950163071dd3ba32f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160565"
---
# <a name="strings-element"></a>Strings – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element Strings musí obsahovat alespoň **ButtonText** podřízený element. Všechny ostatní podřízené prvky jsou volitelné. Neplatné znaky XML, například ' & ' a ' < ', musí být kódovány jako entity (' &amp; ' a ' ' a &lt; tak dále).  
  
 Ampersand v textovém řetězci Určuje klávesovou zkratku pro příkaz.  
  
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
|language|Nepovinný parametr. Jazyk = ".".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|ButtonText|Toto pole a pět následujících textových polí v definici příkazu vám umožní určit text, který se zobrazí v různých nabídkách. Ve výchozím nastavení `ButtonText` se pole zobrazuje v řadičích nabídek. `ButtonText`Pole se také zobrazí jako výchozí, pokud jsou ostatní textová pole prázdná. `ButtonText`Pole nemůže být prázdné, i když jsou uvedena další textová pole.|  
|ToolTipText|`ToolTipText`Pole určuje text, který se zobrazí v popisku pro položku nabídky.<br /><br /> Pokud `ToolTipText` je pole prázdné, použije se `ButtonText` pole.|  
|MenuText|`MenuText`Pole určuje text, který se zobrazí pro příkaz, pokud je v hlavní nabídce, panelu nástrojů, v místní nabídce nebo v podnabídce. Pokud `MenuText` je pole prázdné, integrované vývojové prostředí (IDE) používá `ButtonText` pole. `MenuText`Pole lze také použít k lokalizaci.<br /><br /> U místních nabídek `MenuText` je pole název, který se zobrazí na panelu nástrojů místní nabídky, který umožňuje přizpůsobení místních nabídek v integrovaném vývojovém prostředí (IDE). Proto je nutné, aby byla v místní nabídce pojmenovaná. použijte například zkratku balíčku widget "místo" zástupce ".<br /><br /> Pokud `MenuText` pole není zadáno, `ButtonText` použije se pole.|  
|CommandName|`CommandName`Pole určuje text, který se zobrazí v kategorii klávesnice na kartě **příkazy** v dialogovém okně **přizpůsobit** (k dispozici kliknutím na **přizpůsobit** v nabídce **nástroje** ).|  
|Kanonický tvar|Pole English `CanonicalName` Určuje název příkazu v anglickém textu, který lze zadat v **příkazovém** okně pro provedení položky nabídky. IDE vyříznout všechny znaky, které nejsou písmena, číslice, podtržítka nebo vložená tečky. Tento text se pak zřetězí do `ButtonText` pole, abyste mohli definovat příkaz. Například **Nový projekt** v nabídce **soubor** se zobrazí jako příkaz soubor. NewProject.<br /><br /> Pokud není `CanonicalName` zadáno pole v angličtině, rozhraní IDE použije `ButtonText` pole a odstraní všechny kromě písmen, číslic, podtržítka a vložených teček. Například text tlačítka "&definovat příkazy..." dojde k DefineCommands, kde se odeberou ampersand, místo a tři tečky.<br /><br /> Pokud `TextChanges` je příznak zadán a text příkazu je změněn, odpovídající příkaz rozpoznaný **příkazovým** oknem se nezmění, zůstane kanonický tvar původních `ButtonText` nebo anglických `CanonicalName` polí.|  
|LocCanonicalName|`LocCanonicalName`Pole se chová stejně jako v anglickém poli, `CanonicalName` ale umožňuje zadání lokalizovaného textu příkazu. Lze zadat jak kanonická pole. Vzhledem k tomu, že IDE jenom analyzuje text zadaný v **příkazovém** okně a přidruží ho k příkazu, může být ke stejnému příkazu přidružená angličtina i jiný text než angličtina.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Button – element](../extensibility/button-element.md)|Definuje prvek, se kterým může uživatel pracovat.|  
|[Menu – element](../extensibility/menu-element.md)|Definuje jednu položku nabídky.|  
|[Combo – element](../extensibility/combo-element.md)|Definuje příkazy, které se zobrazí v poli se seznamem.|  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
