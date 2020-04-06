---
title: VSIX Rozšíření schéma 2.0 Reference | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697916"
---
# <a name="vsix-extension-schema-20-reference"></a>Odkaz na schéma rozšíření VSIX 2.0
Soubor manifestu nasazení VSIX popisuje obsah balíčku VSIX. Formát souboru se řídí schématem. Verze 2.0 tohoto schématu podporuje přidávání vlastních typů a atributů.  Schéma manifestu je rozšiřitelné. Zavaděč manifestu ignoruje elementy XML a atributy, kterým nerozumí.

> [!IMPORTANT]
> Visual Studio 2015 můžete načíst soubory VSIX ve formátu Visual Studio 2010, Visual Studio 2012 nebo Visual Studio 2013.

## <a name="package-manifest-schema"></a>Schéma manifestu balíčku
 Kořenovým prvkem souboru XML `<PackageManifest>`manifestu je . Má jeden atribut `Version`, což je verze formátu manifestu. Pokud jsou ve formátu provedeny velké změny, změní se formát verze. Tento článek popisuje formát manifestu verze 2.0, který `Version` je určen v manifestu nastavením atributu na hodnotu Version="2.0".

### <a name="packagemanifest-element"></a>Element PackageManifest
 V `<PackageManifest>` kořenovém prvku můžete použít následující prvky:

- `<Metadata>`- Metadata a reklamní informace o samotném balíčku. V `Metadata` manifestu je povolen pouze jeden prvek.

- `<Installation>`- Tato část definuje způsob, jakým lze nainstalovat tento balíček rozšíření, včetně aplikací SKU, do kterých se dá nainstalovat. V manifestu je povolen pouze jeden `Installation` prvek. Manifest musí mít `Installation` prvek, jinak se tento balíček nenainstaluje do žádné skladové položky.

- `<Dependencies>`- Volitelný seznam závislostí pro tento balíček jsou definovány zde.

- `<Assets>`- Tato část obsahuje všechna aktiva obsažená v tomto balíčku. Bez této části nebude tento balíček vynořován žádný obsah.

