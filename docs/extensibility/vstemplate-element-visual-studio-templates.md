---
title: VSTemplate – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o elementu VSTemplate a o tom, jak obsahuje všechna metadata o šabloně projektu, šabloně položky nebo úvodní sadě.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973e2ede7e97d1e7710e6571d520be3d8919b9d9
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903478"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate – element (šablony sady Visual Studio)
Obsahuje všechna metadata o šabloně projektu, šabloně položky nebo úvodní sadě.

## <a name="syntax"></a>Syntaxe

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

| Atribut | Popis |
|-----------| - |
| `Type` | Identifikuje šablonu jako šablonu projektu nebo šablonu položky. Tento atribut může mít hodnotu `Project` nebo `Item` . |
| `Version` | Určuje číslo verze šablony. Šablony v [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] a [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] mají `Version` hodnotu atributu `3.0.0` . |

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje data, která kategorizují šablonu, a definují, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje obsah šablony.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Volitelný element.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Volitelný element.|

### <a name="parent-elements"></a>Nadřazené prvky
 Žádné

## <a name="remarks"></a>Poznámky
 `VSTemplate`Element je kořenovým prvkem souborů *. vstemplate* .

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu projektu pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikaci.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
