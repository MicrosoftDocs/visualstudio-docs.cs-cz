---
title: Element prořazení (šablony sady Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719915"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder – element (šablony sady Visual Studio)
Určuje hodnotu, která se používá k uspořádání šablony, mezi ostatními šablonami ve stejné kategorii, jak se zobrazuje v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .

 \<VSTemplate > \<TemplateData > \<SortOrder >

## <a name="syntax"></a>Syntaxe

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

|Prvek|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 @No__t_0, která představuje hodnotu pořadí řazení.

## <a name="remarks"></a>Poznámky
 `SortOrder` je volitelný prvek. Výchozí hodnota je 100 a všechny hodnoty musí být násobkem 10.

 Element `SortOrder` se pro šablony vytvořené uživatelem ignoruje. Všechny uživatelem vytvořené šablony jsou seřazené abecedně.

 Šablony s nízkou hodnotou pořadí řazení se zobrazí v dialogovém okně **Nový projekt** nebo **Nový přidat položku** před šablonami, které mají vysoké hodnoty pořadí řazení.

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro standardní šablonu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] třídy.

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

 V tomto příkladu je prvek `SortOrder` relativně vysoký. Je pravděpodobnější, že jiné šablony [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] položek budou mít `SortOrder` hodnotu nižší než `290` a zobrazí se před touto šablonou v dialogovém okně **Nová položka** .

## <a name="see-also"></a>Viz také:
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)