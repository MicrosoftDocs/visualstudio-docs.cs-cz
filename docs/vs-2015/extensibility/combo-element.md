---
title: Prvek pole se seznamem | Dokumentace Microsoftu
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
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ab350133813f32b87570ea17df50060f93bc300
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788919"
---
# <a name="combo-element"></a>Combo – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje příkazy, které se zobrazí v poli se seznamem. Existují čtyři typy polí se seznamem, následujícím způsobem: DropDownCombo, DynamicCombo, IndexCombo a MRUCombo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|identifikátor GUID|Požadováno. Identifikátor GUID identifikátoru GUID a ID příkazu.|  
|id|Požadováno. ID identifikátoru GUID a ID příkazu.|  
|defaultWidth|Požadováno. Celé číslo, které určuje šířka v pixelech pro pole se seznamem.|  
|idCommandList|Požadováno. ID, které se odešle cíli aktivní zařadí načíst seznam položek, který se má zobrazit v poli se seznamem. ID bude ve stejném oboru jako ovládací prvek identifikátor GUID.|  
|Priorita|Volitelné. Číselná hodnota, která určuje prioritu.|  
|– typ|Volitelné. Výčtová hodnota, která určuje typ tlačítka.<br /><br /> Pokud není zadaný, použije tlačítko.<br /><br /> DropDownCombo<br /> Sady VSPackage zodpovídá za vyplnění obsah pro toto pole se seznamem. Uživatel nic nelze zadat do textového pole tomto rozevíracím seznamu.<br /><br /> DynamicCombo<br /> Sady VSPackage zodpovídá za vyplnění obsah tohoto pole se seznamem. Uživatel může upravit toto pole se seznamem a také v něm vyberte položky.<br /><br /> IndexCombo<br /> Stejné jako DynamicCombo s výjimkou, že vyvolá index položky spíše než jeho textu.<br /><br /> MRUCombo<br /> Vyplnění podle integrované vývojové prostředí (IDE) jménem sady VSPackage.  Uživatel může upravovat v tomto poli se seznamem. Prostředí IDE pamatuje až po poslední 16 položek za pole se seznamem.<br /><br /> Když uživatel vybere něco v poli se seznamem nebo zadá něco nového, rozhraní IDE upozorní odpovídající VSPackage.|  
|Podmínka|Volitelné. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Nadřazené|Volitelné. Nadřazený prvek tlačítko.|  
|CommandFlag|Požadováno. Zobrazit [Command Flag – Element](../extensibility/command-flag-element.md). Platné hodnoty CommandFlag pro tlačítka jsou následujícím způsobem.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Kláves<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Řetězce|Požadováno. Zobrazit [řetězce Element](../extensibility/strings-element.md). ButtonText – element podřízený, musí být definovaný.|  
|Poznámka|Volitelný komentář.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Commands – element](../extensibility/commands-element.md)|Představuje kolekci příkazů na panelu nástrojů VSPackage.|  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

