---
title: Project – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 464f6498ccf06f5087c0fa6b12a456082a36c2bd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639136"
---
# <a name="project-element-visual-studio-templates"></a>Project – element (šablony sady Visual Studio)
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
|`File`|Požadovaný atribut.<br /><br /> Určuje název souboru projektu v šabloně *ZIP* souboru.|  
|`ReplaceParameters`|Nepovinný atribut.<br /><br /> Logická hodnota určující, zda soubor projektu obsahuje hodnoty parametrů, které musí být nahrazen, když je projekt vytvořen z šablony. Výchozí hodnota je `false`.|  
|`TargetFileName`|Nepovinný atribut.<br /><br /> Určuje název souboru projektu, když je projekt vytvořen z šablony.|  
|`IgnoreProjectParameter`|Nepovinný atribut.<br /><br /> Určuje, zda by měl přidat projekt do aktuálního řešení. Pokud hodnota parametru vlastní, "$*myCustomParameter*$" existuje v nahrazení souboru parametrů je projekt vytvořen, ale nebyl přidán do aktuálně otevřeného řešení v rámci.|  
  
### <a name="child-elements"></a>Podřízené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Složka](../extensibility/folder-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje složku, kterou chcete přidat do projektu.|  
|[ProjectItem –](../extensibility/projectitem-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje soubor a přidejte do projektu.|  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateContent –](../extensibility/templatecontent-element-visual-studio-templates.md)|Požadovaný element.|  
  
## <a name="remarks"></a>Poznámky  
 `Project` je volitelný podřízený prvek `TemplateContent`.  
  
 `Project` Elementu je použita zadat projekt a proto je platná pouze v šablonách projektů.  
  
 `Project` elementy mohou mít [složky](../extensibility/folder-element-visual-studio-project-templates.md) podřízené prvky nebo [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) podřízené prvky, ale ne kombinace obou `Folder` a `ProjectItem` podřízené prvky.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky přejmenuje název souboru projektu na základě zadaného uživatelem, v názvu **nový projekt** dialogové okno. Použití `TargetFileName` atribut, pokud byste chtěli poskytnout alternativní název_souboru pro souborů projektu vytvořených šablonou.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metadata pro šablona projektu pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikace.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [ProjectItem – element (šablony projektů Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder – element (šablony projektů Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)