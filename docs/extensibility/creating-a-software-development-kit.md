---
title: Vytvoření sady pro vývoj softwaru | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739602"
---
# <a name="create-a-software-development-kit"></a>Vytvoření sady pro vývoj softwaru

Sada Pro vývoj softwaru (SDK) je kolekce api, na které můžete odkazovat jako na jednu položku v sadě Visual Studio. Dialogové okno **Správce odkazů** obsahuje seznam všech sad SDK, které jsou relevantní pro projekt. Když přidáte sdk do projektu, rozhraní API jsou k dispozici v sadě Visual Studio.

Existují dva typy sad SDK:

- Sady SDK platformy jsou povinné součásti pro vývoj aplikací pro platformu. Například [!INCLUDE[win81](../debugger/includes/win81_md.md)] sada SDK je [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] vyžadována k vývoji aplikací.

- Sady SDK rozšíření jsou volitelné součásti, které rozšiřují platformu, ale nejsou povinné pro vývoj aplikací pro tuto platformu.

Následující části popisují obecnou infrastrukturu sad SDK a jak vytvořit platformu SDK a rozšíření SDK.

## <a name="platform-sdks"></a>Sady SDK platformy

Sady SDK platformy jsou nutné k vývoji aplikací pro platformu. [!INCLUDE[win81](../debugger/includes/win81_md.md)] Sada SDK je například vyžadována [!INCLUDE[win81](../debugger/includes/win81_md.md)]k vývoji aplikací pro .

### <a name="installation"></a>Instalace

Všechny sady SDK platformy budou nainstalovány na *adrese HKLM\Software\Microsoft\Microsoft SDK\\ @InstallationFolder [TPI]\v[TPV]\\= [Kořenová sada SDK]*. V souladu [!INCLUDE[win81](../debugger/includes/win81_md.md)] s tím je sada SDK nainstalována na adrese *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

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

| Node | Popis |
|------------------------| - |
| *Složka Reference* | Obsahuje binární soubory, které obsahují api, které mohou být kódovány proti. Ty mohou zahrnovat soubory nebo sestavení metadat systému Windows (WinMD). |
| *Složka DesignTime* | Obsahuje soubory, které jsou potřeba pouze v době před spuštěním/laděním. Mohou mezi ně patřit dokumenty XML, knihovny, záhlaví, binární soubory návrhu panelu nástrojů, artefakty MSBuild atd.<br /><br /> Dokumenty XML by byly v ideálním případě umístěny do složky *\DesignTime,* ale dokumenty XML pro odkazy budou nadále umístěny vedle referenčního souboru v sadě Visual Studio. Například dokument XML pro referenci<em>\Reference\\[config]\\[arch]\sample.dll</em> bude *\Reference [config]\\\\[arch]\sample.xml*a lokalizovaná verze tohoto dokumentu bude *\Reference [config]\\\\[arch]\\[locale]\sample.xml*. |
| *Konfigurační* složka | Mohou existovat pouze tři složky: *Ladění*, *Maloobchod* a *CommonConfiguration*. Autoři sady SDK mohou umístit své soubory do *commonconfiguration,* pokud by měla být spotřebována stejná sada souborů sady SDK, bez ohledu na konfiguraci, na kterou bude příjemce sady SDK cílit. |
| *Složka Architektura* | Může existovat libovolná podporovaná složka *architektury.* Visual Studio podporuje následující architektury: x86, x64, ARM a neutrální. Poznámka: Win32 mapuje na x86 a AnyCPU mapy na neutrální.<br /><br /> MSBuild vypadá pouze v části *\CommonConfiguration\neutral* pro sady SDK platformy. |
| *Soubor SDKManifest.xml* | Tento soubor popisuje, jak visual studio by měl využívat sdk. Podívejte se na manifest [!INCLUDE[win81](../debugger/includes/win81_md.md)]sady SDK pro:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Hodnota, kterou prohlížeč objektů zobrazí v seznamu Procházet.<br /><br /> **Platformidentity:** Existence tohoto atributu říká Visual Studio a MSBuild, že Sada SDK je sada SDK platformy a že odkazy přidané z něj by neměly být zkopírovány místně.<br /><br /> **TargetFramework:** Tento atribut používá Visual Studio k zajištění, že pouze projekty, které cílí na stejné architektury, jak je uvedeno v hodnotě tohoto atributu můžete spotřebovat SDK.<br /><br /> **MinVSVersion:** Tento atribut používá visual studio využívat pouze sady SDK, které se na něj vztahují.<br /><br /> **Odkaz:** Tento atribut musí být určen pouze pro ty odkazy, které obsahují ovládací prvky. Informace o tom, jak určit, zda odkaz obsahuje ovládací prvky, naleznete níže. |

