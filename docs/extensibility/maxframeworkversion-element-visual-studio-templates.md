---
title: Prvek MaxFrameworkVersion (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702625"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Prvek MaxFrameworkVersion (šablony sady Visual Studio)

Určuje maximální verzi rozhraní .NET Framework, kterou šablona vyžaduje. Určuje nejvyšší hodnotu, která je k dispozici v rozevíracím okně **Verze cílového rozhraní** v dialogovém okně **Nový projekt.** Aby uživatelé mohli vybrat verzi architektury, musíte také zadat [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) jako minimální verzi rozhraní .NET Framework pro šablonu.

> [!IMPORTANT]
> Počínaje Visual Studio 2017 verze 15.6, cílový **rámec verze** rozevírací seznam již není filtr pro zobrazené šablony v části **Šablony** dialogového okna **Nový projekt.** Místo toho rozevírací nabídka **verze cílového rozhraní** funguje jako výběr architektury pro vybranou šablonu.

 \<VSTemplate \<> TemplateData> \<MaxFrameworkVersion>

## <a name="syntax"></a>Syntaxe

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být nejvyšší číslo verze rozhraní .NET Framework, který je povolen šablonou.

## <a name="remarks"></a>Poznámky

`MaxFrameworkVersion`je volitelný prvek. Prvek `MaxFrameworkVersion` by měl být vynechán, pokud není vyžadován, aby nedošlo k neúmyslnému omezení podporovaného rozsahu verzí rozhraní .NET Framework pro šablonu. Měl by být také vynechán, pokud rozhraní .NET Framework není pro šablonu použitelné.

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

V tomto příkladu je maximální verze rozhraní .NET Framework, `MaxFrameworkVersion`která je vyžadována šablonou, reprezentovaná rozhraním 4.7.1. Projekt vytvořený pomocí této šablony může cílit na verze rozhraní .NET Framework až do verze 4.7.1.

## <a name="see-also"></a>Viz také

- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
