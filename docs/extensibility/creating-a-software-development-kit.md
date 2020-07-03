---
title: Vytvoření sady SDK (Software Development Kit) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61e547be5f240cafccc058eb7ea2249fd492554b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904112"
---
# <a name="create-a-software-development-kit"></a>Vytvoření sady SDK (Software Development Kit)

Sada SDK (Software Development Kit) je kolekce rozhraní API, která můžete odkazovat jako na jednu položku v sadě Visual Studio. Dialogové okno **Správce odkazů** obsahuje seznam všech sad SDK, které jsou relevantní pro projekt. Když přidáte sadu SDK do projektu, rozhraní API jsou k dispozici v sadě Visual Studio.

Existují dva typy sad SDK:

- Sady SDK platforem jsou povinné komponenty pro vývoj aplikací pro platformu. [!INCLUDE[win81](../debugger/includes/win81_md.md)]Sada SDK je například nutná pro vývoj [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikací.

- Sady SDK rozšíření jsou volitelné komponenty, které šíří platformu, ale nejsou povinné pro vývoj aplikací pro tuto platformu.

V následujících částech jsou popsány obecné infrastruktury sady SDK a postup vytvoření sady SDK platformy a sady SDK rozšíření.

## <a name="platform-sdks"></a>Sady SDK platformy

Sady SDK platformy se vyžadují pro vývoj aplikací pro platformu. [!INCLUDE[win81](../debugger/includes/win81_md.md)]Sada SDK je například nutná pro vývoj aplikací pro [!INCLUDE[win81](../debugger/includes/win81_md.md)] .

### <a name="installation"></a>Instalace

Všechny sady SDK platformy se nainstalují na *HKLM\Software\Microsoft\Microsoft sady SDK \\ [TPI] \v [TPV] \\ @InstallationFolder = [kořen SDK]*. Proto se [!INCLUDE[win81](../debugger/includes/win81_md.md)] sada SDK nainstaluje na *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

### <a name="layout"></a>Layout

Sady SDK platforem mají následující rozložení:

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
| *Odkazuje na* složku | Obsahuje binární soubory, které obsahují rozhraní API, se kterými se dá zakódovat. Ty můžou zahrnovat soubory Windows metadata (WinMD) nebo sestavení. |
| *DesignTime* složka | Obsahuje soubory, které jsou potřeba pouze v době před spuštěním nebo ladění. Mezi ně můžou patřit dokumentace XML, knihovny, hlavičky, sady nástrojů pro vytváření binárních souborů v době návrhu, artefakty MSBuild a tak dále.<br /><br /> Dokumentace XML by v ideálním případě měla být umístěna do složky *\DesignTime* , ale dokumenty XML pro reference budou nadále umístěny společně s referenčním souborem v aplikaci Visual Studio. Například DOC XML pro referenci<em>\References \\ [config] \\ [arch] \sample.dll</em> bude *\References \\ [config] \\ [arch] \sample.xml*a lokalizovaná verze tohoto dokumentu bude *\References \\ [config] \\ [arch] \\ [locale] \sample.xml*. |
| *Konfigurační* složka | K dispozici můžou být jenom tři složky: *Debug*, *Retail* a *CommonConfiguration*. Autoři sady SDK mohou umístit své soubory do *CommonConfiguration* , pokud by měla být spotřebována stejná sada souborů sady SDK bez ohledu na konfiguraci, kterou bude příjemce sady SDK cílit. |
| Složka *architektury* | Může existovat libovolná podporovaná složka *architektury* . Visual Studio podporuje následující architektury: x86, x64, ARM a neutrální. Poznámka: Win32 mapuje na x86 a AnyCPU se mapuje na neutrální.<br /><br /> Nástroj MSBuild hledá v sadách SDK platformy pouze *\CommonConfiguration\neutral* . |
| *SDKManifest.xml* | Tento soubor popisuje, jak by měla sada Visual Studio využívat sadu SDK. Podívejte se na manifest sady SDK pro [!INCLUDE[win81](../debugger/includes/win81_md.md)] :<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Zobrazovaný název:** Hodnota, kterou Prohlížeč objektů zobrazuje v seznamu procházení.<br /><br /> **PlatformIdentity:** Existence tohoto atributu oznamuje sadě Visual Studio a MSBuild, že sada SDK je Platform SDK a že odkazy z nich přidané by neměly být kopírovány lokálně.<br /><br /> **TargetFramework:** Tento atribut je používán sadou Visual Studio k zajištění toho, aby sada SDK mohla využívat pouze projekty, které cílí na stejné architektury, jak je uvedeno v hodnotě tohoto atributu.<br /><br /> **MinVSVersion:** Tento atribut používá aplikace Visual Studio ke zpracování pouze sad SDK, které na něj vztahují.<br /><br /> **Odkaz:** Tento atribut musí být zadán pouze pro odkazy obsahující ovládací prvky. Informace o tom, jak určit, zda odkaz obsahuje ovládací prvky, naleznete níže. |

## <a name="extension-sdks"></a>Sady SDK rozšíření

Následující části popisují, co je třeba udělat k nasazení sady SDK rozšíření.

### <a name="installation"></a>Instalace

Sady SDK rozšíření je možné nainstalovat pro konkrétního uživatele nebo pro všechny uživatele bez zadání klíče registru. Chcete-li nainstalovat sadu SDK pro všechny uživatele, použijte následující cestu:

*% Program Files%\Microsoft SDK \<target platform\> \v<číslo verze platformy \> \ExtensionSDKs*

V případě instalace specifické pro uživatele použijte následující cestu:

*%USERPROFILE%\AppData\Local\Microsoft SDK \<target platform\> \v<číslo verze platformy \> \ExtensionSDKs*

Pokud chcete použít jiné umístění, musíte udělat jednu z následujících dvou věcí:

1. Zadejte ho do klíče registru:

     **HKLM\Software\Microsoft\Microsoft SDK \<target platform> \v<číslo verze platformy \> \ExtensionSDKs\<SDKName>\<SDKVersion>**\

     a přidejte podklíč (výchozí), který má hodnotu `<path to SDK><SDKName><SDKVersion>` .

2. Přidejte `SDKReferenceDirectoryRoot` do souboru projektu vlastnost MSBuild. Hodnota této vlastnosti je seznam adresářů oddělených středníky, ve kterých se nacházejí rozšiřující sady SDK, na které chcete odkazovat.

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

1. \\<SDKName \> \\<SDKVersion \> : název a verze sady SDK rozšíření jsou odvozeny z odpovídajících názvů složek v cestě k kořenu sady SDK. Nástroj MSBuild používá tuto identitu k nalezení sady SDK na disku a aplikace Visual Studio zobrazí tuto identitu v okně **vlastnosti** a v dialogovém okně **Správce odkazů** .

2. Složka *odkazů* : binární soubory, které obsahují rozhraní API. Můžou to být soubory nebo sestavení Windows metadata (WinMD).

3. Složka *Redist* : soubory, které jsou potřebné pro modul runtime/ladění a měly by být zabaleny jako součást aplikace uživatele. Všechny binární soubory by se měly umístit pod *\redist \\<config \> \\<\> *a binární názvy by měly mít následující formát, aby se zajistila jedinečnost: *]* \<company> . \<product> . \<purpose> . \<extension> <em>. Například * Microsoft.Cpp.Build.dll</em>. Všechny soubory s názvy, které mohou kolidovat s názvy souborů z jiných sad SDK (například JavaScript, CSS, pri, XAML, PNG a jpg), by měly být umístěny pod <em>\redist \\<config \> \\<\> \\<sdkname \> \* s výjimkou souborů, které jsou spojeny s ovládacími prvky XAML. Tyto soubory by měly být umístěny pod * \redist \\<config \> \\<\> \\<součásti \> \\ </em>.

