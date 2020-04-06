---
title: Vytvořit prvek newfolder (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 860f4df3e69a568a3e391da4d7437d9a5fd83f15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739680"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>Element CreateNewFolder (šablony sady Visual Studio)
Určuje, zda má být kontrolován cílový adresář, ve kterém má být projekt vytvořen, neexistuje. Pokud adresář existuje, lze pro projekt vytvořit nový adresář. Toto nastavení je obvykle `NewProjectRequiresNewFolder(VsTemplate)` přepsáno`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`příznakem registru ( ), který používají všechny běžné typy projektů k určení, zda chcete vytvořit nový projekt v novém adresáři.

 \<VSTemplate \<> TemplateData> \<CreateNewFolder>

## <a name="syntax"></a>Syntaxe

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>Typ
 `Boolean`

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být `true` `false`buď nebo , označující, zda má být vytvořena nová složka kontejneru při vytvoření projektu ze šablony.

## <a name="remarks"></a>Poznámky
 `CreateNewFolder`je volitelný prvek. Výchozí hodnota je `true`.

 Hodnota zadaná `CreateNewFolder` v prvku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je dodržena pouze v případě, že základní systém projektu ji podporuje.

## <a name="example"></a>Příklad
 Následující příklad kódu určuje, že při vytvoření projektu ze šablony nemá být vytvořena nová složka.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
