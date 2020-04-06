---
title: Prvek projektu (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701994"
---
# <a name="project-element-visual-studio-templates"></a>Prvek projektu (šablony sady Visual Studio)
Určuje soubory nebo adresáře, které chcete přidat do projektu.

 \<VSTemplate \<> TemplateContent> \<project>

## <a name="syntax"></a>Syntaxe

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`File`|Požadovaný atribut.<br /><br /> Určuje název souboru projektu v souboru *ZIP* šablony.|
|`ReplaceParameters`|Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda soubor projektu obsahuje hodnoty parametrů, které musí být nahrazeny při vytvoření projektu ze šablony. Výchozí hodnota `false`je .|
|`TargetFileName`|Nepovinný atribut.<br /><br /> Určuje název souboru projektu při vytvoření projektu ze šablony.|
|`IgnoreProjectParameter`|Nepovinný atribut.<br /><br /> Určuje, zda má být projekt přidán do aktuálního řešení. Pokud hodnota vlastního parametru "$*myCustomParameter*$" existuje v souboru nahrazení parametru, projekt je vytvořen, ale není přidán jako součást aktuálně otevřeného řešení.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Složka](../extensibility/folder-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje složku, kterou chcete přidat do projektu.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje soubor, který má být přidejte do projektu.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Požadovaný element.|

## <a name="remarks"></a>Poznámky
 `Project`je volitelný podřízený `TemplateContent`prvek .

 Prvek `Project` se používá ke specifii projektu, a proto je platný pouze v šablonách projektu.

 `Project`elementy mohou mít [Folder](../extensibility/folder-element-visual-studio-project-templates.md) children elementy nebo [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) podřízené prvky, ale ne směs obou `Folder` a `ProjectItem` podřízených prvků.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automaticky přejmenuje název souboru projektu na základě názvu zadaného uživatelem v dialogovém okně **Nový projekt.** Atribut `TargetFileName` použijte, pokud chcete zadat alternativní název souboru pro soubory projektu vytvořené pomocí šablony.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu pro aplikaci.

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
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Element ProjectItem (šablony projektů sady Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Element složky (šablony projektů sady Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