4. *DesignTime* složka: soubory, které jsou potřeba pouze v době před spuštěním a ladění, by neměly být zabaleny jako součást aplikace uživatele. Může se jednat o dokumentaci XML, knihovny, hlavičky, sady nástrojů pro vytváření binárních souborů v době návrhu, artefakty MSBuild a tak dále. Všechny sady SDK, které jsou určené pro spotřebu v nativním projektu, musí mít soubor *SDKName. props* . Následující příklad ukazuje ukázku tohoto typu souboru.

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

    Referenční dokumenty XML jsou umístěny společně s referenčním souborem. Například referenční dokument XML pro *\References \\<config \> \\<arch \>\sample.dll* sestavení je *\References \\<config \> \\<\sample.xml\><* a lokalizovaná verze tohoto dokumentu je *\References \\<config \> \\<\sample.xml\> \\ locale \> *.

5. *Konfigurační* složka: tři podsložky: *Debug*, *Retail*a *CommonConfiguration*. Autoři sady SDK mohou umístit své soubory do *CommonConfiguration* , pokud by se měla používat stejná sada souborů sady SDK, a to bez ohledu na konfiguraci, kterou uživatel SDK zacílí.

6. Složka *architektury* : podporovány jsou následující architektury: x86, x64, ARM, neutrální. Systém Win32 mapuje na x86 a AnyCPU se mapuje na neutrální.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

