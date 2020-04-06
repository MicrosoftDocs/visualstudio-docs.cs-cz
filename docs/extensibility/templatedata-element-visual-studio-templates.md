---
title: Element TemplateData (šablony sady Visual Studio) | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699194"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData – element (šablony sady Visual Studio)
Zařazuje šablonu do kategorií a definuje, jak se zobrazí v dialogovém **okně Nový projekt** nebo Přidat novou **položku.**

 \<> VSTemplate> \<TemplateData

## <a name="syntax"></a>Syntaxe

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
 Žádné.

### <a name="child-elements"></a>Podřízené elementy

| Element | Popis |
| - | - |
| [Název](../extensibility/name-element-visual-studio-templates.md) | Požadovaný element.<br /><br /> Určuje název šablony tak, jak se zobrazuje v dialogovém **okně Nový projekt** nebo Přidat novou **položku.** |
| [Popis](../extensibility/description-element-visual-studio-templates.md) | Požadovaný element.<br /><br /> Určuje popis šablony tak, jak se zobrazuje v dialogovém **okně Nový projekt** nebo Přidat novou **položku.** |
| [Ikona:](../extensibility/icon-element-visual-studio-templates.md) | Požadovaný element.<br /><br /> Určuje cestu a název souboru obrázku, který slouží jako ikona, která se zobrazí v dialogovém okně **Nový projekt** nebo Přidat **novou položku** pro šablonu. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Požadovaný element.<br /><br /> Zařadí šablonu projektu tak, aby se zobrazila pod zadanou skupinou v dialogovém okně **Nový projekt.** |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Klasifikuje šablonu projektu tak, aby se zobrazila pod zadanou podkategorií v dialogovém okně **Nový projekt.** |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje ID šablony. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje ID skupiny šablon. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje hodnotu, která se používá k uspořádání šablony, mimo jiné šablony ve stejné kategorii, jak se zobrazí v dialogovém okně **Nový projekt** nebo Přidat **novou položku.** |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda je při vytváření instancí projektu vytvořena obsahující složka. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje název, který bude systém projektu sady Visual Studio generovat pro projekt nebo položku při jeho vytvoření. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda systém projektu sady Visual Studio vygeneruje při vytvoření výchozí název projektu nebo položky. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda lze projekt vytvořit jako dočasný projekt (pouze Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda je tlačítko **Procházet** k dispozici v dialogovém okně **Nový projekt,** aby uživatelé mohli snadno upravit výchozí adresář, ve kterém je uložen nový projekt. |
| [Skrytý](../extensibility/hidden-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda se šablona zobrazí v dialogovém okně **Nový projekt** nebo Přidat **novou položku.** |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje počet nadřazených kategorií, které budou šablonu zobrazovat v dialogovém okně **Nový projekt.** |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Volitelný element. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Volitelný element.<br /><br /> Určuje, zda je textové pole **Umístění** v dialogovém okně **Nový projekt** pro šablonu projektu povoleno, zakázáno nebo skryto. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Tento prvek použijte, pokud šablona podporuje pouze určitou minimální verzi a případně novější verze rozhraní .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda šablona podporuje vzorovou stránku pro webové projekty. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda šablona podporuje oddělení kódu nebo model stránky s kódem na pozadí pro webové projekty. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje, zda je šablona shodná pro více jazyků a zda je možnost **Jazyk** dostupná v dialogovém okně **Nový projekt.** |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Volitelný element.<br /><br /> Určuje platformu, na kterou se šablona projektu zaměřuje. Tento prvek určuje, že šablona [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projektu se používá k vytváření aplikací. |

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Obsahuje všechna metadata pro šablonu projektu, šablonu položky nebo startovní soupravu.|

## <a name="remarks"></a>Poznámky
 `TemplateData`je povinný prvek.

 Pokud nezahrnete volitelný prvek, použije se výchozí hodnota pro tento prvek.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metadata pro šablonu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu pro aplikaci.

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