## <a name="extension-sdks"></a>Sady SDK rozšíření

Následující části popisují, co je třeba udělat pro nasazení sady SDK rozšíření.

### <a name="installation"></a>Instalace

Sady SDK rozšíření lze nainstalovat pro konkrétního uživatele nebo pro všechny uživatele bez zadání klíče registru. Chcete-li nainstalovat sadu SDK pro všechny uživatele, použijte následující cestu:

*%Program Files%\Cílová platforma\<\>sad Microsoft SDK \v<číslo\>verze platformy \ExtensionSDKs*

Pro instalaci specifickou pro uživatele použijte následující cestu:

*%USERPROFILE%\AppData\Local\Microsoft SDKs cílová platforma\<\>\>\v<číslo verze platformy \ExtensionSDKs*

Pokud chcete použít jiné umístění, musíte udělat jednu ze dvou věcí:

1. Zadejte jej v klíči registru:

     **HKLM\Software\Microsoft\Microsoft\<SDKs cílová platforma>\v<\>číslo\<verze platformy \<\ExtensionSDKs SDKName>SDKVersion>**\

     a přidejte podklíč (Výchozí), který `<path to SDK><SDKName><SDKVersion>`má hodnotu .

2. Přidejte vlastnost `SDKReferenceDirectoryRoot` MSBuild do souboru projektu. Hodnota této vlastnosti je středník oddělený seznam adresářů, ve kterých rozšíření sady SDK, na které chcete odkazovat.

### <a name="installation-layout"></a>Rozložení instalace

Sady SDK rozšíření mají následující rozložení instalace:

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

1. \\<SDKName\> \\<SDKVersion\>: název a verze rozšíření SDK je odvozen a odpovídající názvy složek v cestě ke kořenu sady SDK. MSBuild používá tuto identitu k vyhledání sady SDK na disku a Visual Studio zobrazí tuto identitu v okně **Vlastnosti** a **dialogovém okně Správce odkazů.**

2. *Složka odkazy:* binární soubory, které obsahují api. Mohou to být soubory nebo sestavení metadat systému Windows (WinMD).

3. *Redist* složka: soubory, které jsou potřebné pro runtime/ladění a měly by být zabaleny jako součást aplikace uživatele. Všechny binární soubory by měly být umístěny pod *\redist\\<\> \\ config<\>arch*a binární názvy by měly mít následující formát, aby byla zajištěna jedinečnost: *]*\<> společnosti. \<> výrobku. \<účelu>. \<>prodlužování <em>. Například *Microsoft.Cpp.Build.dll</em>. Všechny soubory s názvy, které mohou kolidovat s názvy souborů z jiných sad SDK (například javascript, css, pri, xaml, png a jpg soubory) by měly být umístěny pod <em>\\ \redist\> \\<config\> \\<arch<\> \* sdkname s výjimkou souborů, které jsou spojeny s ovládacími prvky XAML. Tyto soubory by měly být\\ umístěny\> \\ pod\> \\ *\redist<config<arch<componentname\></em>.

