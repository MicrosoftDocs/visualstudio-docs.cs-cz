---
title: Upgrade vlastních šablon projektů a položek pro Visual Studio 2017
titleSuffix: ''
description: Zjistěte, jak aktualizovat vlastní šablonu projektu a položky z předchozích verzí sady Visual Studio SDK pro použití s Visual Studio 2017 a novějšími verzemi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0d07af0a00ab840df8a9af437bcddc427f606948
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903057"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Upgrade vlastního šablony projektů a položek pro Visual Studio 2017

Od Visual Studio 2017 nástroj Visual Studio zjišťuje šablony projektů a položek, které byly nainstalovány pomocí souboru .vsix nebo .msi jiným způsobem než předchozí verze Visual Studio. Pokud vlastníte rozšíření, která používají vlastní šablony projektů nebo položek, musíte rozšíření aktualizovat. Tento článek vysvětluje, co musíte udělat.

Tato změna se týká pouze Visual Studio 2017. Nemá vliv na předchozí verze Visual Studio.

Pokud chcete vytvořit šablonu projektu nebo položky jako součást rozšíření VSIX, podívejte se na část Vytváření vlastních šablon projektů a [položek.](../extensibility/creating-custom-project-and-item-templates.md)

## <a name="template-scanning"></a>Kontrola šablon

V předchozích verzích Visual Studio soubor **devenv /setup** nebo **devenv /installvstemplates** naskenoval místní disk a našel šablony projektů a položek. Počínaje Visual Studio 2017 se kontrola provádí pouze pro umístění na úrovni uživatele. Výchozí umístění na úrovni uživatele je **%USERPROFILE%\Documents \\<Visual Studio \> \Templates. \\** Toto umístění se používá pro šablony vygenerované příkazem **Project**  >  **Export Templates...** (Exportovat šablony projektu), pokud je v průvodci vybraná možnost Automaticky importovat šablonu **do Visual Studio.**

Pro jiná umístění (bez uživatele) musíte zahrnout soubor manifest(.vstman), který určuje umístění a další charakteristiky šablony. Vygeneruje se soubor .vstman společně se souborem .vstemplate, který se používá pro šablony. Pokud rozšíření nainstalujete pomocí souboru .vsix, můžete to udělat tak, že rozšíření překompilíte v Visual Studio 2017. Pokud ale použijete .msi, musíte provést změny ručně. Seznam toho, co je potřeba udělat k provedení těchto změn, najdete v tématu  **Upgrady** pro rozšíření nainstalovaná s .MSIpozději na této stránce.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Aktualizace rozšíření VSIX pomocí šablon projektů nebo položek

1. Otevřete řešení v Visual Studio 2017. Zobrazí se vám dotaz, jestli chcete kód upgradovat. Klikněte na **OK**.

2. Po dokončení upgradu možná budete muset změnit verzi cíle instalace. V projektu VSIX otevřete soubor source.extension.vsixmanifest a vyberte **kartu Install Targets (Nainstalovat** cíle). Pokud je **pole Rozsah verzí** **[14.0],** klikněte na Upravit a změňte ho tak, aby zahrnoval Visual Studio 2017.  Můžete ho například nastavit na **[14.0,15.0]** a nainstalovat rozšíření na Visual Studio 2015 nebo Visual Studio 2017 nebo **na [15.0]** a nainstalovat ho jenom na Visual Studio 2017.

3. Znovu zkompilujte kód.

4. Zavřete Visual Studio.

5. Nainstalujte VSIX.

6. Aktualizaci můžete otestovat následujícím způsobem:

    1. Změnu kontroly souborů aktivuje následující klíč registru:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Po přidání klíče spusťte **příkaz devenv /installvstemplates**.

    3. Znovu otevřete Visual Studio. Šablonu byste měli najít v očekávaném umístění.

    > [!NOTE]
    > Šablony Visual Studio extensibility nejsou k dispozici, pokud je klíč registru k dispozici. Abyste ho měli používat, musíte odstranit klíč registru (a znovu spustit **příkaz devenv /installvstemplates).**

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Další doporučení pro nasazení šablon projektů a položek

- Nepoužívejte komprimované soubory šablon. Komprimované soubory šablon musí být nekomprimované, aby se načítaly prostředky a obsah, takže jejich použití bude nákladnější. Místo toho byste měli šablony projektů a položek nasadit jako jednotlivé soubory v jejich vlastním adresáři, abyste urychlili inicializaci šablony. V případě rozšíření VSIX úlohy sestavení sady SDK při vytváření souboru VSIX automaticky rozbalí všechny komprimované šablony.

- Nepoužívejte položky ID balíčku nebo prostředku pro název, popis, ikonu nebo náhled šablony, abyste se vyhnuli zbytečným načítáním sestavení prostředků během zjišťování šablony. Místo toho můžete použít lokalizované manifesty k vytvoření položky šablony pro každé národní prostředí, které používá lokalizované názvy nebo vlastnosti.

- Pokud do položek souboru zadáte šablony, generování manifestu vám nemusí poskytnout očekávané výsledky. V takovém případě budete muset do projektu VSIX přidat ručně vygenerovaný manifest.

## <a name="file-changes-in-project-and-item-templates"></a>Změny souborů v šablonách projektů a položek
Ukazujeme rozdíly mezi verzemi šablon Visual Studio 2015 a Visual Studio 2017, abyste mohli nové soubory vytvořit správně.

 Tady je výchozí soubor .vstemplate projektu vytvořený Visual Studio 2015:

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

 Tady je soubor .vstman (najdete ho v adresáři manifestu projektu VSIX), který byl výsledkem opětovného sestavení projektu VSIX:

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

 Informace, které poskytuje [element TemplateData,](../extensibility/templatedata-element-visual-studio-templates.md) zůstávají stejné. Element **\<VSTemplateContainer>** odkazuje na soubor .vstemplate pro přidruženou šablonu.

 Tady je výchozí soubor .vstemplate položky vytvořený Visual Studio 2015:

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

 Tady je soubor .vstman (najdete ho v adresáři manifestu projektu VSIX), který byl výsledkem opětovného sestavení projektu VSIX:

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

 Informace poskytované **\<TemplateData>** elementem zůstávají stejné. Element **\<VSTemplateContainer>** odkazuje na soubor .vstemplate pro přidruženou šablonu.

 Další informace o různých prvcích souboru .vstman najdete v tématu [Visual Studio schématu manifestu šablony.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrady pro rozšíření nainstalovaná s .MSI

Některá rozšíření založená na MSI nasadí šablony do běžných umístění šablon, jako jsou například následující adresáře:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<Project/ItemTemplates\>**

Pokud vaše rozšíření provádí nasazení založené na MSI, musíte manifest šablony vygenerovat ručně a zajistit, aby byl součástí nastavení rozšíření. Porovnejte výše uvedené příklady .vstman a referenční [Visual Studio schématu manifestu šablony.](../extensibility/visual-studio-template-manifest-schema-reference.md)

Vytvořte samostatné manifesty pro šablony projektů a položek a měly by odkazovat na kořenový adresář šablony, jak je uvedeno výše. Vytvořte jeden manifest pro jedno rozšíření a národní prostředí.

## <a name="see-also"></a>Viz také

- [Řešení potíží se zjišťováním šablon](troubleshooting-template-discovery.md)
- [Vytváření vlastních šablon projektů a položek](creating-custom-project-and-item-templates.md)
