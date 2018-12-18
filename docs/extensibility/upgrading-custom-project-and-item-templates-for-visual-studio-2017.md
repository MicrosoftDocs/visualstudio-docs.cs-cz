---
title: Upgrade vlastních šablon projektů a položek pro Visual Studio 2017 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af60281e7211e7b16e86200c02aef791d26da274
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143475"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Upgrade vlastních šablon projektů a položek pro Visual Studio 2017

Počínaje Visual Studio 2017, Visual Studio zjistí šablon projektů a položek, které byly nainstalovány VSIX nebo byl soubor MSI jiným způsobem s předchozími verzemi sady Visual Studio. Pokud jste vlastníkem rozšíření, které používají vlastní projektu nebo šablony položek, budete muset aktualizovat rozšíření. Toto téma vysvětluje, co musíte udělat.

Tato změna ovlivňuje pouze Visual Studio 2017. Předchozí verze sady Visual Studio nemá vliv.

Pokud chcete vytvořit šablonu projektu nebo položky jako součást rozšíření VSIX, přečtěte si téma [vytváření vlastních projektů a šablon položek](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Šablona kontrolu

V předchozích verzích sady Visual Studio **devenv/Setup** nebo **devenv/installvstemplates** zkontrolovat místního disku najít šablony projektů a položek. Od verze Visual Studio 2017, kontrola se provádí pouze pro individuální umístění. Výchozí umístění individuální **%USERPROFILE%\Documents\\< verze sady Visual Studio\>\Templates\\**. Toto umístění se používá pro šablony, které jsou generované **projektu** > **exportovat šablony...**  příkaz, pokud **automaticky importovat šablonu do sady Visual Studio** možnost je vybraná v průvodci.

Pro jiné umístění (neuživatelských) musí obsahovat manifest(.vstman) soubor, který určuje umístění a dalších vlastností šablony. .Vstman soubor je vytvořen společně s .vstemplate soubor použitý pro šablony. Při instalaci rozšíření pomocí VSIX, můžete k tomu lze nutnosti rekompilace rozšíření ve Visual Studio 2017. Ale pokud používáte byl soubor MSI, je potřeba provést změny ručně. Seznam co je potřeba udělat, aby byly tyto změny, naleznete v části **upgrady pro rozšíření nainstalované pomocí. MSI** dál v tomto tématu.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Postup aktualizace VSIX rozšíření projektu nebo šablony položek  

1.  Otevřete řešení ve Visual Studio 2017. Zobrazí se výzva k upgradu kód. Click **OK**.  
  
2.  Po dokončení upgradu, musíte změnit verzi cíl instalace. V projektu VSIX, otevřete soubor source.extension.vsixmanifest a vyberte **nainstalovat cíle** kartě. Pokud **rozsahu verze** pole je **[14.0]**, klikněte na tlačítko **upravit** a změnit tak, aby obsahovala Visual Studio 2017. Například můžete nastavit **[14.0,15.0]** nainstalovat rozšíření pro Visual Studio 2015 nebo Visual Studio 2017, nebo **[15.0]** nainstalovat do právě Visual Studio 2017.  
  
3.  Znovu zkompiluje kód.  
  
4.  Zavřete Visual Studio.  
  
5.  Nainstalujte VSIX.  
  
6.  Pomocí následujícího postupu můžete otestovat aktualizace:  
  
    1.  Soubor Kontrola změn se aktivuje pomocí následujícího klíče registru:  
  
         **REG přidat hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Po přidání klíče, spusťte **devenv/installvstemplates**.  
  
    3.  Znovu otevřete Visual Studio. Vaše šablona by měl zjistit do očekávaného umístění.  
  
    > [!NOTE]
    >  Šablony projektů Visual Studio rozšíření nejsou k dispozici, když se nachází v klíči registru. Je nutné odstranit klíč registru (a znovu spusťte **devenv/installvstemplates**) jejich použití.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Další doporučení pro nasazení šablon projektů a položek  
  
-   Nepoužívejte soubory komprimované šablony. Metoda ZIP šablonu, kterou soubory musí mít nekomprimované, aby bylo možné zjistit prostředky a obsah, takže budou costlier používat. Místo toho měli byste nasadit šablon projektů a položek, jako jednotlivých souborů v části vlastní adresář pro urychlení inicializace šablony. Pro rozšíření VSIX bude úlohami sestavení sady SDK automaticky rozbalte všechny komprimované šablonu při vytváření souboru VSIX.  
  
-   Vyhněte se použití položky ID balíčku nebo prostředků pro název šablony, popis, ikonu nebo preview, aby se zabránilo zbytečným prostředku sestavení načte při zjišťování šablony. Lokalizované manifesty místo, můžete použít k vytvoření šablony položky pro každý národního prostředí, která používá lokalizovaných názvů nebo vlastnosti.  
  
-   Chcete-li zahrnout šablony jako soubor položky, generování manifestu nemusí poskytnout očekávané výsledky. V takovém případě budete muset přidat ručně generované manifestu do projektu VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Změny souborů šablon projektů a položek  
Ukážeme body rozdíl mezi Visual Studio 2015 a Visual Studio 2017 verzích souborům šablon, tak, že můžete vytvořit nové soubory správně.  
  
 Tady je výchozí projekt .vstemplate soubor vytvořený pomocí sady Visual Studio 2015:  
  
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
  
 Tady je soubor .vstman (najdete ji v adresáři projektu VSIX manifestu), který je výsledkem znovu sestavit projekt VSIX:  
  
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
  
 Informace poskytované [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element zůstává stejná.  **\<VSTemplateContainer >** element odkazuje na soubor .vstemplate přidružené šablony.  
  
 Tady je výchozí položku .vstemplate soubor vytvořený pomocí sady Visual Studio 2015:  
  
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
  
 Tady je soubor .vstman (najdete ji v adresáři projektu VSIX manifestu), který je výsledkem znovu sestavit projekt VSIX:  
  
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
  
 Informace poskytované  **\<TemplateData >** element zůstává stejná.  **\<VSTemplateContainer >** element odkazuje na soubor .vstemplate přidružené šablony  
  
 Další informace o různých prvků souboru .vstman najdete v tématu [Visual Studio Manifest odkaz na schéma šablon](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrady pro rozšíření nainstalované pomocí. MSI

Některá rozšíření na základě MSI nasazení šablon do společné umístění šablon například následující:

- **\<Visual Studio Instalační adresář > \Common7\IDE\\< ProjectTemplates nebo šablon položek >**

- **\<Visual Studio Instalační adresář > \Common7\IDE\Extensions\\< Název_rozšíření\>\\< projektu nebo šablon položek >**

Pokud toto rozšíření provede nasazení na základě MSI, budete muset ručně generování manifestu šablony a ujistěte se, že je součástí instalace rozšíření. Porovnání .vstman příklady uvedené výše a [Visual Studio Manifest odkaz na schéma šablon](../extensibility/visual-studio-template-manifest-schema-reference.md).

Měli byste vytvořit samostatné manifesty pro šablony projektů a položek a by měla odkazovat na kořenový šablony adresář uvedeného výše. Vytvoření jednoho manifestu na rozšíření a národní prostředí.

## <a name="see-also"></a>Viz také

[Řešení potíží s zjišťování šablony](troubleshooting-template-discovery.md)  
[Vytváření vlastních šablon projektů a položek](creating-custom-project-and-item-templates.md)