---
title: Element ProjectTemplateLink (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701821"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Element ProjectTemplateLink (šablony sady Visual Studio)
Určuje cestu k souboru *.vstemplate* jednoho projektu v šabloně více projektů.

 \<VSTemplate \<> \<TemplateContent> \<ProjectCollection> ProjectTemplateLink> -or- \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

## <a name="syntax"></a>Syntaxe

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`ProjectName`|Nepovinný atribut.<br /><br /> Určuje název pro každý projekt ve víceprojektové šabloně. Dialogové okno **Nový projekt** nemůže přiřadit názvy jednotlivým projektům.|
|`CopyParameters`|Umožňuje zkopírovat všechny proměnné z hlavní šablony skupiny do jednotlivých propojených šablon.<br /><br /> Parametry v propojených šablonách mají `"$ext_*$"`předponu . Pokud `$projectname$` má například parametr v šabloně nadřazené skupiny hodnotu **ExampleProject1**, když se `$ext_projectname$`propojená šablona `$projectname$` dostane do konce, získá parametr , což je kopie parametru ze šablony nadřazené skupiny.<br /><br /> To umožňuje propojeným šablonám sdílet určité společné parametry, které stačí jednoduše vytvořit pouze v nadřazené šabloně skupiny.<br /><br /> Tento atribut je volitelný a automaticky `false` se použije, pokud není zahrnut.<br /><br /> Představenv visual studio 2013 update 2. Chcete-li odkazovat na správnou verzi produktu, [přečtěte si odkaz na referenční sestavení dodaná v sadě Visual Studio 2013 SDK Update 2](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Určuje uspořádání a obsah víceprojektových šablon.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Seskupuje projekty do víceprojektových šablon.|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Tento text určuje cestu k souboru *.vstemplate* šablony.

## <a name="remarks"></a>Poznámky
 Šablony vícenásobných projektů slouží jako kontejnery pro dva nebo více projektů. Prvek `ProjectTemplateLink` se používá k určení umístění souboru *.vstemplate* pro jeden z projektů v šabloně. Soubor *.vstemplate* šablony více projektů obsahuje `ProjectTemplateLink` jeden prvek pro každý projekt v šabloně. Další informace o šablonách pro více projektů naleznete v [tématu How to: Create multi-project templates](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Příklad
 Tento příklad ukazuje jednoduchý kořenový soubor *.vstemplate* pro více projektů. V tomto příkladu šablona `My Windows Application` obsahuje `My Class Library`dva projekty a . Atribut `ProjectName` prvku `ProjectTemplateLink` nastaví název [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pro přiřazení tohoto projektu. Pokud `ProjectName` atribut neexistuje, název souboru *.vstemplate* se používá jako název projektu.

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
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Postup: Vytvoření šablon pro více projektů](../ide/how-to-create-multi-project-templates.md)