Soubor *SDKManifest.xml* popisuje, jak by měla sada Visual Studio využívat sadu SDK. Například:

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

Následující seznam obsahuje prvky souboru:

1. DisplayName: hodnota, která se zobrazí ve Správci odkazů, Průzkumník řešení, Prohlížeč objektů a dalších místech v uživatelském rozhraní sady Visual Studio.

2. ProductFamilyName: celkový název produktu SDK. Například [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] sada SDK má název "Microsoft. WinJS. 1.0" a "Microsoft. WinJS. 2.0", které patří do stejné rodiny produktů sady SDK "Microsoft. WinJS". Tento atribut umožňuje aplikaci Visual Studio a MSBuild vytvořit toto připojení. Pokud tento atribut neexistuje, použije se název sady SDK jako název řady produktů.

3. FrameworkIdentity: určuje závislost pro jednu nebo více knihoven součástí Windows. Hodnota tohoto atributu je vložena do manifestu využívajícího aplikaci. Tento atribut se vztahuje pouze na knihovny součástí systému Windows.

4. TargetFramework: Určuje sady SDK, které jsou k dispozici ve Správci odkazů a sadě nástrojů. Jedná se o středníkem oddělený seznam monikerů cílového rozhraní, například ".NET Framework, verze = v 2.0; .NET Framework, verze = v 4.5.1". Pokud jsou zadány různé verze stejného cílového rozhraní, Správce odkazů používá nejnižší určenou verzi pro účely filtrování. Například pokud je zadána možnost ".NET Framework, verze = v 2.0; .NET Framework, verze = v 4.5.1", Správce odkazů použije ".NET Framework, Version = v 2.0". Pokud je zadán konkrétní profil cílového rozhraní, bude správce odkazů pro účely filtrování používat pouze tento profil. Pokud je například zadáno "Silverlight, Version = v 4.0, profil = WindowsPhone", Správce odkazů bude filtrovat pouze v profilu Windows Phone; projekt, který cílí na úplné rozhraní Silverlight 4,0, nevidí sadu SDK ve Správci odkazů.

5. MinVSVersion: minimální verze sady Visual Studio.

6. MaxPlatformVerson: maximální verze cílové platformy by se měla použít k určení verzí platformy, na kterých vaše sada SDK rozšíření nebude fungovat. Například balíček Microsoft Visual C++ Runtime v 11.0 by měl být odkazován pouze v projektech se systémem Windows 8. Proto je MaxPlatformVersion projektu Windows 8 8,0. To znamená, že správce odkazů vyfiltruje balíček Microsoft Visual C++ Runtime pro projekt Windows 8.1 a MSBuild vyvolá chybu, když na [!INCLUDE[win81](../debugger/includes/win81_md.md)] něj projekt odkazuje. Poznámka: Tento element je podporován od začátku [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] .

