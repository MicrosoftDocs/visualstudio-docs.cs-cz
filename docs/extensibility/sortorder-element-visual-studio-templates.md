---
title: Element prořazení (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o elementu upřesňuj a o tom, jak Určuje hodnotu, která se používá k uspořádání šablony, jak se zobrazuje v dialogovém okně Nový projekt nebo přidat novou položku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a086f2ae678541ce28e9ede874c4198e349f438
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942916"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder – element (šablony sady Visual Studio)
Určuje hodnotu, která se používá k uspořádání šablony, mezi ostatními šablonami ve stejné kategorii, jak se zobrazuje v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .

 \<VSTemplate> \<TemplateData>
 \<SortOrder>

## <a name="syntax"></a>Syntax

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené elementy
 Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 `integer`Hodnota, která představuje hodnotu pořadí řazení.

## <a name="remarks"></a>Poznámky
 `SortOrder` je volitelný prvek. Výchozí hodnota je 100 a všechny hodnoty musí být násobkem 10.

 `SortOrder`Element je ignorován pro uživatelem vytvořené šablony. Všechny uživatelem vytvořené šablony jsou seřazené abecedně.

 Šablony s nízkou hodnotou pořadí řazení se zobrazí v dialogovém okně **Nový projekt** nebo **Nový přidat položku** před šablonami, které mají vysoké hodnoty pořadí řazení.

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] šablonu standardní třídy.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 V tomto příkladu `SortOrder` je prvek relativně vysoký. Je pravděpodobnější, že ostatní [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] šablony položek budou mít `SortOrder` hodnotu nižší než `290` a zobrazí se před touto šablonou v dialogovém okně **Nová položka** .

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