4. *Složka DesignTime:* soubory, které jsou potřeba pouze v době před spuštěním/laděním a neměly by být zabaleny jako součást aplikace uživatele. Mohou to být dokumenty XML, knihovny, záhlaví, binární soubory návrhu panelu nástrojů, artefakty MSBuild atd. Každá sada SDK, která je určena ke spotřebě nativním projektem, musí mít soubor *SDKName.props.* Následující text ukazuje ukázku tohoto typu souboru.

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

    Referenční dokumenty XML jsou umístěny vedle referenčního souboru. Referenční dokument XML pro sestavení *\Reference\\<\> \\ config\><arch \sample.dll* je například *\Reference\\<konfigurace\> \\<arch\>\sample.xml*a lokalizovaná verze tohoto dokumentu *\Reference\\<config\> \\<arch\> \\<národním prostředím\>\sample.xml*.

5. *Konfigurační* složka: tři podsložky: *Ladění*, *Maloobchod*a *CommonConfiguration*. Autoři sady SDK mohou umístit své soubory do *commonconfiguration,* pokud by měla být spotřebována stejná sada souborů sady SDK, bez ohledu na konfiguraci, na kterou cílí příjemce sady SDK.

6. *Složka architektury:* jsou podporovány následující architektury: x86, x64, ARM, neutrální. Win32 mapuje na x86 a AnyCPU mapy na neutrální.

### <a name="sdkmanifestxml"></a>Soubor SDKManifest.xml

Soubor *SDKManifest.xml* popisuje, jak by měl visual studio využívat sadu SDK. Například:

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
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

V následujícím seznamu jsou uvedeny prvky souboru:

1. DisplayName: hodnota, která se zobrazí ve Správci odkazů, Průzkumníku řešení, prohlížeči objektů a dalších umístěních v uživatelském rozhraní sady Visual Studio.

