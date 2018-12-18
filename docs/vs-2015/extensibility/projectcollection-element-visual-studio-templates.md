---
title: Projectcollection – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f8b9ba0902b193bb630e99a7908818688c25fd1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778680"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection – element (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje uspořádání a obsah víceprojektových šablon.  
  
 \<Vstemplate – >  
 \<TemplateContent – >  
 \<Projectcollection – >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[ProjectTemplateLink –](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje projekt ve víceprojektové šabloně.|  
|[SolutionFolder –](../extensibility/solutionfolder-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Seskupuje projekty do víceprojektových šablon.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateContent –](../extensibility/templatecontent-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje obsah značek šablony.|  
  
## <a name="remarks"></a>Poznámky  
 Šablony vícenásobných projektů slouží jako kontejnery pro dva nebo více projektů. `ProjectCollection` Element slouží k určení projekty tak, aby obsahovala v šabloně. Další informace o víceprojektových šablonách naleznete v tématu [postupy: vytváření šablon vícenásobného projektu](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje jednoduchý kořenový soubor .vstemplate víceprojektové šablony, V tomto příkladu obsahuje šablona dva projekty `My Windows Application` a `My Class Library`. `ProjectName` Atribut na `ProjectTemplateLink` nastaví název elementu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tomuto projektu přiřadí. Pokud `ProjectName` atribut neexistuje, název souboru .vstemplate slouží jako název projektu.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Postupy: Vytváření šablon vícenásobného projektu](../ide/how-to-create-multi-project-templates.md)

