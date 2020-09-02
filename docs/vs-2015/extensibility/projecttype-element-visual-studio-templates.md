---
title: ProjectType – element (šablony sady Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b01dd370fe5e3d7a5207363c5ab7ec4f2a0254c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64783049"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType – element (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kategorizuje šablonu projektu tak, aby se zobrazila pod určenou skupinou v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .  
  
> [!WARNING]
> Šablony projektů jsou podporovány pro jazyk C++ počínaje verzí Visual Studio 2012. V jazyce C++ v aplikaci Visual Studio 2010 a dřívějších verzích nejsou podporovány.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectType>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 Tato hodnota určuje typ projektu, který šablona vytvoří, a musí obsahovat jednu z následujících hodnot:  
  
- `CSharp`: Určuje, zda šablona vytvoří [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekt nebo položku.  
  
- `VisualBasic`: Určuje, zda šablona vytvoří [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekt nebo položku.  
  
- `Web`: Určuje, zda šablona vytvoří webový projekt nebo položku. Pokud `ProjectType` element obsahuje tuto hodnotu, jazyk projektu nebo položky je definován v [prvku ProjectSubType (šablony sady Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Poznámky  
 `ProjectType` je požadovaný podřízený prvek `TemplateData` .  
  
 Hodnota `ProjectType` elementu určuje, kde je šablona umístěna v dialogovém okně **Nový projekt** nebo **Přidat novou položku** . Například šablona s `ProjectType` hodnotou `CSharp` se zobrazí pod uzlem **Visual C#** v dialogovém okně **Nový projekt** .  
  
 Podtyp šablony lze zadat pomocí elementu [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) .  
  
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
 [ProjectSubType – element (šablony sady Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
