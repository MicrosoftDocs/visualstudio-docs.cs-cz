---
title: Přidání nebo úprava tagů v šablonách projektu
description: Přečtěte si, jak přidat nebo upravit značky v šablonách projektů ve Visual Studiu.
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
ms.openlocfilehash: 37fa5449847eb4c093475df11a07decb31168f1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189532"
---
# <a name="add-tags-to-project-templates"></a>Přidání značek do šablon projektů

Počínaje [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) verze 16.1 Náhled 2, můžete přidat jazyk, platformu a značky typu projektu do šablon projektu. 

Značky se používají na dvou místech v dialogovém okně **Nový projekt:**

- Značky se zobrazí pod popisem šablony.

   ![Šablona projektu se značkami v dialogovém okně Nový projekt](media/npd-item-with-template-tags.png)

- Značky umožňují prohledávat a filtrovat šablonu.

   ![Hledání a filtrování v dialogovém okně Nový projekt](media/npd-search-and-filter.png)

Značky můžete přidat aktualizací souboru XML *.vstemplate.* Můžete buď použít značky šablony, které jsou integrované do Sady Visual Studio, nebo vytvořit vlastní značky šablon. Značky šablony se zobrazí jenom v dialogovém okně **Nový projekt** Visual Studia 2019. Značky šablon nemají vliv na způsob vykreslení šablony v dřívějších verzích sady Visual Studio.

## <a name="add-or-edit-tags"></a>Přidání nebo úprava značek

Tagy v xml *šablony* projektu můžete přidat nebo upravit, když projdete některou z následujících akcí:

* [Vytvořte novou šablonu projektu](how-to-create-project-templates.md) pomocí Průvodce exportem šablony.
* [Aktualizujte existující šablonu projektu](how-to-update-existing-templates.md).
* [Vytvořte novou šablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="syntax"></a>Syntaxe

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atributy

V pokročilých uživatelských scénářích můžete použít následující volitelné atributy:

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

Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Povinné) Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo V dialogovém okně Přidat **novou položku.**|

## <a name="text-value"></a>Textová hodnota

Textová hodnota je vyžadována, pokud nepoužíváte atributy `Package` a. `ID`

Text obsahuje název šablony.

## <a name="built-in-tags"></a>Vestavěné značky

Visual Studio nabízí seznam předdefinovaných značek. Když přidáte vestavěnou značku, značka vykreslí lokalizovaný prostředek. 

V následujícím seznamu jsou uvedeny předdefinované značky, které jsou k dispozici v sadě Visual Studio. Odpovídající hodnoty jsou zobrazeny v závorce.

| Jazyk | Platforma | Typ projektu |
| -- | -- | -- |
| C++`cpp`( ) | Android`android`( ) | Mrak`cloud`( ) |
| C#`csharp`( ) | Azure`azure`( ) | Konzola`console`( ) |
| F#`fsharp`( ) | iOS`ios`( ) | Plocha`desktop`( ) |
| Java (`java`) | Linux`linux`( ) | Rozšíření (`extension`) |
| JavaScript`javascript`( ) | macOS`macos`( ) | Hry`games`( ) |
| Krajta (`python`) | tvOS`tvos`( ) | IoT`iot`( ) |
| Dotaz Languate`querylanguage`( ) | Okna`windows`( ) | Knihovna`library`( ) |
| TypeScript`typescript`( ) | Konzole`xbox`Xbox ( ) | Strojové`machinelearning`učení ( ) |
| Visual Basic`visualbasic`( ) | | Mobilní`mobile`( ) |
| | | Kancelář`office`( ) |
| | | Ostatní`other`( ) |
| | | Služba`service`( ) |
| | | Zkouška`test`( ) |
| | | Upw`uwp`( ) |
| | | Web`web`( ) |

## <a name="example"></a>Příklad

Následující příklad ukazuje metadata pro šablonu projektu pro aplikaci Visual C#:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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

- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytvoření šablon projektů a položek](creating-project-and-item-templates.md)
- [Přizpůsobení šablon projektů a položek](customizing-project-and-item-templates.md)
- [Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