- `<AnyElement>*`- Schéma manifestu je dostatečně flexibilní, aby bylo možné povolit další prvky. Všechny podřízené prvky, které nejsou rozpoznány zavaděčem manifestu, jsou v rozhraní API správce rozšíření vystaveny jako další objekty XmlElement. Pomocí těchto podřízených prvků mohou rozšíření VSIX definovat další data v souboru manifestu, ke kterému má kód spuštěný v sadě Visual Studio přístup za běhu. Viz [Microsoft.VisualStudio.extensionmanager.iextension.additionalelements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Prvek metadat
 Tato část je metadata o balíčku, jeho identity a reklamní informace. `<Metadata>`obsahuje následující prvky:

- `<Identity>`- Definuje identifikační informace pro tento balíček a obsahuje následující atributy:

  - `Id`- Tento atribut musí být jedinečné ID pro balíček zvolený jeho autorem. Název by měl být kvalifikován stejným způsobem clr typy jsou názvové: Company.Product.Feature.Name. Atribut `Id` je omezen na 100 znaků.

  - `Version`- Definuje verzi tohoto balíčku a jeho obsah. Tento atribut se řídí formátem správy verzí sestavení CLR: Major.Minor.Build.Revision (1.2.40308.00). Balíček s vyšším číslem verze je považován za aktualizaci balíčku a lze jej nainstalovat přes existující nainstalovanou verzi.

  - `Language`- Tento atribut je výchozí jazyk pro balíček a odpovídá textová data v tomto manifestu. Tento atribut následuje konvence kódu národního prostředí CLR pro sestavení prostředků, například: en-us, en, fr-fr. Můžete zadat `neutral` deklarovat jazykově neutrální rozšíření, které bude spuštěno v libovolné verzi sady Visual Studio. Výchozí hodnota je `neutral`.

  - `Publisher`- Tento atribut identifikuje vydavatele tohoto balíčku, buď název společnosti nebo jednotlivé jméno. Atribut `Publisher` je omezen na 100 znaků.

- `<DisplayName>`- Tento prvek určuje uživatelsky přívětivý název balíčku, který se zobrazí v uživatelském rozhraní Správce rozšíření. Obsah `DisplayName` je omezen na 50 znaků.

- `<Description>`- Tento volitelný prvek je krátký popis balíčku a jeho obsah, který je zobrazen v uzdu Správce rozšíření. Obsah `Description` může obsahovat libovolný text, který chcete, ale je omezen na 1000 znaků.

- `<MoreInfo>`- Tento volitelný prvek je URL na stránku on-line, která obsahuje úplný popis tohoto balíčku. Protokol musí být zadán jako http.

- `<License>`- Tento volitelný prvek je relativní cesta k licenčnímu souboru (.txt, .rtf) obsaženému v balíčku.

- `<ReleaseNotes>`- Tento volitelný prvek je buď relativní cestou k souboru poznámky k verzi obsažené v balíčku (.txt, .rtf) nebo url na webu, který zobrazuje poznámky k verzi.

- `<Icon>`- Tento volitelný prvek je relativní cesta k obrazovému souboru (png, bmp, jpeg, ico) obsaženév balíčku. Obrázek ikony by měl být 32 x 32 pixelů (nebo bude zmenšen na tuto velikost) a zobrazí se v uživatelském uživatelském panelu zobrazení seznamu. Pokud `Icon` není zadán žádný prvek, použití výchozího použití rozhraní používá.

- `<PreviewImage>`- Tento volitelný prvek je relativní cesta k obrazovému souboru (png, bmp, jpeg) obsaženému v balíčku. Náhled obrázku by měl být 200x200 pixelů a zobrazí se v uživatelském uživatelském období podrobností. Pokud `PreviewImage` není zadán žádný prvek, použití výchozího použití rozhraní používá.

- `<Tags>`- Tento volitelný prvek obsahuje další textové značky oddělené středníkem, které se používají pro rady při hledání. Prvek `Tags` je omezen na 100 znaků.

- `<GettingStartedGuide>`- Tento volitelný prvek je buď relativní cesta k souboru HTML nebo URL na webové stránky, která obsahuje informace o tom, jak používat rozšíření nebo obsah v rámci tohoto balíčku. Tato příručka je spuštěna jako součást instalace.

- `<AnyElement>*`- Schéma manifestu je dostatečně flexibilní, aby bylo možné povolit další prvky. Všechny podřízené prvky, které nejsou rozpoznány zavaděčmanifestu jsou vystaveny jako seznam objektů XmlElement. Pomocí těchto podřízených prvků mohou rozšíření VSIX definovat další data v souboru manifestu a vytvořit jejich výčet za běhu.

### <a name="installation-element"></a>Instalační prvek
 Tato část definuje způsob instalace tohoto balíčku a soupoložky aplikace, do kterých lze nainstalovat. Tato část obsahuje následující atributy:

- `Experimental`- Nastavte tento atribut na hodnotu true, pokud máte rozšíření, které je aktuálně nainstalováno pro všechny uživatele, ale vyvíjíte aktualizovanou verzi ve stejném počítači. Například pokud jste nainstalovali MyExtension 1.0 pro všechny uživatele, ale chcete ladit MyExtension 2.0 ve stejném počítači, nastavte Experimental ="true". Tento atribut je k dispozici v aktualizaci Visual Studio 2015 Update 1 a novější.

- `Scope`- Tento atribut může mít hodnotu "Global" nebo "ProductExtension":

  - "Globální" určuje, že instalace není vymezena na konkrétní skladovou položku. Tato hodnota se například používá při instalaci sady SDK rozšíření.

  - "ProductExtension" určuje, že je nainstalovántradiční Rozšíření VSIX (verze 1.0) s vymezeným oborem pro jednotlivé skupy Sady skurech sady Visual Studio. Toto je výchozí hodnota.

- `AllUsers`- Tento volitelný atribut určuje, zda bude tento balíček nainstalován pro všechny uživatele. Ve výchozím nastavení je tento atribut false, který určuje, že balíček je pro jednotlivé uživatele. (Pokud nastavíte tuto hodnotu na hodnotu true, musí instalační uživatel zvýšit úroveň oprávnění správce, aby mohl nainstalovat výsledný VSIX.

- `InstalledByMsi`- Tento volitelný atribut určuje, zda je tento balíček nainstalován msi. Balíčky nainstalované pomocí msi jsou nainstalovány a spravovány msi (programy a funkce) a nikoli Správcem rozšíření sady Visual Studio.  Ve výchozím nastavení je tento atribut false, který určuje, že balíček není nainstalován MSI.

- `SystemComponent`- Tento volitelný atribut určuje, zda má být tento balíček považován za systémovou součást. Systémové součásti se nezobrazují v uzdu Správce rozšíření a nelze je aktualizovat. Ve výchozím nastavení je tento atribut false, který určuje, že balíček není systémovou součástí.

- `AnyAttribute*`- `Installation` Prvek přijímá otevřenou sadu atributů, které budou vystaveny za běhu jako slovník dvojice název-hodnota.

- `<InstallationTarget>`-Tento prvek řídí umístění, kde instalátor VSIX nainstaluje balíček. Pokud je hodnota `Scope` atributu "ProductExtension" balíček musí cílit na skladovou položku, která nainstalovala soubor manifestu jako součást jeho obsahu inzerovat jeho dostupnost rozšíření. Prvek `<InstallationTarget>` má následující atributy, `Scope` pokud má atribut explicitní nebo výchozí hodnotu "ProductExtension":

  - `Id`- Tento atribut identifikuje balíček.  Atribut následuje podle konvence oboru názvů: Company.Product.Feature.Name. Atribut `Id` může obsahovat pouze alfanumerické znaky a je omezen na 100 znaků. Očekávané hodnoty:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VswinExpress

    - Soubor Microsoft.VisualStudio.VSLS

    - Aplikace My.Shell.App

  - `Version`- Tento atribut určuje rozsah verzí s minimální a maximální podporované verze této skladové položky. Balíček můžete podrobně verze sku, které podporuje. Zápis rozsahu verze je [10.0 - 11.0], kde

    - [ - minimální verze včetně.

    - ] - maximální verze včetně.

    - ( - minimální verze exkluzivní.

    - ) - maximální verze exkluzivní.

    - Jedna verze # - pouze zadaná verze.

    > [!IMPORTANT]
    > Verze 2.0 schématu VSIX byla představena v sadě Visual Studio 2012. Chcete-li použít toto schéma, musíte mít v počítači nainstalovánvisual studio 2012 nebo novější a používat soubor VSIXInstaller.exe, který je součástí tohoto produktu. Starší verze sady Visual Studio můžete cílit pomocí aplikace Visual Studio 2012 nebo novějšího vsixinstalleru, ale pouze pomocí novějších verzí instalačního programu.

    Čísla verzí sady Visual Studio 2017 najdete v [číslech sestavení sady Visual Studio a datech vydání](../install/visual-studio-build-numbers-and-release-dates.md).

    Při vyjádření verze pro verze Sady Visual Studio 2017 by dílčí verze měla být vždy **0**. Například Visual Studio 2017 verze 15.3.26730.0 by měla být vyjádřena jako [15.0.26730.0,16.0). To je vyžadováno pouze pro čísla visual studio 2017 a novější verze.

  - `AnyAttribute*`- `<InstallationTarget>` Prvek umožňuje otevřenou sadu atributů, která je vystavena za běhu jako slovník dvojice název-hodnota.

### <a name="dependencies-element"></a>Prvek závislostí
 Tento prvek obsahuje seznam závislostí, které tento balíček deklaruje. Pokud jsou zadány některé závislosti, tyto `Id`balíčky (identifikované jejich ) musí být nainstalovány dříve.

- `<Dependency>`element - Tento podřízený prvek má následující atributy:

  - `Id`- Tento atribut musí být jedinečné ID pro závislý balíček. Tato hodnota identity `<Metadata><Identity>Id` musí odpovídat atributu balíčku, na který je tento balíček závislý. Atribut `Id` následuje podle konvence oboru názvů: Company.Product.Feature.Name. Atribut může obsahovat pouze alfanumerické znaky a je omezen na 100 znaků.

  - `Version`- Tento atribut určuje rozsah verzí s minimální a maximální podporované verze této skladové položky. Balíček můžete podrobně verze sku, které podporuje. Zápis rozsahu verze je [12.0, 13.0], kde:

    - [ - minimální verze včetně.

    - ] - maximální verze včetně.

    - ( - minimální verze exkluzivní.

    - ) - maximální verze exkluzivní.

    - Jedna verze # - pouze zadaná verze.

  - `DisplayName`- Tento atribut je zobrazovaný název závislého balíčku, který se používá v prvcích uživatelského rozhraní, jako jsou dialogová okna a chybové zprávy. Atribut je volitelný, pokud závislý balíček není nainstalován msi.

  - `Location`- Tento volitelný atribut určuje relativní cestu v rámci tohoto vsix vnořený balíček VSIX nebo adresu URL do umístění pro stahování pro závislost. Tento atribut se používá k pomoci uživateli najít požadavek balíček.

  - `AnyAttribute*`- `Dependency` Prvek přijímá otevřenou sadu atributů, které budou vystaveny za běhu jako slovník dvojice název-hodnota.

### <a name="assets-element"></a>Prvek datového zdroje
 Tento prvek obsahuje `<Asset>` seznam značek pro každou rozšíření nebo prvek obsahu, který se zobrazí v tomto balíčku.

- `<Asset>`- Tento prvek obsahuje následující atributy a prvky:

  - `Type`- Typ rozšíření nebo obsah reprezentované tímto prvkem. Každý `<Asset>` prvek musí `Type`mít jeden `<Asset>` , ale `Type`více prvků může mít stejné . Tento atribut by měl být reprezentován jako plně kvalifikovaný název podle konvencí oboru názvů. Známé typy jsou:

    1. Balíček Microsoft.VisualStudio.VsPackage

    2. Součást Microsoft.VisualStudio.MefComponent

    3. Ovládací prvek Microsoft.VisualStudio.Toolbox

    4. Microsoft.VisualStudio.Samples

    5. Šablona Microsoft.VisualStudio.ProjectTemplate

    6. Šablona Microsoft.VisualStudio.Item

    7. Microsoft.VisualStudio.Assembly

       Můžete vytvořit vlastní typy a dát jim jedinečné názvy. V době běhu v sadě Visual Studio může váš kód vytvořit výčet a získat přístup k těmto vlastním typům prostřednictvím rozhraní API správce rozšíření.

  - `Path`- relativní cestu k souboru nebo složce v rámci balíčku, který obsahuje datový zdroj.

  - `TargetVersion`- rozsah verzí, na který se daný majetek vztahuje. Používá se pro odesílání více verzí datových zdrojů do různých verzí sady Visual Studio. Vyžaduje Visual Studio 2017.3 nebo novější efekt.

  - `AnyAttribute*`- Otevřená sada atributů, která je vystavena za běhu jako slovník dvojice název-hodnota.

    `<AnyElement>*`- Mezi počáteční a koncovou `<Asset>` značkou je povolen jakýkoli strukturovaný obsah. Všechny prvky jsou vystaveny jako seznam objektů XmlElement. Rozšíření VSIX můžete definovat strukturované typově specifická metadata v souboru manifestu a jejich výčet za běhu.

### <a name="sample-manifest"></a>Ukázkový manifest

```xml
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

- [Rozšíření aplikace Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
