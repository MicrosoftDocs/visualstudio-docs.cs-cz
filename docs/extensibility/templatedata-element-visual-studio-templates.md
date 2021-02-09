---
title: TemplateData – element (šablony sady Visual Studio) | Microsoft Docs
description: Přečtěte si o prvku TemplateData a o tom, jak tato šablona kategorizuje, a definuje, jak se zobrazí v dialogovém okně Nový projekt nebo přidat novou položku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 423bcc7b3d902488f268b2d0706cb5126125f37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895385"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData – element (šablony sady Visual Studio)
Zařadí šablonu do kategorie a definuje, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** .

 \<VSTemplate> \<TemplateData>

## <a name="syntax"></a>Syntax

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené elementy

| Element | Popis |
| - | - |
| [Název](../extensibility/name-element-visual-studio-templates.md) | Požadovaný element.<br /><br /> Určuje název šablony, jak je zobrazen v dialogovém okně **Nový projekt** nebo **Přidat novou položku** . |
| [Popis](../extensibility/description-element-visual-studio-templates.md) | Požadovaný element.<br /><br /> Určuje popis šablony tak, jak se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** . |
| [Ikona](../extensibility/icon-element-visual-studio-templates.md) | Požadovaný element.<br /><br /> Určuje cestu a název souboru obrázku, který slouží jako ikona, která se zobrazí v dialogovém okně **Nový projekt** nebo **Přidat novou položku** pro šablonu. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Požadovaný element.<br /><br /> Kategorizuje šablonu projektu tak, aby se zobrazila pod určenou skupinou v dialogovém okně **Nový projekt** . |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Klasifikuje šablonu projektu tak, aby se zobrazila pod určenou podkategorií v dialogovém okně **Nový projekt** . |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje ID šablony. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje ID skupiny šablon. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje hodnotu, která se používá k uspořádání šablony, mezi ostatními šablonami ve stejné kategorii, jak se zobrazuje v dialogovém okně **Nový projekt** nebo **Přidat novou položku** . |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda je pro instanci projektu vytvořena nadřazená složka. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje název, který bude systém projektu sady Visual Studio generovat pro projekt nebo položku při jejím vytvoření. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda systém projektu sady Visual Studio vygeneruje výchozí název pro projekt nebo položku při jejím vytvoření. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda lze projekt vytvořit jako dočasný projekt (pouze Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda je v dialogovém okně **Nový projekt** k dispozici tlačítko **Procházet** , aby uživatelé mohli snadno upravit výchozí adresář, do kterého je uložen nový projekt. |
| [Skrytý](../extensibility/hidden-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda se šablona zobrazuje v dialogovém okně **Nový projekt** nebo **Přidat novou položku** . |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje počet nadřazených kategorií, které budou zobrazovat šablonu v dialogovém okně **Nový projekt** . |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Volitelný element. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Volitelný element.<br /><br /> Určuje, zda je textové pole **umístění** v dialogovém okně **Nový projekt** buď povoleno, zakázáno nebo skryto pro šablonu projektu. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Tento prvek použijte v případě, že šablona podporuje pouze konkrétní minimální verzi a novější verze .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda šablona podporuje stránku předlohy pro webové projekty. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda šablona podporuje oddělení kódu, nebo model stránky na pozadí pro webové projekty. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda je šablona identická pro více jazyků a zda je možnost **jazyk** k dispozici v dialogovém okně **Nový projekt** . |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje platformu, na kterou se šablona projektu zaměřuje. Tento prvek určuje, že se šablona projektu používá k vytváření [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikací. |

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Obsahuje všechna metadata pro šablonu projektu, šablonu položky nebo Startovní sadu.|

## <a name="remarks"></a>Poznámky
 `TemplateData` je vyžadovaný element.

 Pokud nezahrnete volitelný prvek, je použita výchozí hodnota tohoto prvku.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu projektu pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikaci.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
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
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
