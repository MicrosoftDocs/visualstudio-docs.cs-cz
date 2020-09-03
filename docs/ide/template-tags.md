---
title: Přidání nebo úprava značek v šablonách projektů
description: Naučte se přidávat nebo upravovat značky v šablonách projektů v aplikaci Visual Studio.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 37a1965712920420bdc4d784a003dbfbd2f2167a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85285215"
---
# <a name="add-tags-to-project-templates"></a>Přidání značek do šablon projektů

Počínaje verzí [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) verze 16,1 Preview 2 můžete do šablon projektu přidat značky jazyka, platformy a typu projektu. 

Značky se používají na dvou místech v dialogovém okně **Nový projekt** :

- V popisu šablony se zobrazí značky.

   ![Šablona projektu s značkami v dialogovém okně Nový projekt](media/npd-item-with-template-tags.png)

- Značky umožňují vyhledávat a filtrovat šablonu.

   ![Hledání a filtrování v dialogovém okně Nový projekt](media/npd-search-and-filter.png)

Značky lze přidat aktualizací souboru XML *. vstemplate* . Můžete buď použít Tagy šablony, které jsou součástí sady Visual Studio, nebo vytvořit vlastní značky šablony. Značky šablony se zobrazí pouze v dialogovém okně **Nový projekt** sady Visual Studio 2019. Značky šablony nemají vliv na to, jak šablona vykreslí v dřívějších verzích sady Visual Studio.

## <a name="add-or-edit-tags"></a>Přidat nebo upravit značky

Pokud provedete jednu z následujících akcí, můžete přidat nebo upravit značky v souboru XML šablony projektu *. vstemplate* :

* [Vytvořte novou šablonu projektu](how-to-create-project-templates.md) pomocí Průvodce exportem šablony.
* [Aktualizujte stávající šablonu projektu](how-to-update-existing-templates.md).
* [Vytvořte novou šablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="syntax"></a>Syntax

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atributy

V pokročilých scénářích uživatelů můžete použít následující volitelné atributy:

|Atribut|Popis|
|---------------|-----------------|
|`Package`|Identifikátor GUID, který určuje ID balíčku sady Visual Studio.|
|`ID`|Určuje ID prostředku sady Visual Studio.|

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Požadovanou Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo v dialogovém okně **Přidat novou položku** .|

## <a name="text-value"></a>Textová hodnota

Textová hodnota je povinná, pokud nepoužijete `Package` `ID` atributy a.

Text poskytuje název šablony.

## <a name="built-in-tags"></a>Předdefinované značky

Visual Studio nabízí seznam předdefinovaných značek. Když přidáte vestavěnou značku, značka vykresluje lokalizovaný prostředek. 

Následující seznam obsahuje předdefinované značky, které jsou k dispozici v aplikaci Visual Studio. Odpovídající hodnoty jsou uvedeny v závorkách.

| Značka jazyka | Značka platformy | Značka typu projektu |
| -- | -- | -- |
| C++ ( `cpp` ) | Android ( `android` ) | Cloud ( `cloud` ) |
| C# ( `csharp` ) | Azure ( `azure` ) | Konzola ( `console` ) |
| F # ( `fsharp` ) | iOS ( `ios` ) | Plocha ( `desktop` ) |
| Java ( `java` ) | Linux ( `linux` ) | Rozšíření ( `extension` ) |
| JavaScript ( `javascript` ) | macOS ( `macos` ) | Hry ( `games` ) |
| Python ( `python` ) | tvOS ( `tvos` ) | IoT ( `iot` ) |
| Dotaz Languate ( `querylanguage` ) | Windows ( `windows` ) | Knihovna ( `library` ) |
| TypeScript ( `typescript` ) | Xbox ( `xbox` ) | Machine Learning ( `machinelearning` ) |
| Visual Basic ( `visualbasic` ) | | Mobilní ( `mobile` ) |
| | | Office ( `office` ) |
| | | Jiný ( `other` ) |
| | | Služba ( `service` ) |
| | | Test ( `test` ) |
| | | UWP ( `uwp` ) |
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
        <LanguageTag>C#</LanguageTag>
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

- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](creating-project-and-item-templates.md)
- [Přizpůsobení šablon projektů a položek](customizing-project-and-item-templates.md)
- [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
