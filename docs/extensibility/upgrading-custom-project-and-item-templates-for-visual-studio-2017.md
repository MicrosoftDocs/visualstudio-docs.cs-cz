---
title: Upgrade vlastních šablon projektů a položek pro Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698848"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Upgrade vlastních šablony projektů a položek pro Visual Studio 2017

Počínaje verzí sady Visual Studio 2017 aplikace Visual Studio zjišťuje šablony projektů a položek, které byly nainstalovány pomocí souboru. VSIX nebo. msi, jiným způsobem jako předchozí verze sady Visual Studio. Pokud vlastníte rozšíření, která používají vlastní šablony projektu nebo položky, je nutné aktualizovat rozšíření. Tento článek vysvětluje, co je potřeba udělat.

Tato změna se týká pouze sady Visual Studio 2017. Nemá vliv na předchozí verze sady Visual Studio.

Pokud chcete vytvořit šablonu projektu nebo položky jako součást rozšíření VSIX, přečtěte si téma [vytváření vlastních šablon projektů a položek](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Kontrola šablon

V předchozích verzích sady Visual Studio, **devenv/Setup** nebo **devenv/installvstemplates** kontrolovala místní disk a nalezl šablony projektů a položek. Počínaje verzí Visual Studio 2017 se kontrola provádí jenom pro umístění na úrovni uživatele. Výchozí umístění na úrovni uživatele je **%USERPROFILE%\Documents \\<Visual Studio verze \> \templates \\ **. Toto umístění se používá pro šablony generované šablonami **Project**  >  **exportu projektu...** , pokud je v průvodci vybraná možnost **automaticky importovat šablonu do sady Visual Studio** .

U ostatních (neuživatelových) umístění musíte zahrnout soubor manifestu (. vstman), který určuje umístění a další vlastnosti šablony. Soubor. vstman je vygenerován společně se souborem. vstemplate použitým pro šablony. Pokud nainstalujete rozšíření pomocí souboru. vsix, můžete to provést tak, že znovu zkompilujete rozšíření v aplikaci Visual Studio 2017. Pokud ale použijete soubor. msi, musíte provést změny ručně. Seznam toho, co je potřeba udělat k provedení těchto změn, najdete v tématu  **upgrade pro rozšíření nainstalovaná s nástrojem. MSI** později na této stránce.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Postup aktualizace rozšíření VSIX pomocí šablon projektů nebo položek

1. Otevřete řešení v aplikaci Visual Studio 2017. Zobrazí se výzva k upgradu kódu. Klikněte na **OK**.

2. Po dokončení upgradu bude pravděpodobně nutné změnit verzi cíle instalace. V projektu VSIX otevřete soubor source. extension. vsixmanifest a vyberte kartu **instalovat cíle** . Pokud je v poli **rozsah verzí** **[14,0]**, klikněte na **Upravit** a změňte ji tak, aby zahrnovala Visual Studio 2017. Můžete ji například nastavit na **[14.0, 15.0]** pro instalaci rozšíření do sady visual Studio 2015 nebo visual Studio 2017 nebo na **[15,0]** a nainstalovat jej pouze do sady Visual Studio 2017.

3. Zkompilujte kód znovu.

4. Zavřete Visual Studio.

5. Nainstalujte VSIX.

6. Aktualizaci můžete otestovat následujícím způsobem:

    1. Změna prohledávání souborů je aktivována následujícím klíčem registru:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg: 32**

    2. Po přidání klíče spusťte **devenv/installvstemplates**.

    3. Znovu otevřete Visual Studio. Měli byste najít šablonu v očekávaném umístění.

    > [!NOTE]
    > Šablony projektů rozšiřitelnosti sady Visual Studio nejsou k dispozici, pokud je přítomen klíč registru. Je nutné odstranit klíč registru (a znovu spustit **devenv/installvstemplates**), aby je bylo možné použít.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Další doporučení pro nasazení šablon projektů a položek

- Vyhněte se použití souborů šablony zip. Aby bylo možné načíst prostředky a obsah, je nutné dekomprimovat soubory šablon zip, aby se daly costlier použít. Místo toho byste měli nasadit šablony projektů a položek jako samostatné soubory v jejich vlastním adresáři, aby se urychlila inicializace šablony. V případě rozšíření VSIX budou úkoly sestavení sady SDK při vytváření souboru VSIX automaticky rozbalit všechny šablony zip.

- Nepoužívejte položky ID balíčku/prostředku pro název šablony, popis, ikonu nebo náhled, aby nedocházelo k zbytečnému načítání sestavení prostředků během zjišťování šablon. Místo toho můžete použít lokalizované manifesty k vytvoření položky šablony pro každé národní prostředí, které používá lokalizované názvy nebo vlastnosti.

- Pokud patříte mezi šablony jako položky souborů, generování manifestu vám nemusí poskytnout očekávané výsledky. V takovém případě budete muset přidat do projektu VSIX ručně generovaný manifest.

## <a name="file-changes-in-project-and-item-templates"></a>Změny souborů v šablonách projektů a položek
Zobrazujeme body rozdílu mezi verzemi šablon sady Visual Studio 2015 a Visual Studio 2017, aby bylo možné nové soubory vytvořit správně.

 Zde je výchozí soubor Project. vstemplate vytvořený v rámci sady Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Zde je soubor. vstman (můžete ho najít v adresáři manifestu VSIX projektu), který je výsledkem nového sestavení projektu VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Informace poskytnuté prvkem [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) zůstávají stejné. **\<VSTemplateContainer>** Prvek odkazuje na soubor. vstemplate pro přidruženou šablonu.

 Zde je výchozí soubor Item. vstemplate vytvořený v rámci sady Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Zde je soubor. vstman (můžete ho najít v adresáři manifestu VSIX projektu), který je výsledkem nového sestavení projektu VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 Informace poskytnuté **\<TemplateData>** elementem zůstávají stejné. **\<VSTemplateContainer>** Element odkazuje na soubor. vstemplate pro přidruženou šablonu.

 Další informace o různých prvcích souboru. vstman naleznete v tématu [reference schématu manifestu šablony sady Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrady pro rozšíření nainstalovaná pomocí. SOUBOR

Některá rozšíření založená na MSI nasazují šablony do společných umístění šablon, například do následujících adresářů:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<rozšíření \> \\<Project/ItemTemplates\>**

Pokud rozšíření provede nasazení založené na MSI, budete muset vygenerovat manifest šablony ručně a ujistit se, že je součástí nastavení rozšíření. Porovnejte příklady. vstman uvedené výše a [referenční informace schématu manifestu šablony sady Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Vytvořte samostatné manifesty pro šablony projektů a položek a měly by odkazovat na kořenový adresář šablon, jak je uvedeno výše. Vytvořte jeden manifest podle rozšíření a národního prostředí.

## <a name="see-also"></a>Viz také

- [Řešení potíží se zjišťováním šablon](troubleshooting-template-discovery.md)
- [Vytváření vlastních šablon projektů a položek](creating-custom-project-and-item-templates.md)
