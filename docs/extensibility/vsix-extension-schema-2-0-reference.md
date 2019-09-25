---
title: Referenční dokumentace schématu rozšíření VSIX 2,0 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c288764cf9182bc34233d312546f7915eed5975
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252184"
---
# <a name="vsix-extension-schema-20-reference"></a>Referenční dokumentace schématu rozšíření VSIX 2,0
Soubor manifestu nasazení VSIX popisuje obsah balíčku VSIX. Formát souboru se řídí schématem. Verze 2,0 tohoto schématu podporuje přidávání vlastních typů a atributů.  Schéma manifestu je rozšiřitelné. Zavaděč manifestu ignoruje prvky XML a atributy, které nerozumí.

> [!IMPORTANT]
> Visual Studio 2015 může načíst soubory VSIX v formátech Visual Studio 2010, Visual Studio 2012 nebo Visual Studio 2013.

## <a name="package-manifest-schema"></a>Schéma manifestu balíčku
 Kořenový prvek souboru XML manifestu je `<PackageManifest>`. Má jeden atribut `Version`, což je verze formátu manifestu. Pokud jsou ve formátu provedeny významné změny, změní se formát verze. Tento článek popisuje formát manifestu verze 2,0, který je zadán v manifestu `Version` nastavením atributu na hodnotu Version = "2.0".

### <a name="packagemanifest-element"></a>Element PackageManifest
 V rámci `<PackageManifest>` kořenového elementu můžete použít následující prvky:

- `<Metadata>`– Metadata a reklamní informace o samotném balíčku. V manifestu `Metadata` je povolen pouze jeden prvek.

- `<Installation>`– Tato část definuje způsob, jakým se dá balíček pro rozšíření nainstalovat, včetně SKU aplikace, do kterého se dá nainstalovat. V manifestu je `Installation` povolen pouze jeden prvek. Manifest musí mít `Installation` element, nebo tento balíček nebude nainstalován do žádné SKU.

- `<Dependencies>`– Tady je definovaný volitelný seznam závislostí pro tento balíček.

- `<Assets>`– Tato část obsahuje všechny prostředky obsažené v rámci tohoto balíčku. Bez této části Tento balíček nebude mít žádný obsah.

