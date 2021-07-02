---
title: Přidání nebo úprava značek v šablonách projektů
description: Zjistěte, jak přidat nebo upravit značky v šablonách projektů v Visual Studio.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jmartens
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: ac4757464d720ca50632833b3911f0d594e1becb
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222978"
---
# <a name="add-tags-to-project-templates"></a>Přidání značek do šablon projektů

Od [verze Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) verze 16.1 Preview 2 můžete do šablon projektů přidat značky jazyka, platformy a typu projektu. 

Značky se používají na dvou místech v dialogovém **Project** nový název:

- Značky se zobrazí pod popisem šablony.

   ![Project šablony se značkami v dialogovém Project nový název](media/npd-item-with-template-tags.png)

- Značky umožňují prohledávat a filtrovat šablonu.

   ![Hledání a filtrování v dialogovém Project nový název](media/npd-search-and-filter.png)

Značky můžete přidat aktualizací souboru *XML .vstemplate.* Můžete použít buď značky šablon, které jsou integrované do Visual Studio, nebo vytvořit vlastní značky šablony. Značky šablony se zobrazí pouze v dialogovém Visual Studio 2019 **Nový Project** 2019. Značky šablon neovlivňuje, jak se šablona vykresluje v dřívějších verzích Visual Studio.

## <a name="add-or-edit-tags"></a>Přidání nebo úprava značek

Můžete chtít přidat nebo upravit značky v xml *.vstemplate* šablony projektu, když použijete jednu z následujících akcí:

* [Vytvořte novou šablonu projektu](how-to-create-project-templates.md) pomocí průvodce exportem šablony.
* [Aktualizujte existující šablonu projektu.](how-to-update-existing-templates.md)
* [Vytvořte novou šablonu projektu VSIX.](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="syntax"></a>Syntax

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atributy

V pokročilých uživatelských scénářích můžete použít následující volitelné atributy:

|Atribut|Popis|
|---------------|-----------------|
|`Package`|Identifikátor GUID, který Visual Studio ID balíčku.|
|`ID`|Určuje ID Visual Studio prostředku.|

Syntaxe:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Elementy

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Povinné) Zařazuje šablonu do kategorií a definuje způsob zobrazení v dialogovém **Project** nová položka nebo **v dialogovém** okně Přidat novou položku.|

## <a name="text-value"></a>Textová hodnota

Pokud atributy a nepou ítáte, vyžaduje `Package` se `ID` textová hodnota.

Text obsahuje název šablony.

## <a name="built-in-tags"></a>Předdefinné značky

Visual Studio nabízí seznam předdefinových značek. Když přidáte integrovanou značku, značka vykreslí lokalizovaný prostředek. 

Následující seznam obsahuje integrované značky, které jsou k dispozici v Visual Studio. Odpovídající hodnoty se zobrazují v závorkách.

| Značka jazyka | Značka platformy | Project typu |
| -- | -- | -- |
| C++ ( `cpp` ) | Android ( `android` ) | Cloud ( `cloud` ) |
| C# ( `csharp` ) | Azure ( `azure` ) | Konzola ( `console` ) |
| F# ( `fsharp` ) | iOS ( `ios` ) | Desktop ( `desktop` ) |
| Java ( `java` ) | Linux ( `linux` ) | Rozšíření ( `extension` ) |
| JavaScript (`javascript`) | macOS ( `macos` ) | Games ( `games` ) |
| Python ( `python` ) | tvOS ( `tvos` ) | IoT ( `iot` ) |
| Jazyk dotazu ( `querylanguage` ) | Windows ( `windows` ) | Knihovna ( `library` ) |
| TypeScript ( `typescript` ) | Xbox ( `xbox` ) | Machine Learning ( `machinelearning` ) |
| Visual Basic ( `visualbasic` ) | | Mobilní zařízení ( `mobile` ) |
| | | Office ( `office` ) |
| | | Jiné ( `other` ) |
| | | Služba ( `service` ) |
| | | Test ( `test` ) |
| | | UPW ( `uwp` ) |
| | | Web ( `web` ) |

## <a name="example"></a>Příklad

Následující příklad ukazuje metadata pro šablonu projektu pro aplikaci Visual C#:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
        <LanguageTag>csharp</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
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

- [Visual Studio schématu šablony](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](creating-project-and-item-templates.md)
- [Přizpůsobení šablon projektů a položek](customizing-project-and-item-templates.md)
- [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
