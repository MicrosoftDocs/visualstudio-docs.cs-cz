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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698848"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Upgrade vlastních šablon projektů a položek pro Visual Studio 2017

Počínaje Visual Studio 2017, Visual Studio zjišťuje projekt a šablony položek, které byly nainstalovány .vsix nebo .msi jiným způsobem než předchozí verze sady Visual Studio. Pokud vlastníte rozšíření, která používají vlastní šablony projektu nebo položek, je třeba rozšíření aktualizovat. Tento článek vysvětluje, co musíte udělat.

Tato změna ovlivní pouze Visual Studio 2017. Nemá vliv na předchozí verze sady Visual Studio.

Pokud chcete vytvořit šablonu projektu nebo položky jako součást rozšíření VSIX, přečtěte si část [Vytvoření vlastních šablon projektu a položek](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Prohledávání šablon

V předchozích verzích sady Visual Studio **devenv /setup** nebo **devenv /installvstemplates** prohledali místní disk a našli šablony projektu a položek. Počínaje Visual Studio 2017 skenování se provádí pouze pro umístění na úrovni uživatele. Výchozí umístění na úrovni uživatele je **%USERPROFILE%\Documents\\<Visual Studio verze\>\Templates\\**. Toto umístění se používá pro šablony generované příkazem > **Šablony exportu** **projektu...** pokud je v průvodci vybrána možnost **Automaticky importovat šablonu do sady Visual Studio.**

Pro jiná umístění (bez uživatele) je nutné zahrnout soubor manifestu(.vstman), který určuje umístění a další charakteristiky šablony. Soubor .vstman je generován spolu se souborem .vstemplate používaným pro šablony. Pokud nainstalujete rozšíření pomocí .vsix, můžete to provést rekompilací rozšíření v Sadě Visual Studio 2017. Ale pokud používáte .msi, je třeba provést změny ručně. Seznam, co je třeba provést, naleznete v **tématu Inovace pro rozšíření nainstalovaná pomocí aplikace . MSI** dále na této stránce.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Jak aktualizovat rozšíření VSIX se šablonami projektu nebo položek

1. Otevřete řešení v Sadě Visual Studio 2017. Budete vyzváni k upgradu kódu. Klikněte na tlačítko **OK**.

2. Po dokončení upgradu bude pravděpodobně nutné změnit verzi cíle instalace. V projektu VSIX otevřete soubor source.extension.vsixmanifest a vyberte kartu **Instalovat cíle.** Pokud je pole **Rozsah verze** **[14.0]**, klikněte na **Upravit** a změňte ho tak, aby zahrnovalo Visual Studio 2017. Můžete ji například nastavit na **[14.0,15.0]** pro instalaci rozšíření do Visual Studia 2015 nebo Visual Studia 2017 nebo **[15.0]** a nainstalovat ho pouze do Visual Studia 2017.

3. Překompilujte kód.

4. Zavřete Visual Studio.

5. Nainstalujte VSIX.

6. Aktualizaci můžete otestovat následujícím způsobem:

    1. Změna skenování souborů je aktivována následujícím klíčem registru:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Po přidání klíče spusťte **devenv /installvstemplates**.

    3. Znovu otevřete visual studio. Šablonu byste měli najít v očekávaném umístění.

    > [!NOTE]
    > Šablony projektu rozšiřitelnostsady Visual Studio nejsou k dispozici, pokud je k dispozici klíč registru. Je nutné odstranit klíč registru (a znovu spustit **devenv /installvstemplates**) k jejich použití.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Další doporučení pro nasazení šablon projektů a položek

- Nepoužívejte soubory šablon zip. Zip šablony soubory musí být nekomprimované, aby se načíst zdroje a obsah, takže budou nákladnější k použití. Místo toho byste měli nasadit šablony projektů a položek jako jednotlivé soubory v rámci vlastního adresáře, abyste urychlili inicializaci šablony. Pro rozšíření VSIX úlohy sestavení sady SDK automaticky rozbalí všechny šablony zip při vytváření souboru VSIX.

- Nepoužívejte položky ID balíčku nebo prostředků pro název šablony, popis, ikonu nebo náhled, abyste se vyhnuli zbytečnému zatížení sestavení prostředků během zjišťování šablony. Místo toho můžete použít lokalizované manifesty k vytvoření položky šablony pro každé národní prostředí, které používá lokalizované názvy nebo vlastnosti.

- Pokud jste včetně šablony jako položky souboru, generování manifestu nemusí poskytnout očekávané výsledky. V takovém případě budete muset přidat ručně generovaný manifest do projektu VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Změny souborů v šablonách projektů a položek
Zobrazujeme body rozdílu mezi visual studio 2015 a Visual Studio 2017 verze souborů šablon, takže můžete vytvořit nové soubory správně.

 Tady je výchozí soubor .vstemplate vytvořený visual studio 2015:

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

 Zde je soubor .vstman (najdete jej v adresáři manifestu projektu VSIX), který byl výsledkem opětovného sestavení projektu VSIX:

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

 Informace poskytnuté [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element zůstává stejný. Prvek ** \<VSTemplateContainer>** odkazuje na soubor .vstemplate pro přidruženou šablonu.

 Tady je výchozí položka .vstemplate soubor vytvořený Visual Studio 2015:

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

 Zde je soubor .vstman (najdete jej v adresáři manifestu projektu VSIX), který byl výsledkem opětovného sestavení projektu VSIX:

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

 Informace poskytnuté ** \<templatedata>** prvek zůstává stejný. Prvek ** \<VSTemplateContainer>** odkazuje na soubor .vstemplate pro přidruženou šablonu.

 Další informace o různých prvcích souboru VSTMAN naleznete v tématu [Visual Studio Template Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Inovace pro rozšíření nainstalovaná pomocí aplikace . Msi

Některá rozšíření založená na MSI nasazují šablony do běžných umístění šablon, jako jsou následující adresáře:

- **\<Instalační adresář sady Visual Studio>\Common7\IDE\\<Šablony projektů/Šablony položek\>**

- **\<Instalační adresář sady Visual Studio>\Common7\IDE\Extensions\\<ExtensionName\> \\<Project/ItemTemplates\>**

Pokud vaše rozšíření provádí nasazení založené na MSI, je třeba vygenerovat manifest šablony ručně a ujistěte se, že je součástí nastavení rozšíření. Porovnejte výše uvedené příklady vstman a [odkaz na schéma manifestu šablony sady Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

Vytvořte samostatné manifesty pro šablony projektů a položek a měly by ukazovat na adresář kořenové šablony, jak je uvedeno výše. Vytvořte jeden manifest na rozšíření a národní prostředí.

## <a name="see-also"></a>Viz také

- [Poradce při potížích s zjišťováním šablony](troubleshooting-template-discovery.md)
- [Vytváření vlastních šablon projektů a položek](creating-custom-project-and-item-templates.md)
