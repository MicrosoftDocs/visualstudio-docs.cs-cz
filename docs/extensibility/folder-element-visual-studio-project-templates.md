---
title: Element složky (šablony projektů sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711470"
---
# <a name="folder-element-visual-studio-project-templates"></a>Element složky (šablony projektů sady Visual Studio)
Určuje složku, která bude přidána do projektu.

 \<VSTemplate \<> TemplateContent \< \<>> složky projektu>

## <a name="syntax"></a>Syntaxe

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Požadovaný atribut.<br /><br /> Název složky projektu.|
|`TargetFolderName`|Nepovinný atribut.<br /><br /> Určuje název, který má být složky přivytváření projektu ze šablony. Tento atribut je užitečný pro použití nahrazení parametrů k vytvoření názvu složky nebo pojmenování složky s mezinárodním řetězcem, který nelze použít přímo v souboru *ZIP.*|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|`Folder`|Určuje složku, kterou chcete přidat do projektu. `Folder`prvky mohou `Folder` obsahovat podřízené prvky.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Určuje soubor, který má být do projektu připojován.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Volitelný podřízený prvek [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Poznámky
 `Folder`je volitelné dítě `Project`.

 K uspořádání položek projektu do složek v šabloně můžete použít některou z následujících metod:

- Zahrňte složky do souboru *ZIP* šablony a přidejte je do projektu do souboru `ProjectItem` *.vstemplate* zadáním cesty k souboru v prvcích bez `Folder` prvků. Toto je doporučená metoda. Například:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Zahrňte složky do souboru *ZIP* šablony a přidejte je `Folder` do projektu v souboru *.vstemplate* s prvky. Například:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Nezahrnovat složky do souboru *.zip* šablony, ale přidejte složky pomocí `TargetFileName` atributu `ProjectItem` prvku. Například:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Příklad
 Následující příklad ilustruje metadata pro šablonu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu pro aplikaci systému Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Element ProjectItem (šablony položek sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
