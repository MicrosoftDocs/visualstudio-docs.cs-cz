---
title: Prvek SortOrder (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699956"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder – element (šablony sady Visual Studio)
Určuje hodnotu, která se používá k uspořádání šablony, mimo jiné šablony ve stejné kategorii, jak se zobrazí v dialogovém okně **Nový projekt** nebo Přidat **novou položku.**

 \<VSTemplate \<> TemplateData> \<pořadí řazení>

## <a name="syntax"></a>Syntaxe

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené elementy
 Žádné.

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 A, `integer` který představuje hodnotu pořadí řazení.

## <a name="remarks"></a>Poznámky
 `SortOrder`je volitelný prvek. Výchozí hodnota je 100 a všechny hodnoty musí být násobky 10.

 Prvek `SortOrder` je ignorován pro uživatelem vytvořené šablony. Všechny uživatelem vytvořené šablony jsou seřazeny abecedně.

 Šablony s nízkými hodnotami pořadí řazení se zobrazí v dialogovém okně **Nový projekt** nebo Nová **přidat položku** před šablonami s vysokými hodnotami pořadí řazení.

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

 V tomto příkladu `SortOrder` je prvek poměrně vysoký. Je pravděpodobné, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] že jiné šablony `SortOrder` položek budou `290` mít hodnotu nižší než a zobrazí se před touto šablonou v dialogovém okně **Nová položka.**

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
