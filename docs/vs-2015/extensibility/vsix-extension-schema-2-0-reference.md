---
title: VSIX Extension Schema 2.0 – referenční informace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c0121f2d9d4a29942449b180c63c450d4a49b31f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785928"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX Extension Schema 2.0 – referenční informace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soubor manifestu VSIX nasazení popisuje obsah balíčku VSIX. Formát souboru se řídí schéma. Verze 2.0 tato schématu podporuje přidávání vlastních typů a atributů.  Je možné rozšířit schéma manifestu. Manifestu zaváděcího programu ignoruje XML elementů a atributů, které ho nerozumí.  
  
> [!IMPORTANT]
>  Visual Studio 2015 můžete načíst soubory VSIX v sadě Visual Studio 2010, Visual Studio 2012 nebo Visual Studio 2013 formátech.  
  
## <a name="package-manifest-schema"></a>Schéma manifestu balíčku  
 Kořenový element souboru manifestu XML je `<PackageManifest>`, s jeden atribut `Version`, což je verze manifestu formátu. Pokud hlavní změny provedené ve formátu, formátu verze se změní. Toto téma popisuje formát manifestu verze 2.0, která je určená v manifestu tak, že nastavíte `Version` atributu na hodnotu verze = "2.0".  
  
### <a name="packagemanifest-element"></a>PackageManifest – Element  
 V rámci `<PackageManifest>` kořenový element, můžete použít následující prvky:  
  
-   `<Metadata>` – Metadata a reklamní informace o samotném balíčku. Pouze jeden `Metadata` element je povolen v manifestu.  
  
-   `<Installation>` – Tento oddíl definuje způsob, jakým tento balíček rozšíření může být nainstalován, včetně aplikace skladové položky, které můžete nainstalovat do. Pouze jeden `Installation` element je povolen v manifestu. Manifest musí mít `Installation` element nebo tento balíček nelze nainstalovat do všech SKU.  
  
-   `<Dependencies>` – Zde jsou definovány volitelný seznam závislostí pro tento balíček.  
  
-   `<Assets>` – Tento oddíl obsahuje všechny prostředky obsažené v tomto balíčku. Bez této části nebude tento balíček zařízení surface žádný obsah.  
  
-   `<AnyElement>*` – Schéma manifestu je dostatečně flexibilní, aby povolit další prvky. Všechny podřízené prvky nebyl rozpoznán zavaděčem manifestu jsou přístupné v rozhraní API pro správce rozšíření jako objekty navíc XmlElement. Pomocí těchto podřízených elementů, rozšíření VSIX můžete definovat další data v souboru manifestu, který kód spuštěný v sadě Visual Studio můžete získat přístup za běhu. Zobrazit <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> a <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Metadata – Element  
 Tato část se metadata o balíčku, identity a reklamním informace. `<Metadata>` obsahuje následující prvky:  
  
-   `<Identity>` -Toto definuje identifikační informace pro tento balíček a zahrnuje následující atributy:  
  
    -   `Id` – Tento atribut musí být jedinečné ID pro balíček zvolí jeho autor. Název musí být kvalifikovány stejným způsobem, jako jsou typy CLR namespaced: Company.Product.Feature.Name. `Id` Atribut je maximálně 100 znaků.  
  
    -   `Version` – Ten definuje verze tento balíček a jeho obsah. Tento atribut řídí formát Správa verzí sestavení CLR: Hlavníverze.podverze.Build.revize (1.2.40308.00). Balíček s vyšší číslo verze je považován za aktualizace balíčku a je možné nainstalovat přes existující nainstalovanou verzi.  
  
    -   `Language` – Tento atribut je výchozí jazyk pro balíček a odpovídá textová data v tomto manifestu. Tento atribut řídí konvence kódu CLR národní prostředí pro sestavení prostředků, například: en-us, en, fr-fr. Můžete zadat `neutral` deklarovat příponu neutrální jazyk, který se spustí na libovolné verzi sady Visual Studio. Výchozí hodnota je `neutral`.  
  
    -   `Publisher` – Tento atribut určuje vydavatele tohoto balíčku, společnost nebo jednoho názvu. `Publisher` Atribut je maximálně 100 znaků.  
  
