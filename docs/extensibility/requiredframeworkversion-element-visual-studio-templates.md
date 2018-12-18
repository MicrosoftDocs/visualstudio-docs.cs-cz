---
title: Requiredframeworkversion – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23538e8e00553322f4f04e50414a8b3ddbd73b91
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39635913"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Requiredframeworkversion – element (šablony sady Visual Studio)

Určuje minimální verzi rozhraní .NET Framework, která je vyžadované šablonou. Způsobí, že **cílovou verzi rozhraní Framework** rozevírací seznam, který se má zobrazit **nový projekt** dialogového okna. `RequiredFrameworkVersion` Element také určuje nejnižší hodnota, která je k dispozici v rozevírací nabídce.

> [!IMPORTANT]
> Od verze Visual Studio 2017 verze 15.6 a **cílovou verzi rozhraní Framework** rozevíracího seznamu už není filtr pro zobrazený šablony v **šablony** část **nový projekt** dialogového okna. Místo toho rozevírací seznam funguje jako výběr framework pro vybranou šablonu.

 \<Vstemplate – > \<TemplateData > \<requiredframeworkversion – >

## <a name="syntax"></a>Syntaxe

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData –](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Rozděluje šablonu a definuje, jak se zobrazí buď **nový projekt** nebo **přidat novou položku** dialogové okno.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být číslo minimální verze rozhraní .NET Framework, který je požadovaný pro šablonu.

## <a name="remarks"></a>Poznámky

`RequiredFrameworkVersion` je volitelný prvek. Použijte tento prvek jenom v případě, že šablony podporují konkrétní minimální verzi (a novějších verzích, pokud existuje) rozhraní .NET Framework. Pokud zadáte `RequiredFrameworkVersion` elementu a šablony nepodporuje konkrétní minimální verzi rozhraní .NET Framework **cílovou verzi rozhraní Framework** rozevíracího seznamu se zobrazí, když se nedá použít.

## <a name="example"></a>Příklad

Následující příklad ukazuje metadata pro standardní [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] šablony třídy.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

V tomto příkladu, minimální verze rozhraní .NET Framework, která je nutná šablonou, reprezentovaný `RequiredFrameworkVersion`, je 3.0. Do projektu vytvořeného s touto šablonou můžete cílit na rozhraní .NET Framework verze 3.0 od.

## <a name="see-also"></a>Viz také:

- [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Cílení na určitou konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
