---
title: Řetězce Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cc9adc4d13718fc9b0379c73b1892ba14e61d47
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789795"
---
# <a name="strings-element"></a>Strings – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Řetězce element musí obsahovat alespoň **ButtonText** podřízený element. Všechny ostatní podřízené prvky jsou volitelné. Neplatný kód XML znaky, jako 'a' a ' <' musí být zakódovaný jako entity ("&amp;"a"&lt;" a tak dále).  
  
 Znak ampersand v textovém řetězci Určuje klávesovou zkratku pro příkaz.  
  
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
|ButtonText –|Toto pole a pět následujících textová pole v definici příkazu umožňují zadat text, který se zobrazí v různých nabídkách. Ve výchozím nastavení `ButtonText` pole se zobrazí v nabídce řadiče. `ButtonText` Pole stane výchozí hodnota je-li další textová pole jsou prázdné. `ButtonText` Pole nemůže být prázdný, i když nejsou určeny další textová pole.|  
|ToolTipText –|`ToolTipText` Pole určuje text zobrazený v popisku tooltip položky nabídky.<br /><br /> Pokud `ToolTipText` je pole prázdné, `ButtonText` pole se používá.|  
|MenuText|`MenuText` Pole určuje text, který se zobrazí pro příkaz, pokud je v hlavní nabídce nástrojů, v místní nabídce nebo podnabídky. Pokud `MenuText` je pole prázdné, integrované vývojové prostředí (IDE) používá `ButtonText` pole. `MenuText` Pole můžete také použít pro lokalizaci.<br /><br /> Pro místní nabídky `MenuText` pole je název, který se zobrazí na panelu nástrojů místní nabídky, který umožňuje vlastní nastavení z místní nabídky v integrovaném vývojovém prostředí. Proto se konkrétní v pojmenujete vaší nabídky; například použijte "Widget balíček místní nabídka" místo "Místní".<br /><br /> Pokud `MenuText` pole není zadán, `ButtonText` pole se používá.|  
|commandName|`CommandName` Pole určuje text, který se zobrazí v kategorii klávesnice v **příkazy** kartu **vlastní** dialogové okno (k dispozici kliknutím **vlastní**na **nástroje** nabídky).|  
|CanonicalName|Angličtina `CanonicalName` pole určuje název příkazu v anglický text, který je možné zadat v **příkaz** okna k provedení položky nabídky. Integrované vývojové prostředí odstraní všechny znaky, které nejsou písmena, číslice, podtržítka nebo vložený období. Tento text je pak zřetězeny do `ButtonText` pole k definování příkazu. Například **nový projekt** na **souboru** nabídce stane příkaz File.NewProject.<br /><br /> Pokud Angličtina `CanonicalName` pole není zadaný, použije integrovaného vývojového prostředí `ButtonText` pole a všechny s výjimkou písmena, číslice, podtržítka a tečky vložené pásky. Například Text tlačítka "& definovat příkazy..." stane DefineCommands, kde se odeberou ampersand, prostor a na tři tečky.<br /><br /> Pokud `TextChanges` označen příznakem a text příkazu se změní, odpovídající příkaz rozpoznávaných **příkaz** okno nemění; zůstane kanonický tvar původní `ButtonText` nebo Angličtina `CanonicalName` pole.|  
|LocCanonicalName|`LocCanonicalName` Pole chová stejně jako Angličtina `CanonicalName` pole ale umožňuje lokalizované příkaz text, který má být zadán. Můžete zadat i canonical pole. Protože parsovat text zadaný do integrovaného vývojového prostředí **příkaz** okno a přidruží ji příkazem, angličtina a jiné než anglické jazykové text lze přidružit ten samý příkaz.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Button – element](../extensibility/button-element.md)|Definuje element, který může uživatel zasahovat.|  
|[Menu – element](../extensibility/menu-element.md)|Definuje jednu položku.|  
|[Combo – element](../extensibility/combo-element.md)|Definuje příkazy, které se zobrazí v poli se seznamem.|  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

