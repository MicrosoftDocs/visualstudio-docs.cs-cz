---
title: TemplateContent – element (šablony sady Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe87bff62c1044442b579664fb789f918a2e6c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186464"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent – element (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje obsah šablony.  
  
 \<VSTemplate>  
 \<TemplateContent>  
  
## <a name="syntax"></a>Syntax  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Určuje, zda se má řešení sestavit při vytvoření projektu ze šablony.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje uspořádání a obsah víceprojektových šablon.|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje soubory nebo adresáře, které se mají přidat do projektu.|  
|[Odkazy](../extensibility/references-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje odkazy na sestavení požadované pro šablonu položky.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Volitelný element.<br /><br /> Určuje soubor obsažený v šabloně.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje všechny vlastní parametry, které mají být použity při vytvoření projektu nebo položky ze šablony.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Obsahuje všechna metadata pro šablonu projektu, šablonu položky nebo Startovní sadu.|  
  
## <a name="remarks"></a>Poznámky  
 `TemplateContent` je vyžadovaný element.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metadata pro šablonu projektu pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikaci.  
  
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
 [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
