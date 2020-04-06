---
title: Platí pro element (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b5ee1e3cad0b4d8ddbe0fc2dfa1c2d478ec063
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740083"
---
# <a name="appliesto-element-visual-studio-templates"></a>Element AppliesTo (šablony sady Visual Studio)

Určuje volitelný výraz, který odpovídá jedné <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>nebo více funkcím (viz ). Možnosti jsou vystaveny typy projektů prostřednictvím hierarchie jako [vlastnost __VSHPROPID5. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). Tímto způsobem může šablony sdílet více typů projektů, které mají společné příslušné schopnosti.

Tento element je volitelný. Soubor šablony může obsahovat maximálně jednu jeho instanci. Tento element pouze umožňuje určit, kterou šablonu položky lze případně použít, na základě schopností aktuálně vybraného aktivního projektu. Neumožňuje určit, že šablonu položky nelze použít. Pokud `AppliesTo` chybí nebo výraz není úspěšně odhlasovat, pak `TemplateID` nebo `TemplateGroupID` se používá k nastavení šablony použitelné, stejně jako u předchozích verzí produktu.

Představenv visual studio 2013 update 2. Chcete-li odkazovat na správnou verzi, naleznete [v tématu Odkazování sestavení dodaných v sadě Visual Studio 2013 SDK Update 2](/previous-versions/dn632168(v=vs.120)).

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Syntaxe

```xml
<AppliesTo>Capability1</AppliesTo>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

Žádné.

### <a name="child-elements"></a>Podřízené prvky

Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Určuje kategorii šablony.|

## <a name="text-value"></a>Textová hodnota

Je vyžadována textová hodnota. Tento text určuje schopnosti projektu.

Platná syntaxe výrazu je definována takto:

- Výraz schopnosti, například "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".

- "&#124;" je operátor OR.

- Znaky "&" a "+" jsou oba operátory AND.

- Znak "!" je operátor NOT.

- Závorky určují pořadí vyhodnocování.

- Hodnota null nebo prázdný výraz jsou vyhodnoceny jako shoda.

- Možnosti projektu mohou být libovolný znak kromě těchto vyhrazených znaků: "'':,,+-*/\\!~&#124;&%$@^()={}[]<>? \t\b\n\r

## <a name="example"></a>Příklad

Následující příklad ukazuje tři různé šablony. `Template1`platí buď pro všechny typy projektu Jazyka C# `WindowsAppContainer` nebo jakýkoli jiný typ projektu, který podporuje schopnosti. `Template2`platí pro všechny projekty jazyka C#jakéhokoli druhu. `Template3`platí pro projekty jazyka `WindowsAppContainer` C#, které nejsou projekty.

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

## <a name="see-also"></a>Viz také

- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
