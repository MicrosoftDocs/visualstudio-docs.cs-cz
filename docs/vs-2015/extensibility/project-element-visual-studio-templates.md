---
title: Project – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07700501ae2a76337fed499aeb0a66b8b19dbeba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741128"
---
# <a name="project-element-visual-studio-templates"></a>Element projektu (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje soubory nebo adresáře přidat do projektu.  
  
 \<Vstemplate – >  
 \<TemplateContent – >  
 \<Project>  
  
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
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`File`|Požadovaný atribut.<br /><br /> Určuje název souboru projektu v souboru ZIP šablony.|  
|`ReplaceParameters`|Nepovinný atribut.<br /><br /> Logická hodnota určující, zda soubor projektu obsahuje hodnoty parametrů, které musí být nahrazen, když je projekt vytvořen z šablony. Výchozí hodnota je `false`.|  
|`TargetFileName`|Nepovinný atribut.<br /><br /> Určuje název souboru projektu, když je projekt vytvořen z šablony.|  
|`IgnoreProjectParameter`|Nepovinný atribut.<br /><br /> Určuje, zda by měl přidat projekt do aktuálního řešení. Pokud hodnota parametru vlastní, "$*myCustomParameter*$" existuje v nahrazení souboru parametrů je projekt vytvořen, ale nebyl přidán do aktuálně otevřeného řešení v rámci.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Složka](../extensibility/folder-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje složku, kterou chcete přidat do projektu.|  
|[ProjectItem –](../extensibility/projectitem-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje soubor a přidejte do projektu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateContent –](../extensibility/templatecontent-element-visual-studio-templates.md)|Požadovaný element.|  
  
## <a name="remarks"></a>Poznámky  
 `Project` je volitelný podřízený prvek `TemplateContent`.  
  
 `Project` Elementu je použita zadat projekt a proto je platná pouze v šablonách projektů.  
  
 `Project` elementy mohou mít [složky](../extensibility/folder-element-visual-studio-project-templates.md) podřízené prvky nebo [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) podřízené prvky, ale ne kombinace obou `Folder` a `ProjectItem` podřízené prvky.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky přejmenuje název souboru projektu na základě zadaného uživatelem, v názvu **nový projekt** dialogové okno. Použití `TargetFileName` atribut, pokud byste chtěli poskytnout alternativní název_souboru pro souborů projektu vytvořených šablonou.  
  
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
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [ProjectItem – Element (šablony projektů Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder – element (šablony projektů sady Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)

