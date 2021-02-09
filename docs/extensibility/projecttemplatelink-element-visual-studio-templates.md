---
title: ProjectTemplateLink – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o <element> prvku a o tom, jak Určuje cestu k souboru. vstemplate jednoho projektu v šabloně více projektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dba5063080fb45c366e7a1b76461b0a0d8978f7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915153"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink – element (šablony sady Visual Studio)
Určuje cestu k souboru *. vstemplate* jednoho projektu v šabloně více projektů.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<ProjectTemplateLink>
ani \<VSTemplate>
 \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>
 \<ProjectTemplateLink>

## <a name="syntax"></a>Syntax

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`ProjectName`|Nepovinný atribut.<br /><br /> Určuje název pro každý projekt ve víceprojektové šabloně. Dialogové okno **Nový projekt** nemůže přiřadit názvy jednotlivým projektům.|
|`CopyParameters`|Umožňuje zkopírovat všechny proměnné z hlavní šablony skupiny do jednotlivých propojených šablon.<br /><br /> Parametry v propojených šablonách mají předponu `"$ext_*$"` . Například pokud v nadřazené šabloně skupiny má parametr `$projectname$` hodnotu **ExampleProject1**, když odkazovaná šablona získá své vypnutí, získá parametr `$ext_projectname$` , který je kopií `$projectname$` parametru z nadřazené šablony skupiny.<br /><br /> To umožňuje propojeným šablonám sdílet určité společné parametry, které stačí jednoduše vytvořit pouze v nadřazené šabloně skupiny.<br /><br /> Tento atribut je volitelný a automaticky se nastaví na výchozí hodnotu, `false` Pokud není zahrnutý.<br /><br /> Zavedeno ve Visual Studio 2013 Update 2. Odkaz na správnou verzi produktu naleznete v tématu [referenční sestavení Doručená v sadě Visual Studio 2013 SDK Update 2](/previous-versions/dn632168(v=vs.120)).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Určuje uspořádání a obsah víceprojektových šablon.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Seskupuje projekty do víceprojektových šablon.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Tento text určuje cestu k souboru *. vstemplate* šablony.

## <a name="remarks"></a>Poznámky
 Šablony vícenásobných projektů slouží jako kontejnery pro dva nebo více projektů. `ProjectTemplateLink`Element se používá k určení umístění souboru *. vstemplate* pro jeden z projektů v šabloně. Soubor *. vstemplate* šablony více projektů obsahuje jeden `ProjectTemplateLink` prvek pro každý projekt v šabloně. Další informace o šablonách více projektů naleznete v tématu [How to: Create Multi-Project Templates](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Příklad
 Tento příklad ukazuje jednoduchý soubor root *. vstemplate* pro více projektů. V tomto příkladu šablona obsahuje dva projekty `My Windows Application` a `My Class Library` . `ProjectName`Atribut na `ProjectTemplateLink` elementu nastaví název pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] přiřazení tohoto projektu. Pokud `ProjectName` atribut neexistuje, použije se jako název projektu název souboru *. vstemplate* .

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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Viz také
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postupy: vytváření šablon více projektů](../ide/how-to-create-multi-project-templates.md)