2. ProductFamilyName: Celkový název produktu sady SDK. Sada [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK má například název "Microsoft.WinJS.1.0" a "Microsoft.WinJS.2.0", které patří do stejné rodiny produktů sady SDK, "Microsoft.WinJS". Tento atribut umožňuje Visual Studio a MSBuild k vytvoření tohoto připojení. Pokud tento atribut neexistuje, název sady SDK se používá jako název rodiny produktů.

3. FrameworkIdentity: Určuje závislost na jedné nebo více knihovnách součástí systému Windows. Hodnota tohoto atributu je vložena do manifestu náročné aplikace. Tento atribut je použitelný pouze pro knihovny součástí systému Windows.

4. TargetFramework: Určuje sady SDK, které jsou k dispozici ve Správci odkazů a panelu nástrojů. Toto je seznam názvů cílové horozhraní oddělených středníkem, například ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1". Pokud je zadáno několik verzí stejného cílového rozhraní, správce odkazů používá pro účely filtrování nejnižší zadanou verzi. Například pokud ".NET Framework, version=v2.0; .NET Framework, version=v4.5.1" bude program Reference Manager používat ".NET Framework, version=v2.0". Pokud je zadán konkrétní profil cílového rozhraní, bude pro účely filtrování použit pouze tento profil správcem odkazů. Pokud je například zadáno "Silverlight, version=v4.0, profile=WindowsPhone", správce odkazů filtruje pouze profil Windows Phone; projekt zaměřený na úplnou architekturu Silverlight 4.0 Framework nevidí sadu SDK ve Správci odkazů.

5. MinVSVersion: Minimální verze sady Visual Studio.

6. MaxPlatformVerson: Maximální verze cílové platformy by měla být použita k určení verze platformy, na kterých nebude fungovat sada Extension SDK. Například Balíček runtime Microsoft Visual C++ v11.0 by měl odkazovat pouze na projekty systému Windows 8. To znamená, že Windows 8 projektu MaxPlatformVersion je 8.0. To znamená, že Správce odkazů filtruje balíček microsoft visual c++ runtime pro projekt windows [!INCLUDE[win81](../debugger/includes/win81_md.md)] 8.1 a MSBuild vyvolá chybu, když na něj projekt odkazuje. Poznámka: Tento prvek je [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]podporován od začátku .

7. AppliesTo: Určuje sady SDK, které jsou k dispozici ve Správci odkazů zadáním příslušných typů projektů sady Visual Studio. Jsou rozpoznány devět hodnot: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed a Native. Autor sady SDK může používat a ("+') nebo ("&#124;"), nikoli ("!") operátory přesně určit rozsah typů projektů, které se vztahují k sdk.

    WindowsAppContainer identifikuje projekty pro [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace.

8. SupportPrefer32Bit: Podporované hodnoty jsou "True" a "False". Výchozí hodnota je "True". Pokud je hodnota nastavena na hodnotu False, [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] msbuild vrátí chybu pro projekty (nebo upozornění pro projekty plochy), pokud projekt, který odkazuje na sadu SDK má Prefer32Bit povolena. Další informace o prefer32Bit, naleznete [v tématu sestavení stránky, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) nebo [kompilace stránky, Návrhář projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: Středník oddělený seznam architektur, které podporuje sada SDK. MSBuild zobrazí upozornění, pokud není podporována cílená architektura sady SDK ve náročném projektu. Pokud tento atribut není zadán, MSBuild nikdy zobrazí tento typ upozornění.

10. SupportsMultipleVersions: Pokud je tento atribut nastaven na **chybu** nebo **upozornění**, MSBuild označuje, že stejný projekt nemůže odkazovat na více verzí stejné řady sad SDK. Pokud tento atribut neexistuje nebo je nastavena na **povolit**, MSBuild nezobrazí tento typ chyby nebo upozornění.

11. AppX: Určuje cestu k balíčkům aplikací pro knihovnu součástí Windows na disku. Tato hodnota je předána registrační součásti knihovny komponent systému Windows během místního ladění. Konvence pojmenování pro název souboru je * \<společnost>.\< produktová>. \<Architektura>. \<Konfigurační>. Verze \<>.appx*. Konfigurace a architektura jsou volitelné v názvu atributu a hodnotu atributu, pokud se nevztahují na knihovnu komponent systému Windows. Tato hodnota je použitelná pouze pro knihovny součástí systému Windows.

12. CopyRedistToSubDirectory: Určuje, kde by měly být soubory pod *\redist* složky zkopírovány vzhledem ke kořenu balíčku aplikace (to znamená **umístění balíčku** zvolenému v **průvodci vytvořením balíčku aplikace)** a kořenovému adresáři rozložení runtime. Výchozí umístění je kořen balíčku aplikace a rozložení **F5.**

13. DependsOn: Seznam identit sady SDK, které definují sady SDK, na kterých tato sada SDK závisí. Tento atribut se zobrazí v podokně podrobností správce odkazů.

14. MoreInfo: Adresa URL webové stránky, která poskytuje nápovědu a další informace. Tato hodnota se používá v odkazu Další informace v pravém podokně Správce odkazů.

15. Typ registrace: Určuje registraci WinMD v manifestu aplikace a je vyžadovánpro nativní WinMD, který má protějšek implementace DLL.

16. Odkaz na soubor: Určeno pouze pro ty odkazy, které obsahují ovládací prvky nebo jsou nativní mise WinMD. Informace o tom, jak určit, zda odkaz obsahuje ovládací prvky, naleznete [v tématu Určení umístění položek panelu nástrojů](#ToolboxItems) níže.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Určení umístění položek panelu nástrojů

Element **ToolBoxItems** schématu *SDKManifest.xml* určuje kategorii a umístění položek panelu nástrojů v sadách SDK platformy i rozšíření. Následující příklady ukazují, jak určit různá umístění. To platí pro odkazy WinMD nebo DLL.

1. Umístěte ovládací prvky do výchozí kategorie panelu nástrojů.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Umístěte ovládací prvky pod název určité kategorie.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Umístěte ovládací prvky pod názvy konkrétních kategorií.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Umístěte ovládací prvky pod názvy různých kategorií v prolnutí a Visual Studiu.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Výčet konkrétní ovládací prvky odlišně v prolnutí a Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Výčet konkrétní ovládací prvky a umístěte je pod visual studio společné cesty nebo pouze ve skupině všechny ovládací prvky.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Výčet konkrétních ovládacích prvků a zobrazit pouze určitou sadu v ChooseItems bez nich je v panelu nástrojů.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Viz také

- [Návod: Vytvoření sady SDK pomocí jazyka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Návod: Vytvoření sady SDK pomocí jazyka C# nebo jazyka Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
