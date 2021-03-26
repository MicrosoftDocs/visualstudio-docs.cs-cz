---
title: Project – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku projektu a o tom, jak Určuje soubory nebo adresáře, které mají být přidány do projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52bfb5f65aa9d42c46eece619a21152c51e8fa28
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068801"
---
# <a name="project-element-visual-studio-templates"></a>Project – element (šablony sady Visual Studio)
Určuje soubory nebo adresáře, které se mají přidat do projektu.

 \<VSTemplate> \<TemplateContent>
 \<Project>

## <a name="syntax"></a>Syntax

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`File`|Požadovaný atribut.<br /><br /> Určuje název souboru projektu v souboru template *. zip* .|
|`ReplaceParameters`|Nepovinný atribut.<br /><br /> Logická hodnota určující, zda soubor projektu obsahuje hodnoty parametrů, které musí být nahrazeny při vytvoření projektu ze šablony. Výchozí hodnota je `false`.|
|`TargetFileName`|Nepovinný atribut.<br /><br /> Určuje název souboru projektu při vytvoření projektu ze šablony.|
|`IgnoreProjectParameter`|Nepovinný atribut.<br /><br /> Určuje, zda má být projekt přidán do aktuálního řešení. Pokud hodnota vlastního parametru, "$*myCustomParameter*$" existuje v souboru náhradního parametru, projekt se vytvoří, ale nepřidá se jako součást aktuálně otevřeného řešení.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Složka](../extensibility/folder-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje složku, která se má přidat do projektu.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje soubor, který se má přidat do projektu.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Požadovaný element.|

## <a name="remarks"></a>Poznámky
 `Project` je volitelný podřízený prvek elementu `TemplateContent` .

 `Project`Prvek slouží k zadání projektu, a proto je platný pouze v šablonách projektů.

 `Project` elementy mohou mít podřízené prvky [složky](../extensibility/folder-element-visual-studio-project-templates.md) nebo prvky [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) , ale ne kombinaci obou i `Folder` `ProjectItem` podřízených prvků.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky přejmenuje název souboru projektu na základě názvu zadaného uživatelem v dialogovém okně **Nový projekt** . Použijte `TargetFileName` atribut, pokud chcete zadat alternativní název souboru pro soubory projektu vytvořené pomocí šablony.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu projektu pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikaci.

```
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
            <ProjectItem>Form1.cs<ProjectItem>
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
- [ProjectItem – element (šablony projektů sady Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Folder – element (šablony projektů sady Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