-   `<DisplayName>` – Tento prvek určuje název uživatelsky přívětivé balíčku, který se zobrazí v Uživatelském rozhraní Správce rozšíření. `DisplayName` Obsah je maximálně 100 znaků.  
  
-   `<Description>` – Tento volitelný prvek je krátký popis balíček a jeho obsah, který se zobrazí v uživatelském rozhraní Správce rozšíření. `Description` Obsahu může obsahovat jakýkoli text, který chcete, ale je omezený na 1 000 znaků.  
  
-   `<MoreInfo>` – Tento volitelný prvek je adresa URL online stránku, která obsahuje úplný popis tohoto balíčku. Protokol musí být zadán jako protokolu http.  
  
-   `<License>` – Tento volitelný prvek je relativní cesta k licenční soubor (.txt, RTF) obsažené v balíčku.  
  
-   `<ReleaseNotes>` – Tento volitelný prvek je buď relativní cesta k souboru poznámky k verzi obsažené v balíčku (.txt, RTF), jinak se adresa URL webu, který se zobrazí zpráva k vydání verze.  
  
-   `<Icon>` – Tento volitelný prvek je relativní cesta k souboru image (png, bmp, jpeg, ico) obsažené v balíčku. Obrázek ikony musí být 32 x 32 pixelů (nebo bude zmenšit s velikostí) a zobrazí se v zobrazení listview uživatelského rozhraní. Pokud ne `Icon` Zadaný prvek, uživatelské rozhraní používá výchozí.  
  
-   `<PreviewImage>` – Tento volitelný prvek je relativní cesta k souboru image (png, bmp, jpeg) obsažené v balíčku. Obrázek náhledu by měl být 200 x 200 pixelů a zobrazí v podrobnostech uživatelského rozhraní. Pokud ne `PreviewImage` Zadaný prvek, uživatelské rozhraní používá výchozí.  
  
-   `<Tags>` – Tento volitelný prvek obsahuje seznam dalších text oddělený středníkem značky, které jsou používány pro pomocné parametry vyhledávání. `Tags` Element je maximálně 100 znaků.  
  
-   `<GettingStartedGuide>` – Tento volitelný prvek je relativní cesta k souboru ve formátu HTML nebo adresa URL webu, který obsahuje informace o tom, jak používat rozšíření nebo obsah v rámci tohoto balíčku. Tento průvodce se spustí jako součást instalace.  
  
-   `<AnyElement>*` – Schéma manifestu je dostatečně flexibilní, aby povolit další prvky. Podřízené elementy, které nejsou rozpoznány aplikací manifestu zaváděcího programu jsou vystaveny jako seznam objektů XmlElement. Pomocí těchto podřízených elementů, rozšíření VSIX definovat další data v souboru manifestu a výčet za běhu.  
  
### <a name="installation-element"></a>Instalace – Element  
 Tento oddíl definuje způsob, jakým lze nainstalovat tento balíček a skladové položky aplikace, které můžete nainstalovat do. Tato část obsahuje následující atributy:  
  
-   `Experimental` – Tento atribut nastaven na hodnotu true, pokud máte rozšíření, která je aktuálně nainstalována pro všechny uživatele, ale vyvíjíte aktualizovanou verzi na stejném počítači. Například pokud jste nainstalovali MyExtension 1.0 pro všechny uživatele, ale chcete ladit MyExtension 2.0 na stejném počítači, nastavte experimentální = "true". Tento atribut je k dispozici v aplikaci Visual Studio 2015 Update 1 nebo novější.  
  
