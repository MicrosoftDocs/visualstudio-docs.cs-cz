---
title: AppliesTo – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o elementu AppliesTo a o tom, jak Určuje volitelný výraz, který odpovídá jedné nebo více funkcím.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48f1d7e0011b3f195224d8e55072ccd4c7666802
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876118"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo – element (šablony sady Visual Studio)

Určuje volitelný výraz, který odpovídá jedné nebo více funkcím (viz <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher> ). K dispozici jsou možnosti typu projektu prostřednictvím hierarchie jako vlastnost [__VSHPROPID5. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). Tímto způsobem může šablony sdílet více typů projektů, které mají společné příslušné schopnosti.

Tento element je volitelný. Soubor šablony může obsahovat maximálně jednu jeho instanci. Tento element pouze umožňuje určit, kterou šablonu položky lze případně použít, na základě schopností aktuálně vybraného aktivního projektu. Neumožňuje určit, že šablonu položky nelze použít. Pokud `AppliesTo` chybí, nebo se výraz neaktivuje úspěšně, pak se `TemplateID` `TemplateGroupID` použije k provedení šablony, jako u předchozích verzí produktu.

Zavedeno ve Visual Studio 2013 Update 2. Chcete-li odkazovat na správnou verzi, přečtěte si odkazování na [sestavení Doručená v sadě Visual Studio 2013 SDK Update 2](/previous-versions/dn632168(v=vs.120)).

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Syntax

```xml
<AppliesTo>Capability1</AppliesTo>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

Žádné

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Určuje kategorii šablony.|

## <a name="text-value"></a>Textová hodnota

Je vyžadována textová hodnota. Tento text určuje schopnosti projektu.

Platná syntaxe výrazu je definována takto:

- Výraz schopnosti, například "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".

- "&#124;" je operátor OR.

- Znaky "&" a "+" jsou oba operátory a.

- Znak "!" je operátor NOT.

- Závorky určují pořadí vyhodnocování.

- Hodnota null nebo prázdný výraz jsou vyhodnoceny jako shoda.

- Možnosti projektu můžou být libovolný znak kromě těchto vyhrazených znaků: "' ':;, +-*/ \\ ! ~&#124;&% $ @ ^ () = {} [] <>? \t\b\n\r

## <a name="example"></a>Příklad

Následující příklad ukazuje tři různé šablony. `Template1` aplikuje se buď na všechny typy projektů C#, nebo na jakýkoli jiný typ projektu, který podporuje `WindowsAppContainer` schopnost. `Template2` platí pro všechny projekty v jazyce C# libovolného druhu. `Template3` platí pro projekty C#, které nejsou `WindowsAppContainer` projekty.

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

- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
