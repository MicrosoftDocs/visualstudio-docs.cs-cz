---
title: 'Postupy: vytváření šablon více projektů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1de155b71e82bb7561030cae2e1d0d4d777c9586
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668064"
---
# <a name="how-to-create-multi-project-templates"></a>Postupy: Vytváření šablon vícenásobného projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablony vícenásobných projektů slouží jako kontejnery pro dva nebo více projektů. Při vytvoření projektu založeného na šabloně více projektů v dialogovém okně **Nový projekt** jsou všechny projekty v šabloně přidány do řešení.

 Šablona více projektů musí zahrnovat následující položky, které jsou komprimovány do souboru. zip:

- Kořenový soubor. vstemplate pro celou šablonu více projektů. Tento kořenový soubor. vstemplate obsahuje metadata, která se zobrazí v dialogovém okně **Nový projekt** , a určuje, kde najít soubory. vstemplate pro projekty v této šabloně. Tento soubor se musí nacházet v kořenovém adresáři souboru. zip.

- Jedna nebo více složek, které obsahují soubory, které jsou požadovány pro úplnou šablonu projektu. To zahrnuje všechny soubory kódu projektu a také soubor. vstemplate pro projekt.

  Například soubor. zip šablony pro více projektů, který má dva projekty, může obsahovat následující soubory a adresáře:

  MultiProjectTemplate. vstemplate

  \Project1\Project1.vstemplate

  \Project1\Project1.vbproj

  \Project1\Class.vb

  \Project2\Project2.vstemplate

  \Project2\Project2.vbproj

  \Project2\Class.vb

  Kořenový soubor. vstemplate pro šablonu s více projekty se liší od šablony jednoho projektu následujícími způsoby:

- Atribut `Type` elementu `VSTemplate` obsahuje hodnotu `ProjectGroup`. Příklad:

  ```
  <VSTemplate Version="2.0.0" Type="ProjectGroup"
      xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
  ```

- Element `TemplateContent` obsahuje prvek `ProjectCollection`, který obsahuje jeden nebo více `ProjectTemplateLink` prvků, které definují cesty k souborům. vstemplate zahrnutých projektů. Příklad:

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

  Šablony více projektů se také chovají jinak než normální šablony. Šablony více projektů mají následující jedinečné charakteristiky:

- Jednotlivé projekty v šabloně více projektů nelze přiřadit názvy pomocí dialogového okna **Nový projekt** . Místo toho použijte atribut `ProjectName` u elementu `ProjectTemplateLink` k určení názvu pro každý projekt. Další informace najdete v prvním příkladu v následující části.

- Šablony více projektů mohou obsahovat projekty napsané v různých jazycích, ale celou samotnou šablonu lze umístit pouze do jedné kategorie pomocí elementu `ProjectType`.

### <a name="to-create-a-multi-project-template"></a>Vytvoření šablony s více projekty

1. Vytvořte projekty, které chcete zahrnout do šablony více projektů.

2. Vytvořte soubory. vstemplate pro každý projekt. Další informace naleznete v tématu [How to: Create Project Templates](../ide/how-to-create-project-templates.md).

3. Vytvořte root. vstemplate soubor, který obsahuje metadata pro šablonu více projektů. Další informace najdete v prvním příkladu v následující části.

4. Vyberte soubory a složky, které chcete zahrnout do šablony, klikněte pravým tlačítkem myši na výběr, klikněte na **Odeslat do**a pak klikněte na **komprimovanou složku (ZIP)** . Soubory a složky jsou komprimovány do souboru ZIP.

5. Soubor šablony. zip vložte do adresáře šablon projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Ve výchozím nastavení je tento adresář \My Documents\Visual Studio *verze*\Templates\ProjectTemplates \\.

## <a name="example"></a>Příklad
 Tento příklad ukazuje základní soubor. vstemplate root více projektů. V tomto příkladu šablona obsahuje dva projekty `My Windows Application` a `My Class Library`. Atribut `ProjectName` u elementu `ProjectTemplateLink` nastaví název [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k přiřazení tohoto projektu. Pokud atribut `ProjectName` neexistuje, název souboru. vstemplate slouží jako název projektu.

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
 V tomto příkladu se používá element `SolutionFolder` k rozdělení projektů do dvou skupin, `Math Classes` a `Graphics Classes`. Šablona obsahuje čtyři projekty, z nichž dva jsou umístěny do každé složky řešení.

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
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md) [schéma šablon sady Visual Studio referenční](../extensibility/visual-studio-template-schema-reference.md) informace [o tom, jak vytvořit šablony projektů](../ide/how-to-create-project-templates.md) [Referenční schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md) [SolutionFolder – element (šablony sady Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md) [ ProjectTemplateLink – element (šablony sady Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
