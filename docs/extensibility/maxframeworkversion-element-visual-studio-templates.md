---
title: MaxFrameworkVersion – – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku MaxFrameworkVersion – a o tom, jak určuje maximální verzi .NET Framework, kterou šablona vyžaduje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44345b712f448bd7eedf288d7c58cb4193e1b020
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672422"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion – – element (šablony sady Visual Studio)

Určuje maximální verzi .NET Framework, kterou šablona vyžaduje. Určuje nejvyšší hodnotu dostupnou v rozevíracím seznamu **verze cílového rozhraní** dialogového okna **Nový projekt** . Aby uživatelé mohli vybrat verzi architektury, musíte zadat také [RequiredFrameworkVersion –](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) jako minimální verzi .NET Framework pro šablonu.

> [!IMPORTANT]
> Počínaje verzí Visual Studio 2017 verze 15,6 není v rozevíracím seznamu **verze rozhraní Target Framework** nadále filtr pro zobrazené šablony v části **šablony** v dialogovém okně **Nový projekt** . Místo toho se v rozevíracím seznamu **verze rozhraní Target Framework** funkce zobrazí jako výběr architektury pro vybranou šablonu.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být nejvyšší číslo verze .NET Framework, které šablona povoluje.

## <a name="remarks"></a>Poznámky

`MaxFrameworkVersion` je volitelný prvek. `MaxFrameworkVersion`Element by měl být vynechán, pokud není požadován, takže neúmyslně omezte podporovaný rozsah .NET Framework verzí pro šablonu. Pokud .NET Framework neplatí pro šablonu, mělo by být také vynecháno.

## <a name="example"></a>Příklad

Následující příklad ilustruje metadata pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] šablonu standardní třídy.

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

V tomto příkladu je maximální verze .NET Framework, který je vyžadován šablonou, reprezentovaná pomocí `MaxFrameworkVersion` , je 4.7.1. Projekt vytvořený pomocí této šablony může cílit na .NET Framework verze až do 4.7.1.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
