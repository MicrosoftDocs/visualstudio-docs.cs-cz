---
title: AppliesTo – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f399e0b054b5f9b112733399d644e1357837049
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280719"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo – element (šablony sady Visual Studio)
Určuje volitelný výraz, který musí odpovídat jedné nebo více možnostem (viz <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>). Možnosti jsou vystavené typy projektů hierarchie jako vlastnost <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5>. Tímto způsobem může šablony sdílet více typů projektů, které mají společné příslušné schopnosti.  
  
 Tento element je volitelný. Soubor šablony může obsahovat maximálně jednu jeho instanci. Tento element pouze umožňuje určit, kterou šablonu položky lze případně použít, na základě schopností aktuálně vybraného aktivního projektu. Neumožňuje určit, že šablonu položky nelze použít. Pokud `AppliesTo` chybí nebo výraz nevyjadřovat výslovný úspěšně, potom `TemplateID` nebo `TemplateGroupID` umožňuje zajistit, že šablona použitelný, jako v předchozích verzích produktu.  
  
 Zavedena v aplikaci Visual Studio 2013 Update 2. Tak, aby odkazovaly na správné verzi, najdete v článku [odkazování na sestavení doručit v aktualizaci 2 pro Visual Studio 2013 SDK](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<Vstemplate – >  
 \<TemplateData >  
 \<AppliesTo – >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<AppliesTo>Capability1</AppliesTo>   
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateData –](../extensibility/templatedata-element-visual-studio-templates.md)|Určuje kategorii šablony.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota. Tento text určuje schopnosti projektu.  
  
 Platná syntaxe výrazu je definována takto:  
  
-   Výraz schopnosti, například "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".  
  
-   "&#124;" Je operátor OR.  
  
-   "&" A "+" znaky jsou oba operátory.  
  
-   Znak "!" je operátor NOT.  
  
-   Závorky určují pořadí vyhodnocování.  
  
-   Hodnota null nebo prázdný výraz jsou vyhodnoceny jako shoda.  
  
-   Schopnosti projektu mohou používat libovolné znaky kromě těchto vyhrazených znaků: "'' :;,+-*/\\! ~&#124;& %$@^() ={}<> []? \t\b\n\r  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje tři různé šablony. `Template1` vztahuje na všechny typy projektů jazyka C# nebo jakýkoli jiný typ projektu, který podporuje `WindowsAppContainer` funkce. `Template2` platí pro všechny projekty jazyka C# jakéhokoli druhu. `Template3` platí pro projekty jazyka C#, které nejsou `WindowsAppContainer` projekty.  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## <a name="see-also"></a>Viz také:  
 [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)