---
title: Vytváření a Software Development Kit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7c3ff7a3a8c872c4b624c8d2956a6802a0ab139
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723670"
---
# <a name="creating-a-software-development-kit"></a>Vytvoření sady SDK (Software Development Kit)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

(SDK) software development kit je kolekce rozhraní API, která může odkazovat jako jedna položka v sadě Visual Studio. **Správce odkazů** dialogové okno obsahuje všechny sady SDK, které jsou relevantní pro projekt. Když přidáte sadu SDK do projektu, rozhraní API, jsou k dispozici v sadě Visual Studio.  
  
 Existují dva druhy sad SDK:  
  
- Sady SDK platformy jsou povinné součásti pro vývoj aplikací pro platformu. Například [!INCLUDE[win81](../includes/win81-md.md)] SDK je vyžadována k vývoji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace.  
  
- Rozšíření sady SDK jsou volitelné součásti, které rozšiřují platformu, ale nejsou povinné pro vývoj aplikací pro danou platformu.  
  
  Následující části popisují obecné infrastruktury sady SDK a jak vytvořit sadu SDK platformy a sady extension SDK.  
  
- [Sady SDK platformy](#PlatformSDKs)  
  
- [Rozšíření sady SDK](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> Sady SDK platformy  
 Sady SDK platformy jsou nezbytné pro vývoj aplikací pro platformu. Například [!INCLUDE[win81](../includes/win81-md.md)] SDK je vyžadována k vývoji aplikací pro [!INCLUDE[win81](../includes/win81-md.md)].  
  
### <a name="installation"></a>Instalace  
 Všechny platformy sady SDK se nainstalují v nastavení HKLM\Software\Microsoft\Microsoft SDK\\\v [stopami na PALEC] [TPV]\\ @InstallationFolder = [kořeni sady SDK]. Podle toho [!INCLUDE[win81](../includes/win81-md.md)] v nastavení HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 je nainstalovaná sada SDK.  
  
### <a name="layout"></a>Rozložení  
 Sady SDK platformy mají následující rozložení:  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|Uzel|Popis|  
|----------|-----------------|  
|Složka s odkazy|Obsahuje binární soubory, které obsahují rozhraní API, která mohou být kódovány proti. Ty mohou zahrnovat souborů metadat Windows (soubor WinMD) nebo sestavení.|  
|Složku DesignTime|Obsahuje soubory, které jsou potřeba pouze v předprodukční-spuštění/ladění v době. Ty mohou zahrnovat dokumentace XML, knihovny, záhlaví, binární soubory návrhových nástrojů, MSBuild artefakty a tak dále<br /><br /> Dokumentace XML, v ideálním případě umístěné ve složce \DesignTime ale dokumentace XML pro odkazy budou i nadále umístit odkaz na soubor v sadě Visual Studio. Například dokumentu XML pro referenční \References\\[Konfigurace]\\[arch]\sample.dll bude \References\\[Konfigurace]\\[arch]\sample.xml a lokalizovanou verzi tohoto dokumentu bude \References\\[Konfigurace]\\[arch]\\[locale]\sample.xml.|  
|Konfigurace složky|Může existovat jenom tři složky: ladění, maloobchodní prodej a CommonConfiguration. Autoři sady SDK můžete umístit své soubory pod CommonConfiguration, pokud stejnou sadu SDK soubory by měly využívat bez ohledu na to, konfiguraci, která zaměřené na spotřebitele SDK.|  
|Složka architektury|Může existovat žádná složka podporované architektury. Visual Studio podporuje následující architektury: x86, x64, ARM a neutral. Poznámka: Win32 mapuje x86 a AnyCPU mapuje na neutrální.<br /><br /> Nástroj MSBuild hledá jenom v rámci \CommonConfiguration\neutral sad SDK platformy.|  
|SDKManifest.xml|Tento soubor popisuje, jak by měl mít Visual Studio využívat sadu SDK. Podívejte se na Manifest sady SDK pro [!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Zobrazovaný název:** hodnotu, která prohlížeče objektů se zobrazí v seznamu Procházet.<br /><br /> **PlatformIdentity:** existence tohoto atributu instruuje Visual Studio a nástroje MSBuild, že sada SDK je sadu SDK platformy a že odkazy přidány z něj neměla Kopírovat místně.<br /><br /> **TargetFramework:** tento atribut se používá sada Visual Studio k zajištění, který pouze projekty, které cílí stejné rozhraní uvedená hodnota tohoto atributu můžou využívat sadu SDK.<br /><br /> **MinVSVersion:** tento atribut se používá sada Visual Studio používat pouze se sadami SDK služby, které se vztahují k němu.<br /><br /> **Referenční dokumentace:** tento atribut musí být zadán pouze odkazy, které obsahují ovládací prvky. Informace o tom, jak určit, zda odkaz obsahuje ovládací prvky najdete níže.|  
  
##  <a name="ExtensionSDKs"></a> Rozšíření sady SDK  
 Následující části popisují, co potřebujete k nasazení rozšíření sady SDK.  
  
### <a name="installation"></a>Instalace  
 Rozšíření sady SDK můžete nainstalovat pro konkrétního uživatele nebo pro všechny uživatele bez udání klíče registru. Pokud chcete nainstalovat sadu SDK pro všechny uživatele, použijte následující cestu:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Pro instalaci konkrétního uživatele použijte následující cestu:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Pokud chcete použít jiné umístění, musíte udělat jednu ze dvou kroků:  
  
1.  Zadejte ji v klíči registru:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     a přidejte podklíč (výchozí), který má hodnotu `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Přidat vlastnost MSBuild `SDKReferenceDirectoryRoot` do souboru projektu. Hodnota této vlastnosti je částečně identit seznam adresářů, ve kterých jsou umístěny rozšíření sady SDK, kterou chcete odkazovat.  
  
### <a name="installation-layout"></a>Instalace rozložení  
 Rozšíření sady SDK mají následující rozložení instalace:  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< SDKName\>\\< SDKVersion\>: název a verzi sady SDK je odvozen od odpovídající názvy složek v cestě ke kořenu sady SDK rozšíření. Tuto identitu použije nástroj MSBuild se najít sadu SDK na disku a sady Visual Studio se zobrazí tato identita v **vlastnosti** okno a **správce odkazů** dialogového okna.  
  
2.  Složka s odkazy: binární soubory, které obsahují rozhraní API. Může se jednat soubory Windows Metadata (WinMD) nebo sestavení.  
  
3.  Složky Redist: soubory, které jsou potřebné pro ladění nebo za běhu a by měl získat zabalené jako součást aplikace daného uživatele. Všechny binární soubory by měl být umístěn pod \redist\\< config\>\\< arch\>, a binárními názvy by měl mít následující formát, který zajistí jedinečnost:  **\<společnosti >.\< produkt >. \<účel >. \<rozšíření >**. Například Microsoft.Cpp.Build.dll. Všechny soubory s názvy, které mohou kolidovat s názvy souborů od ostatních sad SDK (například soubory jazyka javascript, css, pri, xaml, png a jpg) musí být umístěné pod \redist\\< config\>\\< arch\> \\< sdkname\>\ s výjimkou souborů, které jsou spojeny s XAML ovládací prvky. Tyto soubory musí být umístěné pod \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4.  Složku DesignTime: soubory, které jsou potřebné jenom předprodukční-spuštění/ladění čas a nesmí se zabalil jako součást aplikace daného uživatele. To může být dokumentace XML, knihovny, záhlaví, binární soubory návrhových nástrojů, MSBuild artefakty a tak dále. Všechny sady SDK, která je určená pro využití v nativní projekt musí mít *SDKName*souboru .props. Následuje ukázka tento typ souboru.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     Referenční dokumenty XML jsou umístěny společně s referenčního souboru. Například referenční dokument XML pro **\References\\< config\>\\< arch\>\sample.dll** sestavení je **\References\\ < config\>\\< arch\>\sample.xml**, a lokalizované verze tohoto dokumentu je **\References\\< config\>\\< arch\>\\< národní prostředí\>\sample.xml**.  
  
5.  Konfigurace složky: tři podsložek: ladění, maloobchodní prodej a CommonConfiguration. Autoři sady SDK můžete umístit své soubory pod CommonConfiguration při stejnou sadu SDK soubory by měly využívat bez ohledu na konfiguraci cílové sady SDK klienta.  
  
6.  Architektura složky: jsou podporovány následující architektury: x86, x64, ARM, neutrální. Win32 mapuje na x86 a AnyCPU mapuje na neutrální.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Tento soubor popisuje, jak by měl mít Visual Studio využívat sadu SDK. Následuje příklad.  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 Následující seznam obsahuje prvky souboru.  
  
1.  Zobrazovaný název: hodnotu, která se zobrazí ve Správci odkazů, Průzkumník řešení, prohlížeče objektů a jiných umístění v uživatelském rozhraní pro sadu Visual Studio.  
  
2.  ProductFamilyName: Celkový SDK název produktu. Například [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK má název "Microsoft.WinJS.1.0" a "Microsoft.WinJS.2.0", které patří do stejné řady produktů sady SDK, "Microsoft.WinJS". Tento atribut umožňuje sady Visual Studio a nástroje MSBuild, aby toto připojení. Pokud tento atribut neexistuje, název sady SDK se používá jako název rodiny produktů.  
  
3.  FrameworkIdentity: určuje závislost na jeden nebo více knihoven Windows komponent, které hodnota tohoto atributu je vložit do manifestu aplikace náročné. Tento atribut se vztahuje pouze na knihovny součástí Windows.  
  
4.  TargetFramework: Určuje, které jsou k dispozici ve Správci odkazů a panelu nástrojů sady SDK. Toto je seznam oddělený středníkem monikery cílové rozhraní framework, například "rozhraní .NET Framework, verze = verze 2.0, rozhraní .NET Framework, verze = v4.5.1". Pokud nejsou zadány několik verzí stejného cílovou architekturu, používá správce odkazů pro účely filtrování nejnižší zadaná verze. Například pokud "rozhraní .NET Framework, verze = verze 2.0, rozhraní .NET Framework, verze = v4.5.1" není zadán, použije Správce odkazů "rozhraní .NET Framework, verze = v2.0". Pokud je zadaný profil framework konkrétní cíl pouze tento profil se použije Správce odkazů pro účely filtrování. Například, když "Silverlight, verze = v4.0 profilu = WindowsPhone" není zadána, filtruje správce odkazů na pouze profilu Windows Phone; projekt, který cílí na úplné rozhraní Framework programu Silverlight 4.0 SDK ve Správci odkazů nezobrazí.  
  
5.  MinVSVersion: minimální verzi sady Visual Studio.  
  
6.  MaxPlatformVerson: Maximální Cílová platforma verze by měla sloužit k určení verze platformy, na kterých vaše rozšíření SDK nebude fungovat. Například balíčku Microsoft Visual C++ Runtime Package v11.0 by měl být odkazovány pouze projekty pro Windows 8. Projekt Windows 8 MaxPlatformVersion tedy 8.0. To znamená, že správce odkazů odfiltruje balíčku Microsoft Visual C++ Runtime pro projekt Windows 8.1 a MSBuild vyvolá chybu při [!INCLUDE[win81](../includes/win81-md.md)] projekt na ni odkazuje. Poznámka: Tento element je podporované počínaje [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
7.  Řetězec AppliesTo: Určuje sady SDK, které jsou k dispozici ve Správci odkazů tak, že zadáte použitelné typy projektů Visual Studio. Jsou rozpoznány devět hodnot: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, spravovaný a nativní. Autor sady SDK můžete použít a ("+"), nebo ("&#124;"), nikoli ("!") operátorů sloužící k určení přesně rozsah typy projektů, které se vztahují k sadě SDK.  
  
     WindowsAppContainer identifikuje projekty [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace.  
  
8.  SupportPrefer32Bit: Podporované hodnoty jsou "True" a "False". Výchozí hodnota je "True". Pokud je hodnota nastavena na hodnotu "False", MSBuild vrátí chybu pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekty (nebo upozornění pro desktopové projekty) obsahuje-li projekt, který odkazuje sadu SDK Prefer32Bit povolena. Další informace o Prefer32Bit najdete v tématu [stránku sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) nebo [stránka kompilovat, Návrhář projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: středníkem oddělený seznam architektur, které podporuje sada SDK. Nástroj MSBuild zobrazí upozornění, pokud Cílová architektura sady SDK v používání projektu se nepodporuje. Pokud tento atribut nezadáte, nástroj MSBuild nikdy nezobrazí tohoto typu upozornění.  
  
10. SupportsMultipleVersions: Pokud tento atribut je nastaven na **chyba** nebo **upozornění**, MSBuild označuje, že více verzí stejného řady SDK nemůže odkazovat na stejný projekt. Pokud tento atribut neexistuje, nebo je nastavena na **povolit**, MSBuild nezobrazí tohoto typu chyby nebo upozornění.  
  
11. AppX: Určuje cestu k balíčky aplikací pro Windows součásti knihovny na disku. Tato hodnota je předán registrační komponenta součástí knihovny Windows při místním ladění. Zásady vytváření názvů pro název souboru je  **\<společnosti >.\< Produkt >. \<Architektura >. \<Configuration >. \<Verze > .appx**. Konfigurace a architektura jsou volitelné v názvu atributu a hodnota atributu, pokud nemůžete použít ke knihovně součásti Windows. Tato hodnota se vztahuje pouze na knihovny součástí Windows.  
  
12. CopyRedistToSubDirectory: Určuje, kam se nakopíruje soubory ve složce \redist kořeni balíčku aplikace (to znamená **balíček umístění** vybrali v Průvodci vytvořením balíčku aplikace) a kořenové rozložení modulu runtime. Výchozí umístění je kořenový adresář balíčku aplikace a rozložení F5.  
  
13. DependsOn: Seznam SDK identit, které definují sad SDK, na kterých závisí Tato sada SDK. Tento atribut se zobrazí v podokně podrobností Správce odkazů.  
  
14. MoreInfo: adresa URL na webovou stránku, která poskytuje další informace a pomoc. Tato hodnota se používá v odkazu Další informace v pravém podokně Správce odkazů.  
  
15. Typ registrace: Určuje soubor WinMD registrace v manifestu aplikace a je vyžadováno pro nativní soubor WinMD, který má protějšek implementace knihovny DLL.  
  
16. Odkaz na soubor: zadaná pro pouze odkazy, které obsahují ovládací prvky nebo jsou soubory nativního Winmd. Informace o tom, jak určit, zda odkaz obsahuje ovládací prvky najdete v tématu [určení umístění položky panelu nástrojů](#ToolboxItems) níže.  
  
##  <a name="ToolboxItems"></a> Určení umístění položky panelu nástrojů  
 Element ToolBoxItems schématu SDKManifest.xml určuje kategorii a umístění položky panelu nástrojů v platformy a sady SDK rozšíření. Následující příklady ukazují, jak zadat jiné umístění. To se vztahuje na odkazy WinMD a DLL.  
  
1.  Umístit ovládací prvky v kategorii výchozí sady nástrojů.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Umístit ovládací prvky v rámci určité kategorie název.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Umístit ovládací prvky v rámci určité kategorie názvy.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Umístit ovládací prvky v rámci názvy různých kategorií v programu Blend a Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Zobrazení výčtu určité ovládací prvky jinak v programu Blend a Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Zobrazení výčtu specifických kontrolních mechanismů a umístit je na cestě Visual Studio běžné nebo pouze ve skupině všechny ovládací prvky.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Zobrazení výčtu specifických kontrolních mechanismů a zobrazit pouze konkrétní sady v ChooseItems bez nich se na panelu nástrojů.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření sady SDK pomocí jazyka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Návod: Vytvoření sady SDK pomocí jazyka C# nebo Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)

