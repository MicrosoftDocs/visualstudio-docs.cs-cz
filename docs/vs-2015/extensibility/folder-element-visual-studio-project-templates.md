---
title: Folder – Element (šablony projektů Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81d2856bb7c261219fd69ec1e12db85cfb41d7e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787663"
---
# <a name="folder-element-visual-studio-project-templates"></a>Element složky (šablony projektů sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje složku, která se přidá do projektu.  
  
 \<Vstemplate – >  
 \<TemplateContent – >  
 \<Project>  
 \<Složky >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Požadovaný atribut.<br /><br /> Název složky projektu.|  
|`TargetFolderName`|Nepovinný atribut.<br /><br /> Určuje název složky při vytvoření projektu ze šablony. Tento atribut je užitečné pro použití k vytvoření názvu složky nahrazení parametru nebo pojmenování složky mezinárodní řetězcem, který nelze použít přímo v souboru ZIP.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`Folder`|Určuje složku, kterou chcete přidat do projektu. `Folder` prvky mohou obsahovat podřízené `Folder` elementy.|  
|[ProjectItem –](../extensibility/projectitem-element-visual-studio-item-templates.md)|Určuje soubor a přidejte do projektu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Volitelný podřízený prvek [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Poznámky  
 `Folder` je volitelný podřízený `Project`.  
  
 Uspořádat do složek v šabloně položky projektu můžete použít některý z následujících metod:  
  
-   Zahrnout složky do souboru ZIP šablony a přidat je do projektu v souboru .vstemplate tak, že zadáte cestu k souboru v `ProjectItem` elementy bez `Folder` elementy. Toto je doporučená metoda. Příklad:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Zahrnout složky soubor ZIP šablony a přidat je do projektu v souboru .vstemplate `Folder` elementy. Příklad:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Nezahrnují složek v souboru ZIP šablony, ale přidat pomocí složky `TargetFileName` atribut `ProjectItem` elementu. Příklad:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metadata pro šablona projektu pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikace Windows.  
  
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
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [ProjectItem – element (šablony sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)