- `<AnyElement>*`– Schéma manifestu je dostatečně flexibilní, aby bylo možné jakékoli jiné prvky. Všechny podřízené elementy, které nejsou rozpoznány zavaděčem manifestu, jsou zveřejněny v rozhraní API Správce rozšíření jako extra objekty XmlElement. Pomocí těchto podřízených prvků mohou rozšíření VSIX definovat další data v souboru manifestu, který kód spuštěný v aplikaci Visual Studio může přistupovat v době běhu. Viz [Microsoft. VisualStudio. ExtensionManager. IExtension. AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Element metadata
 V této části najdete metadata týkající se balíčku, jeho identity a reklamních informací. `<Metadata>`obsahuje následující prvky:

- `<Identity>`– Definuje identifikační informace pro tento balíček a obsahuje následující atributy:

  - `Id`– Tento atribut musí být jedinečným IDENTIFIKÁTORem pro balíček zvolený autorem. Název by měl být kvalifikován stejným způsobem jako typy CLR jsou v oboru názvů: Company.Product.Feature.Name. `Id` Atribut je omezen na 100 znaků.

  - `Version`– Definuje verzi tohoto balíčku a jeho obsah. Tento atribut následuje po formátu verze sestavení CLR: Hlavní_verze. podverze. sestavení. revize (1.2.40308.00). Balíček s vyšším číslem verze se považuje za aktualizace balíčku a dá se nainstalovat přes existující nainstalovanou verzi.

  - `Language`– Tento atribut je výchozím jazykem pro balíček a odpovídá textovým datům v tomto manifestu. Tento atribut následuje po konvenci kódu národního prostředí CLR pro sestavení prostředků, například en-US, EN, fr-fr. Můžete určit `neutral` , že se má deklarovat jazyková a neutrální rozšíření, které se spustí na libovolné verzi sady Visual Studio. Výchozí hodnota je `neutral`.

  - `Publisher`– Tento atribut identifikuje vydavatele tohoto balíčku, buď název společnosti, nebo jméno jednotlivce. `Publisher` Atribut je omezen na 100 znaků.

- `<DisplayName>`– Tento prvek určuje uživatelsky přívětivý název balíčku, který se zobrazí v uživatelském rozhraní Správce rozšíření. `DisplayName` Obsah je omezený na 50 znaků.

- `<Description>`– Tento volitelný element je krátký popis balíčku a jeho obsah, který se zobrazí v uživatelském rozhraní Správce rozšíření. `Description` Obsah může obsahovat libovolný text, který požadujete, ale je omezený na 1000 znaků.

- `<MoreInfo>`– Tento volitelný prvek je adresa URL stránky online obsahující úplný popis tohoto balíčku. Protokol musí být zadaný jako http.

- `<License>`– Tento volitelný prvek je relativní cesta k souboru s licencí (. txt,. RTF) obsaženému v balíčku.

- `<ReleaseNotes>`– Tento volitelný prvek je buď relativní cesta k souboru poznámky k verzi obsažené v balíčku (. txt,. RTF), nebo jinak adresa URL webu, který zobrazuje poznámky k verzi.

- `<Icon>`– Tento volitelný prvek je relativní cesta k souboru obrázku (PNG, BMP, JPEG, ICO) obsaženému v balíčku. Obrázek ikony by měl být 32x32 pixelů (nebo bude zmenšen na tuto velikost) a zobrazí se v uživatelském rozhraní ListView. Pokud není `Icon` zadán žádný element, uživatelské rozhraní použije výchozí.

- `<PreviewImage>`– Tento volitelný prvek je relativní cesta k souboru obrázku (PNG, BMP, JPEG) obsaženému v balíčku. Obrázek verze Preview by měl být 200x200 pixelů a zobrazený v uživatelském rozhraní podrobností. Pokud není `PreviewImage` zadán žádný element, uživatelské rozhraní použije výchozí.

- `<Tags>`– Tento volitelný element vypíše další textové značky oddělené středníkem, které se použijí pro hledání tipů. `Tags` Element je omezený na 100 znaků.

- `<GettingStartedGuide>`– Tento volitelný prvek je buď relativní cesta k souboru HTML, nebo adresa URL webu, který obsahuje informace o tom, jak používat rozšíření nebo obsah v rámci tohoto balíčku. Tato příručka se spouští jako součást instalace.

- `<AnyElement>*`– Schéma manifestu je dostatečně flexibilní, aby bylo možné jakékoli jiné prvky. Všechny podřízené prvky, které nejsou rozpoznány zavaděčem manifestu, jsou zveřejněny jako seznam objektů XmlElement. Pomocí těchto podřízených prvků mohou rozšíření VSIX definovat další data v souboru manifestu a zobrazit je v době běhu.

### <a name="installation-element"></a>Element instalace
 Tato část definuje způsob, jakým se tento balíček dá nainstalovat, a SKU aplikace, do kterých se dá nainstalovat. Tato část obsahuje následující atributy:

- `Experimental`– Nastavte tento atribut na hodnotu true, pokud máte rozšíření, které je aktuálně nainstalováno pro všechny uživatele, ale vyvíjíte aktualizovanou verzi ve stejném počítači. Pokud jste například nainstalovali MyExtension 1,0 pro všechny uživatele, ale chcete ladit MyExtension 2,0 na stejném počítači, nastavte experimentální = "true". Tento atribut je k dispozici v aplikaci Visual Studio 2015 Update 1 nebo novější.

- `Scope`– Tento atribut může mít hodnotu "Global" nebo "ProductExtension":

  - "Globální" Určuje, že instalace není vymezená na konkrétní SKU. Tato hodnota se používá například v případě, že je nainstalována sada SDK rozšíření.

  - "ProductExtension" Určuje, že je nainstalovaná tradiční přípona VSIX (verze 1,0) v oboru pro jednotlivé SKU sady Visual Studio. Jedná se o výchozí hodnotu.

- `AllUsers`– Tento volitelný atribut určuje, jestli se tento balíček nainstaluje pro všechny uživatele. Ve výchozím nastavení má tento atribut hodnotu false, která určuje, že balíček je na uživatele. (Pokud nastavíte tuto hodnotu na true, musí se uživatel, který se instaluje, zvýšit na úroveň oprávnění správce a nainstalovat výsledný VSIX.

- `InstalledByMsi`– Tento volitelný atribut určuje, jestli je tento balíček nainstalovaný pomocí MSI. Balíčky nainstalované pomocí MSI se instalují a spravují pomocí MSI (programy a funkce), ne pomocí Správce rozšíření sady Visual Studio.  Ve výchozím nastavení má tento atribut hodnotu false, která určuje, že balíček není nainstalován pomocí MSI.

- `SystemComponent`– Tento volitelný atribut určuje, zda má být tento balíček považován za součást systému. Systémové součásti se nezobrazují v uživatelském rozhraní Správce rozšíření a nelze je aktualizovat. Ve výchozím nastavení má tento atribut hodnotu false, která určuje, že balíček není součástí systému.

- `AnyAttribute*``Installation` – Prvek přijímá sadu atributů Open-ukončeno, které budou zveřejněny za běhu jako dvojici název-hodnota.

- `<InstallationTarget>`– Tento prvek řídí umístění, kde instalační program VSIX balíček nainstaluje. Pokud je hodnota `Scope` atributu "ProductExtension", balíček musí cílit na SKU, který má k dispozici soubor manifestu jako součást jeho obsahu pro inzerování jeho dostupnosti pro rozšíření. Element má následující atributy, `Scope` Pokud má atribut explicitní nebo výchozí hodnotu "ProductExtension": `<InstallationTarget>`

  - `Id`– Tento atribut identifikuje balíček.  Atribut následuje po konvenci oboru názvů: Company.Product.Feature.Name. `Id` Atribut může obsahovat pouze alfanumerické znaky a je omezen na 100 znaků. Očekávané hodnoty:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft. VisualStudio. VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My. Shell. app

  - `Version`– Tento atribut určuje rozsah verzí s minimální a maximální podporovanou verzí této SKU. Balíček může podrobně navýšit verze SKU, které podporuje. Zápis rozsahu verzí je [10,0-11,0], kde

    - [-minimální verze včetně.

    - ] – maximální verze včetně.

    - (-minimální verze exkluzivní.

    - ) – maximální verze exkluzivní.

    - Samostatná verze – pouze zadaná verze

    > [!IMPORTANT]
    > Verze 2,0 schématu VSIX byla představena v aplikaci Visual Studio 2012. Chcete-li použít toto schéma, je nutné mít v počítači nainstalováno prostředí Visual Studio 2012 nebo novější a používat VSIXInstaller. exe, který je součástí daného produktu. Můžete cílit na starší verze sady Visual Studio pomocí sady Visual Studio 2012 nebo novějšího VSIXInstaller, ale pouze pomocí novějších verzí instalačního programu.

    Čísla verzí sady Visual Studio 2017 najdete na [číslech sestavení a datech verze sady Visual Studio](../install/visual-studio-build-numbers-and-release-dates.md).

    Při vyjádření verze pro vydání sady Visual Studio 2017 by měla podverze vždycky být **0**. Například Visual Studio 2017 verze 15.3.26730.0 by měla být vyjádřena jako [15.0.26730.0, 16.0). To se vyžaduje jenom pro Visual Studio 2017 a novější čísla verzí.

  - `AnyAttribute*``<InstallationTarget>` -Element umožňuje otevřené, ukončené sady atributů, které jsou zpřístupněny v době běhu jako dvojice název-hodnota.

### <a name="dependencies-element"></a>Element závislosti
 Tento prvek obsahuje seznam závislostí, které tento balíček deklaruje. Pokud jsou zadány jakékoli závislosti, musí být tyto balíčky ( `Id`identifikované jejich) nainstalovány před.

- `<Dependency>`element – tento podřízený element má následující atributy:

  - `Id`– Tento atribut musí být jedinečné ID pro závislý balíček. Tato hodnota identity se musí shodovat `<Metadata><Identity>Id` s atributem balíčku, na kterém je tento balíček závislý. `Id` Atribut následuje po konvenci oboru názvů: Company.Product.Feature.Name. Atribut může obsahovat pouze alfanumerické znaky a je omezen na 100 znaků.

  - `Version`– Tento atribut určuje rozsah verzí s minimální a maximální podporovanou verzí této SKU. Balíček může podrobně navýšit verze SKU, které podporuje. Zápis rozsahu verzí je [12,0, 13,0], kde:

    - [-minimální verze včetně.

    - ] – maximální verze včetně.

    - (-minimální verze exkluzivní.

    - ) – maximální verze exkluzivní.

    - Samostatná verze – pouze zadaná verze

  - `DisplayName`– Tento atribut je zobrazovaným názvem závislého balíčku, který se používá v prvcích uživatelského rozhraní, jako jsou dialogová okna a chybové zprávy. Atribut je volitelný, pokud není závislý balíček nainstalován pomocí MSI.

  - `Location`– Tento nepovinný atribut určuje buď relativní cestu v rámci tohoto VSIX, do vnořeného balíčku VSIX nebo adresu URL umístění pro stažení závislosti. Tento atribut slouží k tomu, aby uživatel mohl najít požadovaný balíček.

  - `AnyAttribute*``Dependency` – Prvek přijímá sadu atributů Open-ukončeno, které budou zveřejněny za běhu jako dvojici název-hodnota.

### <a name="assets-element"></a>Asset – element
 Tento prvek obsahuje seznam `<Asset>` značek pro každé rozšíření nebo element obsahu, který je v tomto balíčku Surface.

- `<Asset>`– Tento prvek obsahuje následující atributy a prvky:

  - `Type`-Typ rozšíření nebo obsahu reprezentovaného tímto elementem. Každý `<Asset>` prvek musí mít jeden `Type`, ale více `<Asset>` elementů může mít stejnou `Type`hodnotu. Tento atribut by měl být reprezentován jako plně kvalifikovaný název podle konvencí oboru názvů. Známé typy jsou:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft. VisualStudio. Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft. VisualStudio. Assembly

       Můžete vytvořit vlastní typy a dát jim jedinečné názvy. V době běhu v rámci sady Visual Studio může váš kód vytvořit výčet a přistupovat k těmto vlastním typům prostřednictvím rozhraní API Správce rozšíření.

  - `Path`– relativní cesta k souboru nebo složce v rámci balíčku, který obsahuje Asset.

  - `TargetVersion`– rozsah verzí, na který se daný prostředek vztahuje. Používá se pro přenos více verzí prostředků do různých verzí sady Visual Studio. K tomu je potřeba, aby se projevily sady Visual Studio 2017,3 nebo novější.

  - `AnyAttribute*`– Otevřená sada atributů, která je zveřejněna v době běhu jako dvojice název-hodnota.

    `<AnyElement>*`– Mezi `<Asset>` začátkem a koncovou značkou je povolený libovolný strukturovaný obsah. Všechny elementy jsou zveřejněny jako seznam objektů XmlElement. Rozšíření VSIX mohou v souboru manifestu definovat strukturovaná metadata specifická pro typ a zobrazit je v době běhu.

### <a name="sample-manifest"></a>Vzorový manifest

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

## <a name="see-also"></a>Viz také:

- [Dodávat rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
