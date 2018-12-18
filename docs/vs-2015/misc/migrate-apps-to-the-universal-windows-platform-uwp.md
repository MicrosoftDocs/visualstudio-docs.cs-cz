---
title: Migrace aplikací na platformu Universal Windows (UPW) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8d4bc5d8e8a24483c30ac813d3253626e58dd353
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791745"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrace aplikací do Univerzální platformy Windows (UWP)
Proveďte nutné ruční změny stávajících souborů projektu pro aplikace pro Windows Store 8.1, aplikace pro Windows Phone 8.1 nebo Windows Universal aplikací vytvořených pomocí sady Visual Studio 2015 RC, tak, aby bylo možné s Visual Studio 2015 RTM. (Pokud máte projekt aplikace pro Windows i Windows Phone projektu univerzální aplikace Windows 8.1, musíte provést kroky k migraci každého projektu.)  
  
 Pomocí univerzální platformy Windows teď cílit své aplikace na jeden nebo více rodin zařízení. Pokud chcete získat další informace o funkci Universal Windows apps, podívejte se na to [Průvodce platformou](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
- [Migrujte vaše stávající C# /VB Windows Store 8.1 nebo Windows Phone 8.1 aplikace](#MigrateCSharp) použití univerzální platformu Windows.  
  
- [Migrace stávajících aplikací C++ Windows Store 8.1 nebo Windows Phone 8.1](#MigrateCPlusPlus) použití univerzální platformu Windows.  
  
- [Jsou vyžadovány pro existující aplikace Universal Windows vytvořené pomocí sady Visual Studio 2015 RC změny](#PreviousVersions).  
  
- [Jsou vyžadovány pro existující projekty testů jednotek pro aplikace Windows Universal vytvořené pomocí sady Visual Studio 2015 RC změny](#MigrateUnitTest).  
  
  Pokud nechcete tyto změny udělat, zjistěte, jak [přenášet vaše stávající aplikace](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) do nového projektu Windows Universal.  
  
##  <a name="MigrateCSharp"></a> Migrujte vaše C# /VB Windows Store 8.1 nebo Windows Phone 8.1 aplikace, které používají univerzální platformu Windows  
  
#### <a name="migrate-your-cvb-project-files"></a>Migrace souborů projektu C# /VB  
  
1.  K vyhledání které univerzální platformu Windows, který jste si nainstalovali tuto složku otevřete: **\Program soubory (x86) \Windows Kits\10\Platforms\UAP**. Obsahuje seznam složek pro jednotlivé univerzální platformy Windows, který je nainstalován. Název složky je univerzální platformu Windows verze, kterou jste nainstalovali. Například má toto zařízení s Windows 10 verze 10.0.10240.0 univerzální platformy Windows.  
  
     ![Otevřete složku, chcete-li zobrazit nainstalované verze](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Můžete nainstalovat více než jednu verzi univerzální platformu Windows. Doporučujeme používat nejnovější verzi pro vaši aplikaci.  
  
2.  Pomocí Průzkumníka souborů, přejděte do složky, kde je uložen váš projekt UPW. V této složce vytvořte soubor .json. Název souboru: project.json a potom do tohoto souboru přidejte následující obsah:  
  
    ```json  
    {  
      "dependencies": {  
        "Microsoft.ApplicationInsights": "1.0.0",  
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
      },  
      "frameworks": {  
        "uap10.0": {}  
      },  
      "runtimes": {  
        "win10-arm": {},  
        "win10-arm-aot": {},  
        "win10-x86": {},  
        "win10-x86-aot": {},  
        "win10-x64": {},  
        "win10-x64-aot": {}  
      }  
    }  
  
    ```  
  
3.  Vytvořte soubor s názvem default.rd.xml s následujícím obsahem. Pokud máte projekt jazyka Visual Basic, přidejte tento soubor do adresáře Můj projekt pro váš projekt. Pokud máte projekt C#, přidejte tento soubor do adresáře vlastnosti projektu.  
  
    ```xml  
    <?xml version="1.0"?>  
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>  
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->  
    <Assembly Dynamic="Required All" Name="*Application*"/>  
    <!-- Add your application specific runtime directives here. -->  
    </Application></Directives>  
    ```  
  
4.  Otevřete řešení, která obsahuje vaše stávající aplikace pro Windows Store 8.1 nebo aplikace pro Windows Phone 8.1 v sadě Visual Studio.  
  
5.  Klikněte pravým tlačítkem na existující projekt pro vaši aplikaci v Průzkumníku řešení a pak vyberte **uvolnit projekt**. Po uvolnění projektu znovu klikněte pravým tlačítkem na soubor projektu a zvolte Upravit soubor .csproj nebo .vbproj.  
  
     ![Klikněte pravým tlačítkem na projekt a klikněte na položku upravit](../misc/media/uap-editproject.png "UAP_EditProject")  
  
6.  Najít \<PropertyGroup > element, který obsahuje \<TargetPlatformVersion > element s hodnotou 8.1. Proveďte následující kroky pro tento \<PropertyGroup > element:  
  
    1.  Nastavte hodnotu \<platformy > element: **x86**.  
  
    2.  Přidat \<TargetPlatformIdentifier > element a nastavte jej na hodnotu: **UAP**.  
  
    3.  Přepište stávající hodnotu vlastnosti \<TargetPlatformVersion > element bude hodnota, kterou jste nainstalovali verzi univerzální platformu Windows. Také přidat \<prvkem TargetPlatformMinVersion > element a poskytněte stejnou hodnotu.  
  
    4.  Změňte hodnotu \<MinimumVisualStudioVersion > element: **14**.  
  
    5.  Nahradit \<ProjectTypeGuids > element, jak je znázorněno níže:  
  
         Pro C#:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        ```  
  
         VB:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        ```  
  
    6.  Přidat \<EnableDotNetNativeCompatibleProfile > element a nastavte jej na hodnotu: **true**.  
  
    7.  Výchozí asset škálování pro Universal Windows apps je 200. Pokud váš projekt obsahuje prostředky, ne škálovat s hodnotou 200, budete muset přidat \<UapDefaultAssetScale > element s hodnotou škálování vašich prostředků na tomto PropertyGroup. Další informace o [prostředky a škálování](http://msdn.microsoft.com/library/jj679352.aspx).  
  
         Teď vaše \<PropertyGroup > prvek by měl vypadat nějak takto:  
  
        ```xml  
        <PropertyGroup>  
            …  
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>  
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>  
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>  
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
7.  Nahraďte všechny výskyty 12.0 14.0 tak, aby odrážely verze sady Visual Studio, že teď používáte. Podobně jako tato instance:  
  
    ```xml  
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
    ```  
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">  
        <VisualStudioVersion>14.0</VisualStudioVersion>  
    ```  
  
8.  Najít \<PropertyGroup > elementy, které jsou nakonfigurované pro platformy AnyCPU v rámci atributu Condition. Odebrání těchto prvků a všechny jeho podřízené položky. AnyCPU není podporována pro aplikace pro Windows 10 v sadě Visual Studio 2015. Například byste měli odebrat \<PropertyGroup > elementy, jako jsou tyto značky:  
  
    ```xml  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
    ```  
  
9. Pro každý zbývající \<PropertyGroup > element, zkontrolujte, jestli element má atribut podmínku s konfiguraci vydané verze. Pokud ano, ale neobsahuje \<UseDotNetNativeToolchain > element, ho přidat. Nastavte hodnotu \<UseDotNetNativeToolchain > prvku na hodnotu true, a to takto:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">  
        <OutputPath>bin\x64\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <Optimize>true</Optimize>  
        <NoWarn>;2008</NoWarn>  
        <DebugType>pdbonly</DebugType>  
        <PlatformTarget>x64</PlatformTarget>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
        <ErrorReport>prompt</ErrorReport>  
        <Prefer32Bit>true</Prefer32Bit>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
10. Pro Windows Phone projekty, odebrat pouze \<PropertyGroup > element, který obsahuje \<TargetPlatformIdentifier > element s hodnotou WindowsPhoneApp. Odstranit také všechny podřízené objekty tohoto elementu:  
  
    ```xml  
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">  
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>  
    </PropertyGroup>  
    ```  
  
11. Najít \<ItemGroup > element, který obsahuje \<AppxManifest > element. Přidejte následující \<žádný > jako podřízený element \<ItemGroup > element:  
  
    ```xml  
    <None Include="project.json" />  
    ```  
  
12. Najít \<ItemGroup > element, který obsahuje další prostředky, které jsou přidány do projektu, jako je například logo soubory ve formátu PNG (\<obsahu Include="Assets\Logo.scale-100.png" / >). Přidejte následující \<obsahu > podřízený element tohoto \<ItemGroup > element:  
  
     **Pro jazyk C#:**  
  
    ```xml  
    <Content Include="Properties\default.rd.xml" />  
    ```  
  
     **VB:**  
  
    ```xml  
    <Content Include="My Project\default.rd.xml" />  
    ```  
  
13. Najít \<ItemGroup > element, který zahrnuje \<odkaz > podřízených prvků, které se balíčky NuGet. Poznamenejte si balíčky NuGet, které můžete použít, protože budete muset po opětovném načtení nástroje vašeho projektu si je stáhnout pomocí Správce balíčků NuGet. Tohle odebrat \<ItemGroup > spolu s jeho podřízené položky. Projekt UWP může mít například následující balíčky NuGet, které je potřeba odebrat:  
  
    ```xml  
    <ItemGroup>  
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
      </ItemGroup>  
    ```  
  
14. Uložte provedené změny.  
  
15. Zavřete soubor .csproj nebo .vbproj.  
  
16. Klikněte pravým tlačítkem na projekt v Průzkumníku řešení a v místní nabídce zvolte možnost znovu načíst projekt. Všechny soubory ve vašem projektu by teď mělo být zobrazené v Průzkumníku řešení.  
  
17. Pomocí Správce NuGet zpět přidat balíčky, které jste odstranili v dřívějším kroku.  
  
     Teď je potřeba použít postup [aktualizujte soubory manifestu balíčku](#PackageManifest) pro všechny projekty Windows Store 8.1 nebo Windows Phone 8.1.  
  
##  <a name="MigrateCPlusPlus"></a> Migrace vaší aplikace C++ Windows Store 8.1 nebo Windows Phone 8.1, které používají univerzální platformu Windows  
  
#### <a name="migrate-your-c-project-files"></a>Přenést soubory projektu C++  
  
1.  K vyhledání které univerzální platformu Windows, který jste si nainstalovali tuto složku otevřete: **\Program soubory (x86) \Windows Kits\10\Platforms\UAP**. Obsahuje seznam složek pro jednotlivé univerzální platformy Windows, který je nainstalován. Název složky je univerzální platformu Windows verze, kterou jste nainstalovali. Například má toto zařízení s Windows 10 verze 10.0.10240.0 univerzální platformy Windows.  
  
     ![Otevřete složku, chcete-li zobrazit nainstalované verze](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Můžete nainstalovat více než jednu verzi univerzální platformu Windows. Doporučujeme používat nejnovější verzi pro vaši aplikaci.  
  
2.  Otevřete řešení, která obsahuje vaše stávající aplikace pro C++ Windows Store 8.1 nebo aplikace pro Windows Phone 8.1 v sadě Visual Studio.  
  
     Klikněte pravým tlačítkem na existující projekt v Průzkumníku řešení a pak vyberte **uvolnit projekt**. Po uvolnění projektu znovu klikněte pravým tlačítkem na soubor projektu a zvolte Upravit soubor .vcxproj.  
  
     ![Pravé&#45;klikněte na soubor projektu a vyberte Upravit](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")  
  
3.  Najít \<PropertyGroup > element, který obsahuje \<ApplicationTypeRevision > element s hodnotou 8.1. Proveďte následující kroky pro tento \<PropertyGroup > element:  
  
    1.  Přidat \<WindowsTargetPlatformVersion > element a \<WindowsTargetPlatformMinVersion > element a udělit jim hodnota verze univerzální platformu Windows, který jste nainstalovali.  
  
    2.  Aktualizujte hodnotu prvku ApplicationTypeRevision ze 8.1 10.0.  
  
    3.  Změňte hodnotu \<MinimumVisualStudioVersion > element: 14.  
  
    4.  Přidat \<EnableDotNetNativeCompatibleProfile > element a nastavte jej na hodnotu: true.  
  
    5.  Výchozí asset škálování pro Universal Windows apps je 200. Pokud váš projekt obsahuje prostředky, ne škálovat s hodnotou 200, budete muset přidat \<UapDefaultAssetScale > element s hodnotou škálování vašich prostředků na tomto PropertyGroup. Další informace o [prostředky a škálování](http://msdn.microsoft.com/library/jj679352.aspx).  
  
    6.  Projekty pro Windows Phone, pouze, změňte hodnotu vlastnosti \<ApplicationType > z Windows Phone pro Windows Store.  
  
         Teď vaše \<PropertyGroup > prvek by měl vypadat nějak takto:  
  
        ```xml  
        <PropertyGroup>  
            …  
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
             <ApplicationType>Windows Store</ApplicationType>  
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
4.  Změňte všechny instance \<PlatformToolset > prvku mají v140 hodnotu. Příklad:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
5.  Pro každý zbývající \<PropertyGroup > element, zkontrolujte, jestli element má atribut podmínku s konfiguraci vydané verze. Pokud ano, ale neobsahuje \<UseDotNetNativeToolchain > element, ho přidat. Nastavte hodnotu \<UseDotNetNativeToolchain > prvku na hodnotu true, a to takto:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
6.  Uložte provedené změny. Zavřete soubor projektu.  
  
7.  Klikněte pravým tlačítkem na soubor projektu v Průzkumníku řešení a v místní nabídce zvolte možnost znovu načíst projekt. Všechny soubory ve vašem projektu by teď mělo být zobrazené v Průzkumníku řešení.  
  
     Teď je potřeba použít postup [aktualizujte soubory manifestu balíčku](#PackageManifest) pro všechny projekty Windows Store 8.1 nebo Windows Phone 8.1.  
  
##  <a name="PackageManifest"></a> Aktualizace souboru manifestu balíčku pro projekty pro Windows Store 8.1 nebo Windows Phone 8.1  
 Je nutné aktualizovat soubor manifestu balíčku pro každý projekt ve vašem řešení.  
  
#### <a name="update-your-package-manifest-file"></a>Aktualizujte si soubor manifestu balíčku  
  
1. Otevřete soubor Package.appxmanifest ve vašem projektu. Je potřeba upravit soubor Package.AppxManifest pro jednotlivé projekty Windows Store a Windows Phone.  
  
2. Je potřeba aktualizovat \<balíčku > element s nová schémata podle vaší existující typ projektu. Nejprve odeberte následující schémata závislosti na tom, jestli máte projekt Windows Store nebo Windows Phone.  
  
    **STARÉ pro projekt Windows Store:** vaše \<balíčku > element bude vypadat podobně jako tento.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">  
  
   ```  
  
    **STARÉ pro projekt Windows Phone:** vaše \<balíčku > element bude vypadat podobně jako tento.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"  
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"  
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">  
   ```  
  
    **NOVÉ pro univerzální platformu Windows:** přidat schémata níže na vaše \<balíčku > element. Odeberte všechny přidružené obor názvů předpony identifikátoru z elementů schémat, které jste právě odebrali. Umožňuje aktualizovat vlastnost IgnorableNamespaces k: uap sady Management Pack. Vaše nová \<balíčku > prvek by měl vypadat podobně jako tento.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"  
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"  
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"  
      IgnorableNamespaces= "uap mp">  
  
   ```  
  
3. Přidat \<závislosti > podřízený element pro \<balíčku > element. Pak přidejte \<TargetDeviceFamily > podřízený element tohoto \<závislosti > element s názvem, MinVersion a MaxVersionTested atributy. Zadejte název atributu hodnota: závislosti Windows.Universal. Poskytněte MinVersion a MaxVersionTested hodnota verze univerzální platformu Windows, který jste si nainstalovali. Tento prvek by měl vypadat nějak takto:  
  
   ```xml  
   <Dependencies>  
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />  
   </Dependencies>  
   ```  
  
4. **Pro Windows Store pouze:** je třeba přidat \<mp:PhoneIdentity > podřízený element pro \<balíčku > element. Přidáte atribut PhoneProductId a PhonePublisherId atribut. Nastavte PhoneProductId mít stejnou hodnotu jako atribut Name \<Identity > element. Nastavte na hodnotu PhonePublishedId: 00000000-0000-0000-0000-000000000000. Nějak tak:  
  
   ```xml  
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />   
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>  
   ```  
  
5. Najít \<požadavky > element a odstranit tento element a všechny podřízené prvky, které obsahuje.  
  
6. Přidat **uap** obor názvů následující \<prostředků > elementy: škálování, DXFeatureLevel. Příklad:  
  
   ```xml  
   <Resources>  
     <Resource Language="en-us"/>  
    <Resource uap:Scale="180"/>  
    <Resource uap:DXFeatureLevel="dx11"/>  
   </Resources>  
  
   ```  
  
7. Přidat **uap** obor názvů následující \<funkce > elementy: documentsLibrary picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates removableStorage, události a kontakty. Příklad:  
  
   ```xml  
   <Capabilities>  
     <uap:Capability Name="documentsLibrary"/>  
     <uap:Capability Name="removableStorage"/>  
   </Capabilities>  
  
   ```  
  
8. Přidat **uap** obor názvů, aby \<VisualElements > element a všechny jeho podřízené prvky. Příklad:  
  
   ```xml  
   <uap:VisualElements  
       DisplayName="My WWA App"  
       Square150x150Logo="images/150x150.png"  
       Square44x44Logo="images/44x44.png"  
       Description="My WWA App"  
       BackgroundColor="#777777">  
     <uap:SplashScreen Image="images/splash.png"/>  
   </uap:VisualElements>  
  
   ```  
  
    **Platí jenom pro Windows Store:** názvy velikost dlaždice změnily. Změna atributů \<VisualElements > element tak, aby odrážela nové konvergované velikosti dlaždic. 70 × 70 stane 71 × 71, a 30 × 30 stane 44 × 44.  
  
    **STARÝ:** dlaždici velikost názvy  
  
   ```xml  
   <m2:VisualElements  
       …  
       Square30x30Logo="Assets\SmallLogo.png"  
       …>  
    <m2:DefaultTile  
         …  
         Square70x70Logo="images/70x70.png">  
   </m2:VisualElements>  
  
   ```  
  
    **NOVÉ:** dlaždici velikost názvy  
  
   ```xml  
   <uap:VisualElements  
       …  
       Square44x44Logo="Assets\SmallLogo.png"  
       …>  
    <uap:DefaultTile  
         …  
         Square71x71Logo="images/70x70.png">  
   </uap:VisualElements>  
  
   ```  
  
9. Přidat **uap** obor názvů, aby \<ApplicationContentUriRules > a všechny jeho podřízené prvky. Příklad:  
  
    ```xml  
    <uap:ApplicationContentUriRules>  
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>  
      <uap:Rule Type="exclude" Match="*.pdf"/>  
    </uap:ApplicationContentUriRules>  
  
    ```  
  
10. Přidat **uap** obor názvů následující \<rozšíření > elementy a všech jeho podřízených elementů: windows.accountPictureProvide, windows.alarm, windows.appointmentsProvider windows.autoPlayContent  windows.autoPlayDevice windows.cachedFileUpdate, windows.cameraSettings, windows.fileOpenPicker, windows.fileTypeAssociation, windows.fileSavePicke, windows.lockScreenCall, windows.printTaskSettings, windows.protocol, windows.search, windows.shareTarget. Příklad:  
  
    ```xml  
    <Extensions>  
      <uap:Extension Category="windows.alarm"/>  
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>  
      <uap:Extension Category="windows.protocol">  
        <uap:Protocol Name="mailto" DesiredView="useHalf">  
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>  
        </uap:Protocol>  
      </uap:Extension>  
    </Extensions>  
  
    ```  
  
11. Přidat **uap** obor názvů pro úlohy na pozadí typu chatMessageNotification. Příklad:  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
     <BackgroundTasks ServerName="MyBackgroundTasks">  
        <uap:Task Type="chatMessageNotification"/>  
      </BackgroundTasks>  
    </Extension>  
  
    ```  
  
12. Změňte závislosti rozhraní. Přidat název vydavatele do všech \<PackageDependency > elementy, a pokud ještě není zadán, zadejte MinVersion.  
  
     **STARÝ:** \<PackageDependency > – element  
  
    ```xml  
    <Dependencies>  
     <PackageDependency Name="Microsoft.VCLibs.120.00" />  
    </Dependencies>  
  
    ```  
  
     **NOVÉ:** \<PackageDependency > – element  
  
    ```xml  
    <Dependencies>  
     <PackageDependency  
          Name="Microsoft.VCLibs.120.00"  
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"  
          MinVersion="12.0.30113.0" />  
    </Dependencies>  
  
    ```  
  
     Použijte příslušné vydavatele a MinVersion hodnoty pro skutečné framework, kterou používáte. Mějte na paměti, že tyto názvy mohou změnit pro Windows 10.  
  
13. Úlohy na pozadí typu gattCharacteristicNotification a rfcommConnection nahraďte úloha typu Bluetooth. Příklad:  
  
     **STARÉ:**  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
                <Task Type="rfcommConnection"/>  
               <Task Type="gattCharacteristicNotification"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
     **NOVÉ:** s úlohou typ Bluetooth.  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
               <Task Type="bluetooth"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
14. Nahraďte bluetooth.rfcomm funkce Bluetooth zařízení a bluetooth.genericAttributeProfile obecné funkce Bluetooth. Příklad:  
  
     **STARÉ:**  
  
    ```xml  
    <Capabilities>  
      <m2:DeviceCapability Name="bluetooth.rfcomm">  
        <m2:Device Id="any">  
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">  
        <m2:Device Id="any">  
         <m2:Function Type="name:heartRate"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
    </Capabilities>  
    ```  
  
     **NOVÉ:** nahrazena obecné funkce Bluetooth.  
  
    ```xml  
    <Capabilities>  
      <uap:DeviceCapability Name="bluetooth"/>  
    </Capabilities>  
  
    ```  
  
15. Odeberte všechny nepoužívané prvky.  
  
    1. Tyto atributy pro \<VisualElements > jsou zastaralé a měly by se odebrat:  
  
       - \<VisualElements > atributy: ForegroundText, ToastCapable  
  
       - \<DefaultTile > atribut DefaultSize  
  
       - \<ApplicationView > – element  
  
         Příklad:  
  
       ```xml  
       <m2:VisualElements  
           …  
           ForegroundText="dark"  
           ToastCapable="true">  
       <m2:DefaultTile DefaultSize="square150x150Logo"/>  
         <m2:ApplicationView MinWidth="width320"/>  
       </m2:VisualElements>  
  
       ```  
  
    2. Odeberte Windows.contact a windows.contactPicker rozšíření a všechny prvky v rámci těchto rozšíření.  
  
16. Uložte soubor Package.appxmanifest. Zavřete Visual Studio.  
  
17. Budete muset odebrat některé skryté soubory předtím, než můžete znovu otevřít řešení.  
  
    1.  Otevřete Průzkumníka souborů, klikněte na tlačítko **zobrazení** v panelu nástrojů a vyberte **skryté položky** a **přípony názvu souborů, které**. Otevřít složku v počítači: \<cestu k umístění vašeho řešení >\\.vs\\\v14 {název projektu}. Pokud existuje soubor s příponou souboru .suo, odstraňte ho.  
  
    2.  Nyní přejděte zpět na složku, kde je umístěna vaše řešení. Otevřete některou ze složek pro projekty, které existují ve vašem řešení. Pokud projekt soubor některé z těchto složek. csproj.user nebo. vbproj.user rozšíření, odstraňte ho.  
  
         Teď můžete znovu otevřít řešení v sadě Visual Studio. Jste připraveni ke kódu, sestavení a ladění aplikace na univerzální platformě Windows.  
  
         Zjistěte, jak [přizpůsobení kódu](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) využívat co je nového v univerzální platformu Windows.  
  
##  <a name="PreviousVersions"></a> Změny pro existující aplikace Universal Windows vytvořené pomocí sady Visual Studio 2015 RC  
 Pokud jste vytvořili pomocí sady Visual Studio 2015 RC univerzálních aplikací pro Windows 10, budete muset projekt pomocí verze nástroje univerzální platformy Windows, které jsou nainstalovány v nejnovější verzi sady Visual Studio 2015. Všechny předchozí verze není podporována. Požadované změny se liší v závislosti na jazyku, který jste použili k vytvoření aplikace:  
  
-   [Aplikace C# /VB](#RCUpdate10CSharp)  
  
-   [Aplikace v C++](#RCUpdate10CPlusPlus)  
  
###  <a name="RCUpdate10CSharp"></a> Aktualizace projektů C# /VB používat nejnovější univerzální platformu Windows  
 Při otevření řešení pro svoje stávající aplikace, uvidíte, že vaše aplikace vyžaduje aktualizaci:  
  
 ![Zobrazení projektu v Průzkumníku řešení](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")  
  
 Pokud vyberete možnost znovu načíst tento projekt z Průzkumníku řešení, zobrazí se toto dialogové okno:  
  
 ![Změnit cíl aplikace pro použití správné sady SDK](../misc/media/missingsdkforuap.png "MissingSDKforUAP")  
  
 Protože Universal Windows Platform SDK pro váš projekt je nyní není podporován, nebude možné ji nainstalovat. Stačí kliknout na OK a pak postupujte podle následujících kroků.  
  
##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Aktualizace projektů C# /VB používat nejnovější univerzální platformu Windows  
  
1. K vyhledání které univerzální platformu Windows, který jste si nainstalovali tuto složku otevřete: **\Program soubory (x86) \Windows Kits\10\Platforms\UAP**. Obsahuje seznam složek pro jednotlivé univerzální platformy Windows, který je nainstalován. Název složky je univerzální platformu Windows verze, kterou jste nainstalovali. Například má toto zařízení s Windows 10 verze 10.0.10240.0 univerzální platformy Windows.  
  
    ![Otevřete složku, chcete-li zobrazit nainstalované verze](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
    Můžete nainstalovat více než jednu verzi univerzální platformu Windows. Doporučujeme používat nejnovější verzi pro vaši aplikaci.  
  
2. Pomocí Průzkumníka souborů, přejděte do složky, kde je uložen váš projekt UPW. Odstranit soubor packages.config a vytvořte nový soubor .json v této složce. Název souboru: project.json a potom do tohoto souboru přidejte následující obsah:  
  
   ```json  
  
   {  
     "dependencies": {  
       "Microsoft.ApplicationInsights": "1.0.0",  
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
     },  
     "frameworks": {  
       "uap10.0": {}  
     },  
     "runtimes": {  
       "win10-arm": {},  
       "win10-arm-aot": {},  
       "win10-x86": {},  
       "win10-x86-aot": {},  
       "win10-x64": {},  
       "win10-x64-aot": {}  
     }  
   }  
  
   ```  
  
3. Pomocí sady Visual Studio otevřete řešení, která obsahuje aplikaci C# /VB Universal Windows. Uvidíte, že je potřeba aktualizovat váš soubor projektu (soubor .csproj nebo .vbproj). Klikněte pravým tlačítkem na soubor projektu a zvolte pro úpravy tohoto souboru.  
  
    ![Klikněte pravým tlačítkem na projekt a klikněte na položku upravit](../misc/media/uap-editproject.png "UAP_EditProject")  
  
4. Najít \<PropertyGroup > element, který obsahuje \<TargetPlatformVersion > a \<prvkem TargetPlatformMinVersion > elementy. Přepište stávající hodnotu vlastnosti \<TargetPlatformVersion > a \<prvkem TargetPlatformMinVersion > prvků, které mají být stejná verze nástroje univerzální platformy Windows, který jste nainstalovali.  
  
    Výchozí asset škálování pro Universal Windows apps je 200. Projekty vytvořené pomocí Visual Studio 2015 RC zahrnuté prostředky škálování na 100, budete muset přidat \<UapDefaultAssetScale > element s hodnotou od 100 do této PropertyGroup. Další informace o [prostředky a škálování](http://msdn.microsoft.com/library/jj679352.aspx).  
  
5. Pokud jste přidali všechny odkazy na UPW rozšíření sady SDK (například: Mobile SDK pro Windows), budete muset aktualizovat verzi sady SDK. Například to \<sdkreference – > element:  
  
   ```xml  
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">  
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
   </SDKReference>  
  
   ```  
  
    By měl být změněn na toto:  
  
   ```xml  
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">  
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
   </SDKReference>  
  
   ```  
  
6. Najít \<cíl > element s názvem atribut, který má hodnotu: EnsureNuGetPackageBuildImports. Odstraňte tento element a všechny jeho podřízené objekty.  
  
   ```xml  
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">  
       <PropertyGroup>  
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>  
       </PropertyGroup>  
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />  
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />  
   </Target>  
   ```  
  
7. Vyhledat a odstranit \<Import > prvků s atributy projektu a podmínky, které odkazují na Microsoft.Diagnostics.Tracing.EventSource a Microsoft.ApplicationInsights, tímto způsobem:  
  
   ```xml  
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />  
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />  
  
   ```  
  
8. Najít \<ItemGroup >, který má \<odkaz > podřízených prvků, které se balíčky NuGet. Poznamenejte si balíčky NuGet, na které odkazují, protože tyto informace budete potřebovat pro další krok. Jednou z největších rozdílů mezi formát projektu Windows 10 mezi Visual Studio 2015 RC a Visual Studio 2015 RTM je, že formát RTM používá [NuGet](http://docs.nuget.org/) verze 3.  
  
    Odeberte \<ItemGroup > a všechny jeho podřízené položky. Například projekt UPW vytvořené pomocí sady Visual Studio RC bude mít následující balíčky NuGet, které je potřeba odebrat:  
  
   ```xml  
   <ItemGroup>  
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
     </ItemGroup>  
  
   ```  
  
9. Najít \<ItemGroup > element, který obsahuje \<AppxManifest > element. Dojde-li \<žádný > element s atributem zahrnout nastaveným na: souboru packages.config, odstraňte ho. Přidejte také \<žádný > element s zahrnutí atribut a nastavte jej na hodnotu: project.json.  
  
10. Uložte provedené změny. Zavřete soubor projektu.  
  
11. Klikněte pravým tlačítkem na soubor projektu v Průzkumníku řešení a v místní nabídce zvolte možnost znovu načíst projekt. Všechny soubory ve vašem projektu by teď mělo být zobrazené v Průzkumníku řešení.  
  
12. Vyberte soubor ApplicationInsights.config v Průzkumníku řešení a otevřete jeho vlastnosti. Nastavte vlastnost Akce sestavení na "Obsah" a o kopírování do výstupního adresáře vlastnost na hodnotu kopírovat, pokud je novější".  
  
13. Otevřete soubor Package.appxmanifest ve vašem projektu.  
  
    1.  Najít \<TargetDeviceFamily > element. Změňte jeho atributy MinVersion a MaxVersionTested tak, aby odpovídala verzi univerzální platformu Windows, kterou jste nainstalovali. Nějak tak:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Uložte provedené změny.  
  
14. Pomocí Správce NuGet přidejte balíčky, které jste odstranili v dřívějším kroku. Jednou z největších rozdílů mezi formát projektu Windows 10 mezi Visual Studio 2015 RC a Visual Studio 2015 RTM je, že formát RTM používá [NuGet](http://docs.nuget.org/) verze 3.  
  
    Teď můžete kód, vytvářet a ladit vaši aplikaci.  
  
    Pokud máte projektů testů jednotek pro aplikace pro Universal Windows, je třeba také dodržet [tyto kroky](#MigrateUnitTest).  
  
###  <a name="RCUpdate10CPlusPlus"></a> Aktualizujte vaše projekty C++ používaly nejnovější univerzální platformu Windows  
  
1.  K vyhledání které univerzální platformu Windows, který jste si nainstalovali tuto složku otevřete: **\Program soubory (x86) \Windows Kits\10\Platforms\UAP**. Obsahuje seznam složek pro jednotlivé univerzální platformy Windows, který je nainstalován. Název složky je univerzální platformu Windows verze, kterou jste nainstalovali. Například má toto zařízení s Windows 10 verze 10.0.10240.0 univerzální platformy Windows.  
  
     ![Otevřete složku, chcete-li zobrazit nainstalované verze](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Můžete nainstalovat více než jednu verzi univerzální platformu Windows. Doporučujeme používat nejnovější verzi pro vaši aplikaci.  
  
2.  Otevřete řešení, která obsahuje aplikaci C++ Windows Universal. Klikněte pravým tlačítkem na soubor .vcxproj pro projekt a zvolte uvolnit souboru projektu. Po projektu byl uvolněn, znovu klikněte pravým tlačítkem na soubor projektu a zvolte ho upravit.  
  
     ![Uvolněte projekt a potom upravte soubor projektu](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")  
  
3.  Vyhledání libovolné \<PropertyGroup > elementy, které neobsahují atributu podmínky, ale neobsahují \<ApplicationTypeRevision > element. Aktualizujte hodnotu ApplicationTypeRevision z 8.2 na 10.0. Přidat \<WindowsTargetPlatformVersion > a \<WindowsTargetPlatformMinVersion > element a nastavení jejich hodnot, bude hodnota, kterou jste nainstalovali verzi univerzální platformu Windows.  
  
     Přidat \<EnableDotNetNativeCompatibleProfile > element a nastavte jej na hodnotu na true, pokud prvek už neexistuje.  
  
     Výchozí asset škálování pro Universal Windows apps je 200. Projekty vytvořené pomocí Visual Studio 2015 RC zahrnuté prostředky škálování na 100, budete muset přidat \<UapDefaultAssetScale > element s hodnotou od 100 do této PropertyGroup. Další informace o [prostředky a škálování](http://msdn.microsoft.com/library/jj679352.aspx).  
  
     Proto tento \<PropertyGroup > prvek nyní bude podobný tomuto:  
  
    ```xml  
    <PropertyGroup Label="Globals">  
        …  
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>  
        <ApplicationType>Windows Store</ApplicationType>  
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
        <UapDefaultAssetScale>100</UapDefaultAssetScale>  
      </PropertyGroup>  
  
    ```  
  
4.  Pro každý zbývající \<PropertyGroup > element, zkontrolujte, jestli element má atribut podmínku s konfiguraci vydané verze. Pokud ano, ale neobsahuje \<UseDotNetNativeToolchain > element, ho přidat. Nastavte hodnotu \<UseDotNetNativeToolchain > prvku na hodnotu true, a to takto:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
5.  Je potřeba aktualizovat \<EnableDotNetNativeCompatibleProfile > element a \<UseDotNetNativeToolchain > prvek umožňující .NET Native, ale .NET Native není povolený v šablonách jazyka C++.  
  
     Uložte provedené změny. Zavřete soubor projektu.  
  
6.  Klikněte pravým tlačítkem na soubor projektu v Průzkumníku řešení a v místní nabídce zvolte možnost znovu načíst projekt. Všechny soubory ve vašem projektu by teď mělo být zobrazené v Průzkumníku řešení.  
  
7.  Otevřete soubor Package.appxmanifest ve vašem projektu.  
  
    1.  Najít \<TargetDeviceFamily > element. Změňte jeho atributy MinVersion a MaxVersionTested tak, aby odpovídala verzi univerzální platformu Windows, kterou jste nainstalovali. Nějak tak:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Uložte provedené změny.  
  
         Teď můžete kód, vytvářet a ladit vaši aplikaci.  
  
         Pokud máte projektů testů jednotek pro aplikace pro Universal Windows, je třeba také dodržet [tyto kroky](#MigrateUnitTest).  
  
##  <a name="MigrateUnitTest"></a> Změny pro existující projekty testů jednotek pro aplikace Windows Universal vytvořené pomocí sady Visual Studio 2015 RC  
 Pokud jste vytvořili jednotku testovací projekty univerzálních aplikací pro Windows 10 ve Visual Studiu 2015 RC, je potřeba provést tyto další změny do svého projektu soubory, které chcete použít testovací projekty s nejnovější verzí sady Visual Studio 2015. Požadované změny se liší v závislosti na jazyku, který jste použili k vytvoření aplikace:  
  
-   [Aplikace C# /VB](#UnitTestRCUpdate10CSharp)  
  
-   [Aplikace v C++](#UnitTestRCUpdate10CPlusPlus)  
  
###  <a name="UnitTestRCUpdate10CSharp"></a> Aktualizace projektů testů jednotek vaší C# /VB  
  
1. Pomocí sady Visual Studio otevřete řešení, která obsahuje projektu C# /VB jednotkového testu. Změňte hodnotu \<OuttputType > element: AppContainerExe.  
  
   ```xml  
  
   <OutputType>AppContainerExe</OutputType>  
  
   ```  
  
2. Nahraďte tento prvek \<EnableCoreRuntime > false\</EnableCoreRuntime > s následující element:  
  
   ```xml  
  
   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
  
   ```  
  
3. Odeberte tyto řádky:  
  
   ```xml  
  
   <PropertyGroup>  
       <AppXPackage>True</AppXPackage>  
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>  
    </PropertyGroup>  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
    <PlatformTarget>AnyCPU</PlatformTarget>  
    <DebugSymbols>true</DebugSymbols>  
    <DebugType>full</DebugType>  
    <Optimize>false</Optimize>  
    <OutputPath>bin\Debug\</OutputPath>  
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
    <ErrorReport>prompt</ErrorReport>  
    <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
       <PlatformTarget>AnyCPU</PlatformTarget>  
       <DebugType>pdbonly</DebugType>  
       <Optimize>true</Optimize>  
       <OutputPath>bin\Release\</OutputPath>  
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
       <ErrorReport>prompt</ErrorReport>  
       <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
  
   ```  
  
4. Přidejte tento element \<UseDotNetNativeToolchain > true\</UseDotNetNativeToolchain > jako podřízený prvek do těchto skupin vlastnost:  
  
   ```xml  
  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">  
  
   ```  
  
5. Odstranit následující \<ItemGroup > prvky:  
  
   ```xml  
  
   <ItemGroup>  
      <Compile Include="Properties\AssemblyInfo.cs" />  
      <Compile Include="UnitTest.cs" />  
   </ItemGroup>  
   <ItemGroup>  
      <AppxManifest Include="Package.appxmanifest">  
         <SubType>Designer</SubType>  
      </AppxManifest>  
      <None Include="packages.config" />  
      <None Include="UnitTestProject1_TemporaryKey.pfx" />  
   </ItemGroup>  
   <ItemGroup>  
      <Content Include="Properties\Default.rd.xml" />  
      <Content Include="Assets\Logo.scale-240.png" />  
      <Content Include="Assets\SmallLogo.scale-240.png" />  
      <Content Include="Assets\SplashScreen.scale-240.png" />  
      <Content Include="Assets\Square71x71Logo.scale-240.png" />  
      <Content Include="Assets\StoreLogo.scale-240.png" />  
      <Content Include="Assets\WideLogo.scale-240.png" />  
   </ItemGroup>  
  
   ```  
  
    Nahraďte je tyto prvky:  
  
   ```xml  
  
   <ItemGroup>  
      <Compile Include="Properties\AssemblyInfo.cs" />  
      <Compile Include="UnitTestApp.xaml.cs">  
         <DependentUpon>UnitTestApp.xaml</DependentUpon>  
      </Compile>  
      <Compile Include="UnitTest.cs" />  
   </ItemGroup>  
   <ItemGroup>  
      <ApplicationDefinition Include="UnitTestApp.xaml">  
         <Generator>MSBuild:Compile</Generator>  
         <SubType>Designer</SubType>  
      </ApplicationDefinition>  
   </ItemGroup>  
   <ItemGroup>  
      <AppxManifest Include="Package.appxmanifest">  
         <SubType>Designer</SubType>  
      </AppxManifest>  
      <None Include="UnitTestProject1_TemporaryKey.pfx" />  
   </ItemGroup>  
   <ItemGroup>  
      <Content Include="Properties\UnitTestApp.rd.xml" />  
      <Content Include="Assets\LockScreenLogo.scale-200.png" />  
      <Content Include="Assets\SplashScreen.scale-200.png" />  
      <Content Include="Assets\Square150x150Logo.scale-200.png" />  
      <Content Include="Assets\Square44x44Logo.scale-200.png" />  
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
      <Content Include="Assets\StoreLogo.png" />  
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />  
   </ItemGroup>  
   ```  
  
6. Vytvořte nový projekt testování částí a zkopírujte soubory UnitTestApp.xaml a UnitTestApp.xaml.cs z tohoto nového projektu do existujícího projektu jednotkového testu, který se aktualizuje.  
  
7. Zkopírujte soubor UnitTestApp.rd.xml z vlastnosti složky nového projektu testování částí do složky vlastnosti existujícího projektu jednotkového testu, který se aktualizuje.  
  
8. Otevřete soubor Package.appxmanifest ve vašem projektu. Z něj odstraňte tyto prvky:  
  
   ```xml  
  
   <Applications>  
      <Application Id="vstest.executionengine.universal.App"  
            Executable="vstest.executionengine.appcontainer.uap.exe"  
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
         <uap:VisualElements  
            DisplayName="UnitTestProject1"  
            Square150x150Logo="Assets\Logo.png"  
            Square44x44Logo="Assets\SmallLogo.png"  
            Description="UnitTestProject1"  
            BackgroundColor="#464646">  
            <uap:SplashScreen Image="Assets\SplashScreen.png" />  
         </uap:VisualElements>  
      </Application>  
   </Applications>  
   <Capabilities>  
      <Capability Name="internetClientServer" />  
   </Capabilities>  
   ```  
  
    Nahraďte následující prvky tyto odstraněné prvky. Použijte příslušné hodnoty pro název projektu na základě názvu projektu, namísto UnitTestProject1 v následující prvky:  
  
   ```xml  
  
   <Applications>  
      <Application Id="vstest.executionengine.universal.App"   
            Executable="$targetnametoken$.exe"  
            EntryPoint="UnitTestProject1.App">  
         <uap:VisualElements  
               DisplayName="UnitTestProject1"  
               Square150x150Logo="Assets\Square150x150Logo.png"  
               Square44x44Logo="Assets\Square44x44Logo.png"  
               Description="UnitTestProject1"  
               BackgroundColor="transparent">  
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
            <uap:SplashScreen Image="Assets\SplashScreen.png" />  
         </uap:VisualElements>  
      </Application>  
   </Applications>  
   <Capabilities>  
      <Capability Name="internetClient" />  
   </Capabilities>  
   ```  
  
   Nyní můžete spustit testování částí.  
  
###  <a name="UnitTestRCUpdate10CPlusPlus"></a> Aktualizujte vaše projekty C++ používaly nejnovější univerzální platformu Windows  
  
1.  Pomocí sady Visual Studio otevřete řešení, která obsahuje váš projekt testu jednotek C++. Odeberte následující prvky:  
  
    ```xml  
  
    <TestApplication>true</TestApplication>  
    <AppxPackage>True</AppxPackage>  
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>  
    <EnableCoreRuntime>false</EnableCoreRuntime>  
  
    ```  
  
2.  Přidejte následující \<ProjectConfiguration > elementy tohoto elementu \<ItemGroup Label = "ProjectConfigurations" > Pokud nejsou již v tomto fille:  
  
    ```xml  
  
    <ProjectConfiguration Include="Debug|x64">  
       <Configuration>Debug</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|x64">  
       <Configuration>Release</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
  
    ```  
  
3.  Nahradí všechny výskyty tohoto prvku:  
  
    ```xml  
  
    <ConfigurationType>DynamicLibrary</ConfigurationType>  
  
    ```  
  
     tímto kódem:  
  
    ```xml  
  
    <ConfigurationType>Application</ConfigurationType>  
  
    ```  
  
4.  Přidejte tyto \<PropertyGroup > elementy, pokud nejsou ještě v souboru:  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>true</UseDebugLibraries>  
       <PlatformToolset>v140</PlatformToolset>  
    </PropertyGroup>  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>false</UseDebugLibraries>  
       <WholeProgramOptimization>true</WholeProgramOptimization>  
       <PlatformToolset>v140</PlatformToolset>  
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
    </PropertyGroup>  
  
    ```  
  
5.  Nahradí všechny výskyty tohoto prvku:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
    ```  
  
     tímto kódem:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
  
    ```  
  
6.  Nahradí všechny výskyty tohoto prvku:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
     tímto kódem:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
7.  Přidejte tyto \<ItemDefinitionGroup – > prvky v oddílu, který již obsahuje další \<ItemDefinitionGroup – > prvky:  
  
    ```xml  
  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
    <Link>  
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
    </Link>  
    </ItemDefinitionGroup>  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
       <Link>  
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
       </Link>  
    </ItemDefinitionGroup>  
  
    ```  
  
8.  Odstranit následující \< ItemGroup > element:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\Logo.scale-100.png" />  
       <Image Include="Assets\SmallLogo.scale-100.png" />  
       <Image Include="Assets\StoreLogo.scale-100.png" />  
       <Image Include="Assets\SplashScreen.scale-100.png" />  
       <Image Include="Assets\WideLogo.scale-100.png" />  
    </ItemGroup>  
  
    ```  
  
     Nahraďte ji metodou to \<ItemGroup > element:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\LockScreenLogo.scale-200.png" />  
       <Image Include="Assets\SplashScreen.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
       <Image Include="Assets\Square150x150Logo.scale-200.png" />  
       <Image Include="Assets\StoreLogo.png" />  
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />  
    </ItemGroup>  
  
    ```  
  
9. Odstranit následující \< ItemGroup > element:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
    </ItemGroup>  
    ```  
  
     Nahraďte ji metodou tyto \<ItemGroup > prvky:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
       <ClInclude Include="UnitTestApp.xaml.h">  
          <DependentUpon>UnitTestApp.xaml</DependentUpon>  
       </ClInclude>  
    </ItemGroup>  
    <ItemGroup>  
       <ApplicationDefinition Include="UnitTestApp.xaml">  
          <SubType>Designer</SubType>  
       </ApplicationDefinition>  
    </ItemGroup>  
  
    ```  
  
10. Odstraňte následující element:  
  
    ```xml  
    <ClCompile Include="UnitTest.cpp"/>  
    ```  
  
     Nahraďte ji metodou tyto \<CICompile > prvky:  
  
    ```xml  
  
    <ClCompile Include="UnitTestApp.xaml.cpp">  
       <DependentUpon>UnitTestApp.xaml</DependentUpon>  
    </ClCompile>  
    <ClCompile Include="UnitTest.cpp"/>  
  
    ```  
  
11. Přidejte tento element:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />  
    ```  
  
     Nad tento prvek v souboru:  
  
    ```xml  
  
    <ItemGroup>  
       <Xml Include="UnitTestApp.rd.xml" />  
    </ItemGroup>  
    ```  
  
12. Vytvoření nového projektu C++ testu jednotek a zkopírujte soubory UnitTestApp.xaml, UnitTestApp.xaml.cpp, UnitTestApp.xaml.h a UnitTestApp.rd.xml z projektu do existujícího projektu, který se aktualizuje.  
  
13. Otevřete soubor Package.appxmanifest ve vašem projektu. Z něj odstraňte tyto prvky:  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"  
             Executable="vstest.executionengine.appcontainer.uap.exe"  
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
          <uap:VisualElements  
             DisplayName="UnitTestProject1"  
             Square150x150Logo="Assets\Logo.png"  
             Square44x44Logo="Assets\SmallLogo.png"  
             Description="UnitTestProject1"  
             BackgroundColor="#464646">  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClientServer" />  
    </Capabilities>  
  
    ```  
  
     Nahraďte následující prvky tyto odstraněné prvky. Použijte příslušné hodnoty pro název projektu na základě názvu projektu, namísto UnitTestProject1 v následující prvky:  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"   
                Executable="$targetnametoken$.exe"  
                EntryPoint="UnitTestProject1.App">  
          <uap:VisualElements  
                DisplayName="UnitTestProject1"  
                Square150x150Logo="Assets\Square150x150Logo.png"  
                Square44x44Logo="Assets\Square44x44Logo.png"  
                Description="UnitTestProject1"  
                BackgroundColor="transparent">  
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
                <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClient" />  
    </Capabilities>  
  
    ```