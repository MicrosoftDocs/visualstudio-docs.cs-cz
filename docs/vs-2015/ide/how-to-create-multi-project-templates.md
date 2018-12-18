---
title: 'Postupy: vytváření šablon vícenásobného projektu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eee52a4f77c7d3a07b237f01877c5cba30e53900
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950846"
---
# <a name="how-to-create-multi-project-templates"></a>Postupy: Vytváření šablon vícenásobného projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablony vícenásobných projektů slouží jako kontejnery pro dva nebo více projektů. Když na základě projektu ve víceprojektové šabloně je vytvořen z **nový projekt** dialogové okno, každý projekt v šabloně je přidán do řešení.  
  
 Víceprojektové šablony musí obsahovat následující položky zkomprimovány do souboru ZIP:  
  
- Kořenový soubor .vstemplate pro celý víceprojektové šabloně. Tento kořenový soubor .vstemplate obsahuje metadata, která **nový projekt** dialogové okno zobrazí a určuje, kde se mají hledat soubory .vstemplate pro projekty v této šabloně. Tento soubor musí být umístěn v kořenovém adresáři souboru ZIP.  
  
- Jednu nebo více složek, které obsahují soubory, které jsou požadovány pro dokončení šablony projektu. To zahrnuje všechny soubory kódu pro projekt a soubor .vstemplate pro projekt.  
  
  Soubor ZIP víceprojektové šablony, který má dva projekty může mít například následující soubory a adresáře:  
  
  MultiProjectTemplate.vstemplate  
  
  \Project1\Project1.vstemplate  
  
  \Project1\Project1.vbproj  
  
  \Project1\Class.vb  
  
  \Project2\Project2.vstemplate  
  
  \Project2\Project2.vbproj  
  
  \Project2\Class.vb  
  
  Kořenový soubor .vstemplate víceprojektové šablony se liší od jednoprojektové šablony následujícími způsoby:  
  
- `Type` Atribut `VSTemplate` element obsahuje hodnotu `ProjectGroup`. Příklad:  
  
  ```  
  <VSTemplate Version="2.0.0" Type="ProjectGroup"  
      xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
  ```  
  
- `TemplateContent` Obsahuje element `ProjectCollection` element, který má jeden nebo více `ProjectTemplateLink` prvky, které definují cesty souborech .vstemplate zahrnutých projektů. Příklad:  
  
  ```  
  <TemplateContent>  
      <ProjectCollection>  
          <ProjectTemplateLink>  
              Project1\Project1.vstemplate  
          </ProjectTemplateLink>  
          <ProjectTemplateLink>  
              Project2\Project2.vstemplate  
          </ProjectTemplateLink>  
      </ProjectCollection>  
  </TemplateContent>  
  ```  
  
  Víceprojektové šablony také chovat jinak než běžné šablony. Víceprojektové šablony mají následující jedinečné vlastnosti:  
  
- Jednotlivé projekty ve víceprojektové šabloně nelze přiřadit názvy **nový projekt** dialogové okno. Místo toho použijte `ProjectName` atribut na `ProjectTemplateLink` element zadejte název pro každý projekt. Další informace najdete v prvním příkladu v následující části.  
  
- Víceprojektové šablony může obsahovat projekty, které jsou napsány v různých jazycích, ale samotné šablony celý může být uvedena pouze v jedné kategorii pomocí `ProjectType` elementu.  
  
### <a name="to-create-a-multi-project-template"></a>K vytváření šablon vícenásobného projektu  
  
1.  Vytváření projektů zahrnout ve víceprojektové šabloně.  
  
2.  Vytvoří soubory .vstemplate pro každý projekt. Další informace najdete v tématu [postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md).  
  
3.  Vytvořte kořenový soubor .vstemplate, který obsahuje metadata pro víceprojektové šabloně. Další informace najdete v prvním příkladu v následující části.  
  
4.  Vyberte soubory a složky, které chcete do šablony zahrnout, klikněte pravým tlačítkem na výběr, klikněte na tlačítko **odeslat**a potom klikněte na tlačítko **komprimovaná složka (metoda ZIP)**. Komprimování souborů a složek do souboru .zip.  
  
5.  Vložit soubor ZIP šablony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] adresář šablon projektu. Ve výchozím nastavení je tento adresář Documents\Visual Studio *verze*\Templates\ProjectTemplates\\.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje základní víceprojektové kořenový soubor .vstemplate. V tomto příkladu obsahuje šablona dva projekty `My Windows Application` a `My Class Library`. `ProjectName` Atribut na `ProjectTemplateLink` nastaví název elementu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tomuto projektu přiřadí. Pokud `ProjectName` atribut neexistuje, název souboru .vstemplate slouží jako název projektu.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
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
  
## <a name="example"></a>Příklad  
 V tomto příkladu `SolutionFolder` elementu a rozdělit do dvou skupin, projekty `Math Classes` a `Graphics Classes`. Šablona obsahuje čtyři projekty, z nichž dva jsou umístěny ve složce jednotlivých řešení.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md)   
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder – Element (šablony sady Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink – element (šablony sady Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)