7. AppliesTo: Určuje sady SDK, které jsou k dispozici ve Správci odkazů, zadáním příslušných typů projektů aplikace Visual Studio. Rozpoznávají se devět hodnot: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed a Native. Autor sady SDK může použít a ("+"), nebo ("&#124;"), ne ("!") operátory pro určení přesně rozsahu typů projektu, které platí pro sadu SDK.

    WindowsAppContainer identifikuje projekty pro [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace.

8. SupportPrefer32Bit: podporované hodnoty jsou "true" a "false". Výchozí hodnota je "true". Pokud je hodnota nastavena na false, nástroj MSBuild vrátí chybu pro [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projekty (nebo upozornění pro desktopové projekty), pokud je projekt, který odkazuje na sadu SDK, Prefer32Bit povolen. Další informace o Prefer32Bit naleznete v tématu [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) nebo [Stránka Kompilovat, návrhář projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: seznam architektur, které podporuje sada SDK, oddělený středníky. Nástroj MSBuild zobrazí upozornění, pokud cílová architektura sady SDK v rámci náročného projektu není podporována. Pokud tento atribut není zadán, MSBuild nikdy nezobrazí tento typ upozornění.

10. SupportsMultipleVersions: Pokud je tento atribut nastaven na hodnotu **Error** nebo **Warning**, MSBuild indikuje, že stejný projekt nemůže odkazovat na více verzí stejné řady SDK. Pokud tento atribut neexistuje nebo je nastaven na hodnotu **Allow**, nástroj MSBuild nezobrazí tento typ chyby nebo upozornění.

11. AppX: Určuje cestu k balíčkům aplikací pro knihovnu součástí Windows na disku. Tato hodnota je předána registrační komponentě knihovny součástí systému Windows během místního ladění. Konvence pojmenování pro název souboru je * \<Company> . \<Product> . \<Architecture> \<Configuration> . \<Version> . appx*. Konfigurace a architektura jsou nepovinné v názvu atributu a v případě hodnoty atributu, pokud se nevztahují na knihovnu součástí Windows. Tato hodnota se vztahuje pouze na knihovny součástí systému Windows.

12. CopyRedistToSubDirectory: Určuje, kde se mají soubory ve složce *\redist* zkopírovat vzhledem k kořenovému adresáři balíčku aplikace (to znamená **umístění balíčku** zvolenému v průvodci **vytvořením balíčku aplikace** ) a kořenovému adresáři rozložení modulu runtime. Výchozím umístěním je kořen balíčku aplikace a rozložení **F5** .

13. DependsOn: seznam identit sady SDK, které definují sady SDK, na kterých tato sada SDK závisí. Tento atribut se zobrazí v podokně podrobností Správce odkazů.

14. MoreInfo: adresa URL webové stránky, která poskytuje podporu a další informace. Tato hodnota se používá na odkazu Další informace v pravém podokně Správce odkazů.

15. Typ registrace: Určuje registraci WinMD v manifestu aplikace a vyžaduje se pro nativní soubor WinMD, který má knihovnu DLL implementace partnerského protějšku.

16. Odkaz na soubor: zadaný pouze pro odkazy, které obsahují ovládací prvky nebo jsou nativní soubory WinMD. Informace o tom, jak určit, zda odkaz obsahuje ovládací prvky, naleznete v tématu [určení umístění položek sady nástrojů](#ToolboxItems) níže.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Zadejte umístění položek sady nástrojů.

Element **ToolBoxItems** schématu *SDKManifest.xml* určuje kategorii a umístění položek sady nástrojů v sadách SDK platforem a rozšíření. Následující příklady ukazují, jak zadat různá umístění. Tato možnost platí pro odkazy WinMD nebo DLL.

1. Umístěte ovládací prvky do výchozí kategorie sady nástrojů.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Umístěte ovládací prvky pod název konkrétní kategorie.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Umístěte ovládací prvky pod konkrétní názvy kategorií.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Umístěte ovládací prvky pod názvy různých kategorií v Blendu a v aplikaci Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Zobrazení výčtu konkrétních ovládacích prvků v Blendu a v aplikaci Visual Studio jinak.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Vypsat konkrétní ovládací prvky a umístit je do společné cesty sady Visual Studio nebo pouze do skupiny všechny ovládací prvky.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Umožňuje vytvořit výčet konkrétních ovládacích prvků a v ChooseItems zobrazovat pouze konkrétní sadu, aniž by byla v sadě nástrojů.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Viz také

- [Návod: vytvoření sady SDK pomocí jazyka C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Návod: vytvoření sady SDK pomocí jazyka C# nebo Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
