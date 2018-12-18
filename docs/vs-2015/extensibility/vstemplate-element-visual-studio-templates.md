---
title: Vstemplate – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c497d264e9bf8b4f62559d9c4cfbb4fdb45cd7e4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758019"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate – element (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje všechna metadata o šablony projektu, šablonu položky nebo starter kit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Type`|Identifikuje šablony, která jako šablona projektu nebo šablony položky. Tento atribut může mít hodnotu `Project` nebo `Item`.|  
|`Version`|Určuje číslo verze šablony. Šablony v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] a [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] mít `Version` hodnotu atributu `3.0.0`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateData –](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje data, která rozděluje šablonu a definuje, jak se zobrazuje **nový projekt** nebo **přidat novou položku** dialogové okno.|  
|[TemplateContent –](../extensibility/templatecontent-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje obsah značek šablony.|  
|[WizardExtension –](../extensibility/wizardextension-element-visual-studio-templates.md)|Volitelný element.|  
|[WizardData –](../extensibility/wizarddata-element-visual-studio-templates.md)|Volitelný element.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
 Žádné  
  
## <a name="remarks"></a>Poznámky  
 `VSTemplate` Prvek je kořenovým prvkem souboru .vstemplate.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metadata pro šablona projektu pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikace.  
  
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
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)

