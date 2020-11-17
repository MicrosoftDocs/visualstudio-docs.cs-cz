---
title: CreateNewFolder – – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku CreateNewFolder – a o tom, jak určuje, zda se má ověřit, zda cílový adresář, kde má být projekt vytvořen, neexistuje.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 15633c2f701c813ca24c5484fd4108a86c57b05b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671570"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder – – element (šablony sady Visual Studio)
Určuje, zda se má ověřit, zda cílový adresář, kde má být projekt vytvořen, neexistuje. Pokud adresář existuje, lze pro projekt vytvořit nový adresář. Toto nastavení je obvykle přepsáno `NewProjectRequiresNewFolder(VsTemplate)` příznakem registru ( `HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>` ), který používají všechny běžné typy projektů k určení, zda vytvořit nový projekt v novém adresáři.

 \<VSTemplate> \<TemplateData>
 \<CreateNewFolder>

## <a name="syntax"></a>Syntax

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>Typ
 `Boolean`

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota
 Je vyžadována textová hodnota.

 Text musí být buď `true` nebo `false` , který označuje, jestli se má při vytvoření projektu ze šablony vytvořit nová složka kontejneru.

## <a name="remarks"></a>Poznámky
 `CreateNewFolder` je volitelný prvek. Výchozí hodnota je `true`.

 Hodnota zadaná v `CreateNewFolder` elementu je dodržena pouze v případě, že příslušný [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] systém projektu ho podporuje.

## <a name="example"></a>Příklad
 Následující příklad kódu určuje, že se při vytvoření projektu ze šablony nevytvoří nová složka.

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
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
