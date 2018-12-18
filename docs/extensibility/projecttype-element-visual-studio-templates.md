---
title: ProjectType – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14726d5338830eb4044d22778d886241cfd0cd83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921129"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType – element (šablony sady Visual Studio)
Rozděluje šablonu projektu tak, aby se objevila pod zadané skupiny v rámci **nový projekt** nebo **přidat novou položku** dialogové okno.  
  
> [!WARNING]
>  Šablony projektů jsou podporovány pro C++ v sadě Visual Studio 2012. Nejsou podporovány pro C++ v sadě Visual Studio 2010 a starší verze.  
  
 \<Vstemplate – >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateData –](../extensibility/templatedata-element-visual-studio-templates.md)|Rozděluje šablonu a definuje, jak se zobrazuje **nový projekt** nebo **přidat novou položku** dialogové okno.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 Tato hodnota určuje typ projektu šablony vytvoří a musí obsahovat jednu z následujících hodnot:  
  
- `CSharp`: Určuje, že šablona vytváří [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekt nebo položku.  
  
- `VisualBasic`: Určuje, že šablona vytváří [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekt nebo položku.  
  
- `Web`: Určuje, že šablona vytvoří webový projekt nebo položku. Pokud `ProjectType` prvek obsahuje tuto hodnotu, není definovaný jazyk projektu nebo položky v [ProjectSubType – Element (šablony sady Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Poznámky  
 `ProjectType` je vyžadovaný podřízený prvek `TemplateData`.  
  
 Hodnota `ProjectType` element určuje, kde se tato šablona je umístěná v **nový projekt** nebo **přidat novou položku** dialogové okno. Například šablonu s `ProjectType` hodnotu `CSharp` se zobrazí v části **Visual C#** uzlu **nový projekt** dialogové okno.  
  
 Podtyp šablony se dá nastavit pomocí [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) elementu.  
  
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
 [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType – element (šablony sady Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)