---
title: Řetězce Element | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5994144f07b8af84f61d7833737f45593c551b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143884"
---
# <a name="strings-element"></a>Element řetězce
Element řetězce musí obsahovat alespoň **ButtonText** podřízený element. Všechny ostatní podřízené prvky jsou volitelné. Neplatný kód XML znaky, jako například 'a' a ' <' musí být programového jako entity ('&amp;'a'&lt;' a tak dále).  
  
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
|ButtonText|Toto pole a pět následující pole text v definici příkaz umožňují zadejte text, který se zobrazí v různých nabídky. Ve výchozím nastavení `ButtonText` pole se zobrazí v nabídce řadiče. `ButtonText` Pole také změní výchozí, pokud textová pole jsou prázdné. `ButtonText` Pole nemůže být prázdná, i když nejsou určeny v ostatních polích text.|  
|ToolTipText –|`ToolTipText` Pole určuje text, který se zobrazí v popisu tlačítka pro položku nabídky.<br /><br /> Pokud `ToolTipText` pole je prázdné, `ButtonText` pole se používá.|  
|MenuText|`MenuText` Pole určuje text, který se zobrazí pro příkaz, pokud je v hlavní nabídce panelu nástrojů, v místní nabídce, nebo v podnabídky. Pokud `MenuText` je pole prázdné, používá integrované vývojové prostředí (IDE) `ButtonText` pole. `MenuText` Pole lze také pro lokalizaci.<br /><br /> Pro místní nabídky `MenuText` pole je název, který se zobrazí na panelu nástrojů místní nabídky, které umožňuje přizpůsobení místní nabídky v prostředí IDE. Proto buďte konkrétní v co zadáte název vaší místní nabídky; například použijte "Widgetů balíček místní nabídky" místo "Zástupce".<br /><br /> Pokud `MenuText` pole není zadáno, `ButtonText` pole se používá.|  
|CommandName|`CommandName` Pole určuje text, který se zobrazí v kategorii klávesnice v **příkazy** ve **přizpůsobit** dialogové okno (k dispozici kliknutím **přizpůsobit**na **nástroje** nabídky).|  
|canonicalName|Angličtině `CanonicalName` pole určuje název příkazu v anglické text, který si můžete zaznamenat do **příkaz** okno provést položku nabídky. Prostředí IDE, odstraní se žádné znaky, které nejsou písmena, číslice, podtržítka nebo vložené tečky. Tento text je pak zřetězen do `ButtonText` pole, které chcete definovat příkaz. Například **nový projekt** na **souboru** nabídka se změní příkaz File.NewProject.<br /><br /> Pokud Angličtina `CanonicalName` pole není určeno, používá rozhraní IDE `ButtonText` pole a proužky na všech kromě písmena, číslice, podtržítka, tečky embedded. Například Text tlačítka "& definovat příkazy..." stane DefineCommands, kde jsou odebrány ampersand, místo a se třemi tečkami.<br /><br /> Pokud `TextChanges` zadán příznak a text příkazu se mění, odpovídající příkaz rozpoznáno **příkaz** okno nezmění; zůstane kanonický tvar původní `ButtonText` nebo Angličtina `CanonicalName` pole.|  
|LocCanonicalName|`LocCanonicalName` Pole se chová stejně jako Angličtina `CanonicalName` pole ale umožňuje lokalizované příkaz text, který má být zadán. Je možné zadat obě pole kanonickém tvaru. Protože rozhraní IDE právě analyzuje zadaný text **příkaz** okno a známými pomocí příkazu, angličtinu a jiných než anglických text může být přidružen stejný příkaz.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Button – element](../extensibility/button-element.md)|Definuje element, který může uživatel zasahovat.|  
|[Menu – element](../extensibility/menu-element.md)|Definuje samostatnou položku nabídky.|  
|[Combo – element](../extensibility/combo-element.md)|Definuje příkazy, které se zobrazují v pole se seznamem.|  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)