-   `Scope` – Tento atribut může přijmout hodnoty "Globální" nebo "ProductExtension":  
  
    -   "Globální" Určuje, že instalace není v oboru konkrétní SKU. Například tato hodnota se používá při instalaci sady SDK rozšíření.  
  
    -   "ProductExtension" Určuje, že je nainstalována tradiční rozšíření VSIX (verze 1.0) obor na jednotlivých SKU Visual Studio. Jedná se o výchozí hodnotu.  
  
-   `AllUsers` – Tento volitelný atribut určuje, jestli tento balíček se nainstalují pro všechny uživatele. Ve výchozím nastavení je tento atribut false, která určuje, že balíček je na uživatele. (Když nastavíte tuto hodnotu na hodnotu true, daný uživatel musí zvýšení úrovně oprávnění pro správu instalace výsledného souboru VSIX.  
  
-   `InstalledByMsi` – Tento volitelný atribut určuje, jestli tento balíček je nainstalován pomocí MSI. Balíčky nainstalované pomocí MSI jsou nainstalované a spravované pomocí MSI (programy a funkce) a ne pomocí správce sady Visual Studio rozšíření.  Ve výchozím nastavení je tento atribut false, která určuje, že balíček není nainstalovaný pomocí MSI.  
  
-   `SystemComponent` – Tento volitelný atribut určuje, jestli tento balíček má považovat za součást systému. Součásti systému nezobrazovat v Uživatelském rozhraní Správce rozšíření a nelze ji aktualizovat. Ve výchozím nastavení je tento atribut false, která určuje, že balíček není součástí systému.  
  
-   `AnyAttribute*` – Tím `Installation` element přijímá neuzavřenou množinu atributy, které se zveřejní v době běhu jako slovník dvojice název hodnota.  
  
-   `<InstallationTarget>` – Tento prvek určuje umístění, kde instalátor VSIX nainstaluje balíček. Pokud hodnota `Scope` atribut je "ProductExtension" balíček, musí jako cíl skladové položky, který má nainstalovaný soubor manifestu jako součást svůj obsah rozbalí do inzerovat její dostupnost pro rozšíření. `<InstallationTarget>` Element má následující atributy, kdy `Scope` atribut má explicitní nebo výchozí hodnotu "ProductExtension":  
  
    -   `Id` – Tento atribut určuje balíček.  Atribut konvenci, obor názvů: Company.Product.Feature.Name. `Id` Atribut může obsahovat jenom alfanumerické znaky a je maximálně 100 znaků. Očekávané hodnoty:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` – Tento atribut určuje rozsah verzí s minimální a maximální podporovanou verzí tato skladová položka. Balíček lze podrobně verze SKU, které podporuje. Zápis rozsahu verze je [10.0 – 11.0], kde  
  
        -   [– minimální verze (včetně).  
  
        -   ] – maximální verze (včetně).  
  
        -   (– minimální verze exkluzivní.  
  
        -   ) – exkluzivní maximální verze.  
  
        -   Jedna verze # - jenom určená verze.  
  
        > [!IMPORTANT]
        >  Verze 2.0 VSIX schématu byla zavedena v sadě Visual Studio 2012. Pro toto schéma používají, musíte mít Visual Studio 2012 nebo později na počítači nainstalovaný a použít VSIXInstaller.exe, které jsou součástí tohoto produktu. Můžete cílit starší verze sady Visual Studio s Visual Studio 2012 nebo novější VSIXInstaller, ale pouze pomocí novější verze Instalační služby.  
  
    -   `AnyAttribute*` – Tím `<InstallationTarget>` element umožňuje neuzavřenou množinu atributy, které bude přístupné za běhu jako slovník dvojice název hodnota.  
  
### <a name="dependencies-element"></a>Dependencies – Element  
 Tento prvek obsahuje seznam závislostí, které deklaruje tento balíček. Pokud nejsou zadány žádné závislosti, tyto balíčky (identifikovaný jejich `Id`) musí být nainstalována před.  
  
-   `<Dependency>` Element – tento podřízený element má následující atributy:  
  
    -   `Id` – Tento atribut musí být jedinečné ID pro závislý balíček. Tato hodnota identity musí odpovídat `<Metadata><Identity>Id` atribut, který tento balíček závisí na balíčku. `Id` Atribut konvenci, obor názvů: Company.Product.Feature.Name. Atribut může obsahovat jenom alfanumerické znaky a je maximálně 100 znaků.  
  
    -   `Version` – Tento atribut určuje rozsah verzí s minimální a maximální podporovanou verzí tato skladová položka. Balíček lze podrobně verze SKU, které podporuje. Zápis verze rozsah je [12,0, 13,0], kde:  
  
        -   [– minimální verze (včetně).  
  
        -   ] – maximální verze (včetně).  
  
        -   (– minimální verze exkluzivní.  
  
        -   ) – exkluzivní maximální verze.  
  
        -   Jedna verze # - jenom určená verze.  
  
    -   `DisplayName` – Tento atribut je zobrazovaný název závislý balíček, který se používá v prvky uživatelského rozhraní, jako je například dialogová okna a chybové zprávy. Atribut je volitelný, pokud je nainstalován závislý balíček pomocí Instalační služby MSI.  
  
    -   `Location` – Tento volitelný atribut určuje buď relativní cesta v rámci tohoto VSIX do vnořených balíčku VSIX nebo adresu URL pro umístění stahování pro závislost. Tento atribut slouží umožňující uživateli, vyhledejte balíček požadovaných součástí.  
  
    -   `AnyAttribute*` – Tím `Dependency` element přijímá neuzavřenou množinu atributy, které se zveřejní v době běhu jako slovník dvojice název hodnota.  
  
### <a name="assets-element"></a>Element prostředky  
 Tento prvek obsahuje seznam `<Asset>` prezentované značky pro každý prvek rozšíření nebo obsahu, kterou tento balíček.  
  
- `<Asset>` – Tento prvek obsahuje následující atributy a elementy:  
  
  - `Type` – Toto je typ rozšíření nebo obsah reprezentovaný tímto prvkem. Každý `<Asset>` element musí mít jeden `Type`, ale více `<Asset>` elementy může mít stejný `Type`. Tento atribut by měl být reprezentován jako plně kvalifikovaný název, podle konvence oboru názvů. Známé typy jsou:  
  
    1. Microsoft.VisualStudio.VsPackage  
  
    2. Microsoft.VisualStudio.MefComponent  
  
    3. Microsoft.VisualStudio.ToolboxControl  
  
    4. Microsoft.VisualStudio.Samples  
  
    5. Microsoft.VisualStudio.ProjectTemplate  
  
    6. Microsoft.VisualStudio.ItemTemplate  
  
    7. Microsoft.VisualStudio.Assembly  
  
       Můžete vytvořit vlastní typy a přiřadit jedinečné názvy. Za běhu v sadě Visual Studio můžete kód výčet a tyto vlastní typy přístup prostřednictvím Správce rozšíření pro rozhraní API.  
  
  - Cesta – relativní cesta k souboru nebo složky v rámci balíčku, který obsahuje prostředek.  
  
  - `AnyAttribute*` – Neuzavřenou množinu atributy, které bude přístupné za běhu jako slovník dvojice název hodnota.  
  
     `<AnyElement>*` – Všechny Strukturovaný obsah je povolen mezi `<Asset>` začínají i končí značky. Všechny prvky jsou vystaveny jako seznam objektů XmlElement. Rozšíření VSIX, můžete definovat strukturovaných metadata specifická pro typ v souboru manifestu a výčet za běhu.  
  
### <a name="sample-manifest"></a>Ukázka manifestu  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
  <Metadata>  
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />  
    <DisplayName>Test Package</DisplayName>  
    <Description>Information about my package</Description>  
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>  
    <License>eula.rtf</License>  
    <ReleaseNotes>notes.txt</ReleaseNotes>  
    <Icon>Images\icon.png</Icon>  
    <PreviewImage>Images\preview.png</PreviewImage>  
  </Metadata>  
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />  
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />  
  </Assets>  
</PackageManifest>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

