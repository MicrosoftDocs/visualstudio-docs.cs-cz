---
title: Migrace aplikací na Univerzální platforma Windows (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76590f55b21f1609a20c6fd8eb041a41a0f82131
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656032"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrace aplikací do Univerzální platformy Windows (UWP)
Proveďte potřebné ruční změny stávajících souborů projektu pro aplikace Windows Store 8,1, Windows Phone 8,1 aplikace nebo univerzální aplikace pro Windows vytvořené pomocí sady Visual Studio 2015 RC, aby je bylo možné použít se sadou Visual Studio 2015 RTM. (Pokud máte Windows 8.1 univerzální aplikace s projektem aplikace pro Windows a projektem Windows Phone, budete muset při migraci každého projektu použít postup.)

 V Univerzální platforma Windows nyní cílíte na jednu nebo více rodiny zařízení. Pokud chcete získat další informace o univerzálních aplikacích pro Windows, přečtěte si tuto [příručku k platformě](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

- [Migrujte stávající C#aplikace/VB pro Windows Store 8,1 nebo Windows Phone 8,1](#MigrateCSharp) pro použití Univerzální platforma Windows.

- [Migrujte stávající C++ aplikace pro Windows Store 8,1 nebo Windows Phone 8,1](#MigrateCPlusPlus) , abyste mohli používat Univerzální platforma Windows.

- [Změny požadované pro existující univerzální aplikace pro Windows vytvořené pomocí sady Visual Studio 2015 RC](#PreviousVersions).

- [Změny požadované pro existující projekty testování částí pro univerzální aplikace pro Windows vytvořené pomocí sady Visual Studio 2015 RC](#MigrateUnitTest).

  Pokud nechcete provádět všechny tyto změny, přečtěte si, jak [přenést stávající aplikace](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) do nového univerzálního projektu pro Windows.

## <a name="MigrateCSharp"></a>Migrace aplikací C#/VB pro Windows Store 8,1 nebo Windows Phone 8,1 na používání Univerzální platforma Windows

#### <a name="migrate-your-cvb-project-files"></a>Migrace souborů C#projektu/VB

1. Pokud chcete zjistit, která Univerzální platforma Windows máte nainstalovanou, otevřete tuto složku: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Obsahuje seznam složek pro každou nainstalovanou Univerzální platforma Windows. Název složky je Univerzální platforma Windows verze, kterou jste nainstalovali. Například toto zařízení s Windows 10 má nainstalovanou verzi 10.0.10240.0 Univerzální platforma Windows.

     ![Otevřete složku pro zobrazení nainstalovaných verzí](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Je možné nainstalovat více než jednu verzi Univerzální platforma Windows. Doporučujeme, abyste pro svou aplikaci používali nejnovější verzi.

2. Pomocí Průzkumníka souborů přejdete do složky, ve které je váš projekt UWP uložený. V této složce vytvořte soubor. JSON. Zadejte název souboru: Project. JSON a přidejte následující obsah do tohoto souboru:

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

3. Vytvořte soubor s názvem default. Rd. XML s následujícím obsahem. Pokud máte projekt VB, přidejte tento soubor do adresáře my projektu pro váš projekt. Pokud máte C# projekt, přidejte tento soubor do adresáře Properties (vlastnosti) projektu.

    ```xml
    <?xml version="1.0"?>
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->
    <Assembly Dynamic="Required All" Name="*Application*"/>
    <!-- Add your application specific runtime directives here. -->
    </Application></Directives>
    ```

4. Otevřete řešení, které obsahuje vaši stávající aplikaci Windows Store 8,1 nebo aplikaci Windows Phone 8,1 v aplikaci Visual Studio.

5. Klikněte pravým tlačítkem na existující projekt aplikace v Průzkumník řešení a pak vyberte **Uvolnit projekt**. Po uvolnění projektu klikněte pravým tlačítkem myši na soubor projektu a vyberte možnost upravit soubor. csproj nebo. vbproj.

     ![Klikněte na projekt pravým tlačítkem a vyberte Upravit.](../misc/media/uap-editproject.png "UAP_EditProject")

6. Vyhledejte prvek \<PropertyGroup >, který obsahuje prvek \<TargetPlatformVersion > s hodnotou 8,1. Pro tento \<PropertyGroup > element proveďte následující kroky:

    1. Nastavte hodnotu \<Platform > elementu na: **x86**.

    2. Přidejte prvek \<TargetPlatformIdentifier > a nastavte jeho hodnotu na: **UAP**.

    3. Změňte existující hodnotu prvku \<TargetPlatformVersion > tak, aby byla hodnota Univerzální platforma Windows verze, kterou jste nainstalovali. Přidejte také prvek \<TargetPlatformMinVersion > a přidělte mu stejnou hodnotu.

    4. Změňte hodnotu \<MinimumVisualStudioVersion > elementu na: **14**.

    5. Nahraďte prvek \<ProjectTypeGuids >, jak je znázorněno níže:

         Pro C#:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         Pro jazyk VB:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Přidejte prvek \<EnableDotNetNativeCompatibleProfile > a nastavte jeho hodnotu na: **true**.

    7. Výchozí škála assetů pro univerzální aplikace pro Windows je 200. Pokud váš projekt obsahuje prostředky, které nejsou škálované v 200, bude nutné přidat prvek \<UapDefaultAssetScale > s hodnotou škálování prostředků do této vlastnosti Property. Přečtěte si další informace o [prostředcích a škálování](https://msdn.microsoft.com/library/jj679352.aspx).

         Nyní by váš \<PropertyGroup > element by měl vypadat podobně jako v tomto příkladu:

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

7. Nahraďte všechny výskyty 12,0.14,0 tak, aby odrážely verzi sady Visual Studio, kterou nyní používáte. Podobně jako tyto instance:

    ```xml
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

    ```
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">
        <VisualStudioVersion>14.0</VisualStudioVersion>
    ```

8. Jako součást atributu Condition Najděte \<PropertyGroup > prvky, které jsou nakonfigurované pro platformu AnyCPU. Odeberte tyto prvky a všechny její podřízené položky. AnyCPU se nepodporuje pro aplikace Windows 10 v aplikaci Visual Studio 2015. Například byste měli odebrat \<PropertyGroup > prvky, jako jsou ty:

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

9. Pro každý zbývající \<PropertyGroup > prvek ověřte, zda element má atribut Condition s konfigurací vydání. Pokud má, ale neobsahuje \<UseDotNetNativeToolchain > element, pak ho přidejte. Nastavte hodnotu prvku \<UseDotNetNativeToolchain > na hodnotu true, například:

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

10. U Windows Phonech projektů odstraňte prvek > \<PropertyGroup, který obsahuje prvek \<TargetPlatformIdentifier > s hodnotou WindowsPhoneApp. Odeberte také všechny podřízené prvky tohoto prvku:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. Vyhledejte prvek \<ItemGroup >, který obsahuje prvek \<AppxManifest >. Přidejte následující \<None > prvek jako podřízený prvek \<ItemGroup >:

    ```xml
    <None Include="project.json" />
    ```

12. Vyhledejte prvek \<ItemGroup >, který obsahuje další prostředky, které jsou přidány do projektu, například soubory loga. png (\<Content include = "Assets\Logo.scale-100.png"/>). Do tohoto \<ItemGroup > elementu přidejte následující \<Content > podřízený element:

     **Pro C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **Pro jazyk VB:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. Vyhledejte prvek \<ItemGroup >, který zahrnuje \<Reference > podřízených prvků do balíčků NuGet. Poznamenejte si balíčky NuGet, které použijete, protože je budete muset stáhnout pomocí Správce balíčků NuGet po opětovném načtení projektu. Odeberte tuto \<ItemGroup > spolu se svými podřízenými položkami. Například projekt UWP může mít následující balíčky NuGet, které je třeba odebrat:

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

15. Zavřete soubor. csproj nebo. vbproj.

16. V Průzkumník řešení klikněte pravým tlačítkem na projekt a v místní nabídce vyberte znovu načíst projekt. Všechny soubory v projektu by se teď měly zobrazit v Průzkumník řešení.

17. Pomocí Správce NuGet přidejte zpátky balíčky, které jste odstranili v předchozím kroku.

     Nyní je třeba postupovat podle kroků pro [aktualizaci souborů manifestu balíčku](#PackageManifest) pro všechny projekty Windows Store 8,1 nebo Windows Phone 8,1.

## <a name="MigrateCPlusPlus"></a>Migrace aplikací C++ pro Windows Store 8,1 nebo Windows Phone 8,1 na používání Univerzální platforma Windows

#### <a name="migrate-your-c-project-files"></a>Migrace souborů C++ projektu

1. Pokud chcete zjistit, která Univerzální platforma Windows máte nainstalovanou, otevřete tuto složku: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Obsahuje seznam složek pro každou nainstalovanou Univerzální platforma Windows. Název složky je Univerzální platforma Windows verze, kterou jste nainstalovali. Například toto zařízení s Windows 10 má nainstalovanou verzi 10.0.10240.0 Univerzální platforma Windows.

     ![Otevřete složku pro zobrazení nainstalovaných verzí](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Je možné nainstalovat více než jednu verzi Univerzální platforma Windows. Doporučujeme, abyste pro svou aplikaci používali nejnovější verzi.

2. Otevřete řešení, které obsahuje vaši stávající C++ aplikaci Windows Store 8,1 nebo aplikaci Windows Phone 8,1 v aplikaci Visual Studio.

     V Průzkumníku řešení klikněte pravým tlačítkem na existující projekt a pak vyberte **Uvolnit projekt**. Po uvolnění projektu klikněte pravým tlačítkem myši na soubor projektu a vyberte možnost upravit soubor. vcxproj.

     ![Klikněte&#45;pravým tlačítkem na soubor projektu a vyberte Upravit.](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. Vyhledejte prvek \<PropertyGroup >, který obsahuje prvek \<ApplicationTypeRevision > s hodnotou 8,1. Pro tento \<PropertyGroup > element proveďte následující kroky:

    1. Přidejte prvek \<WindowsTargetPlatformVersion > a \<WindowsTargetPlatformMinVersion > element a poskytněte jim hodnotu Univerzální platforma Windows verze, kterou jste nainstalovali.

    2. Aktualizujte hodnotu elementu ApplicationTypeRevision z 8,1 na 10,0.

    3. Změňte hodnotu \<MinimumVisualStudioVersion > elementu na: 14.

    4. Přidejte prvek \<EnableDotNetNativeCompatibleProfile > a nastavte jeho hodnotu na: true.

    5. Výchozí škála assetů pro univerzální aplikace pro Windows je 200. Pokud váš projekt obsahuje prostředky, které nejsou škálované v 200, bude nutné přidat prvek \<UapDefaultAssetScale > s hodnotou škálování prostředků do této vlastnosti Property. Přečtěte si další informace o [prostředcích a škálování](https://msdn.microsoft.com/library/jj679352.aspx).

    6. U Windows Phonech projektů změňte hodnotu \<ApplicationType > z Windows Phone na Windows Store.

         Nyní by váš \<PropertyGroup > element by měl vypadat podobně jako v tomto příkladu:

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

4. Změňte všechny instance \<PlatformToolset > prvku tak, aby v140 hodnotu. Příklad:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. Pro každý zbývající \<PropertyGroup > prvek ověřte, zda element má atribut Condition s konfigurací vydání. Pokud má, ale neobsahuje \<UseDotNetNativeToolchain > element, pak ho přidejte. Nastavte hodnotu prvku \<UseDotNetNativeToolchain > na hodnotu true, například:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

6. Uložte provedené změny. Pak zavřete soubor projektu.

7. V Průzkumník řešení klikněte pravým tlačítkem na soubor projektu a v místní nabídce vyberte znovu načíst projekt. Všechny soubory v projektu by se teď měly zobrazit v Průzkumník řešení.

     Nyní je třeba postupovat podle kroků pro [aktualizaci souborů manifestu balíčku](#PackageManifest) pro všechny projekty Windows Store 8,1 nebo Windows Phone 8,1.

## <a name="PackageManifest"></a>Aktualizace souboru manifestu balíčku pro všechny projekty Windows Store 8,1 nebo Windows Phone 8,1
 Je nutné aktualizovat soubor manifestu balíčku pro každý projekt ve vašem řešení.

#### <a name="update-your-package-manifest-file"></a>Aktualizace souboru manifestu balíčku

1. Otevřete v projektu soubor Package. appxmanifest. Je potřeba upravit soubor Package. AppxManifest pro každý z vašich projektů Windows Storu a Windows Phone.

2. Je nutné aktualizovat prvek \<Package > novými schématy na základě stávajícího typu projektu. Nejdřív odeberte níže uvedená schémata na základě toho, jestli máte Windows Store nebo Windows Phone projekt.

    **Staré pro projekt Windows Store:** Váš \<Package > prvek bude vypadat podobně jako tento.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **Staré pro Windows Phone projekt:** Váš \<Package > prvek bude vypadat podobně jako tento.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **Novinka pro Univerzální platforma Windows:** Přidejte níže uvedená schémata do prvku \<Package >. Odeberte všechny přidružené předpony identifikátoru oboru názvů z prvků pro schémata, která jste právě odebrali. Aktualizujte vlastnost IgnorableNamespaces na: UAP MP. Nový prvek \<Package > by měl vypadat podobně jako tento.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Do prvku \<Package > přidejte podřízený element \<Dependencies >. Pak do tohoto \<Dependencies > element přidejte \<TargetDeviceFamily > podřízený element s atributy Name, MinVersion a MaxVersionTested. Zadejte název atributu value: Windows. Universal. Přiřaďte hodnoty MinVersion a MaxVersionTested hodnotu verze Univerzální platforma Windows, kterou jste nainstalovali. Tento element by měl vypadat nějak takto:

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **Jenom pro Windows Store:** Do prvku \<Package > je nutné přidat \<mp:P honeIdentity > podřízený element. Přidejte atribut PhoneProductId a atribut PhonePublisherId. Nastavte PhoneProductId tak, aby měl stejnou hodnotu jako atribut Name v elementu \<Identity >. Nastavte hodnotu PhonePublishedId na: 00000000-0000-0000-0000-000000000000. Nějak tak:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Vyhledejte prvek \<Prerequisites > a odstraňte tento prvek a všechny jeho podřízené prvky.

6. Přidejte obor názvů **UAP** do následujících \<Resource > prvky: Scale, DXFeatureLevel. Příklad:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. Přidejte obor názvů **UAP** do následujících \<Capability > prvky: DocumentsLibrary, PicturesLibrary, VideosLibrary, MusicLibrary, EnterpriseAuthentication, SharedUserCertificates, removableStorage, schůzky a kontakty. Příklad:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. Přidejte obor názvů **UAP** do elementu \<VisualElements > a všech jeho podřízených elementů. Příklad:

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

    **Platí jenom pro Windows Store:** Změnily se názvy velikosti dlaždice. Změňte atributy v prvku \<VisualElements > tak, aby odrážely nové sblížené velikosti dlaždic. čtvercové se bude čtvercové a čtvercové se bude 44x44.

    **Old:** názvy velikostí dlaždic

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

    **NOVINKA:** názvy velikostí dlaždic

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

9. Přidejte obor názvů **UAP** do > \<ApplicationContentUriRules a všechny jeho podřízené prvky. Příklad:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Přidejte obor názvů **UAP** do následujících \<Extension > prvků a všech jeho podřízených elementů: Windows. accountPictureProvide, Windows. alarm, Windows. appointmentsProvider Windows. autoPlayContent, Windows. autoPlayDevice, Windows. cachedFileUpdate, Windows. cameraSettings, Windows. fileOpenPicker, Windows. fileTypeAssociation, Windows. fileSavePicke, Windows. lockScreenCall, Windows. printTaskSettings, Windows. Protocol, Windows. Search, Windows. shareTarget. Příklad:

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

11. Přidejte obor názvů **UAP** pro úlohy na pozadí typu chatMessageNotification. Příklad:

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
     <BackgroundTasks ServerName="MyBackgroundTasks">
        <uap:Task Type="chatMessageNotification"/>
      </BackgroundTasks>
    </Extension>

    ```

12. Změňte závislosti rozhraní. Přidejte název vydavatele do všech \<PackageDependency > prvky a zadejte hodnotu MinVersion, pokud již není zadána.

     **Old:** \<PackageDependency > element

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **New:** \<PackageDependency > element

    ```xml
    <Dependencies>
     <PackageDependency
          Name="Microsoft.VCLibs.120.00"
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
          MinVersion="12.0.30113.0" />
    </Dependencies>

    ```

     Pro vlastní rozhraní, které používáte, použijte odpovídající hodnoty Vydavatel a MinVersion. Pamatujte, že tyto názvy se můžou u Windows 10 změnit.

13. Nahraďte úlohy typu gattCharacteristicNotification a rfcommConnection na pozadí typem úlohy Bluetooth. Příklad:

     **PŮVODNÍM**

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
                <Task Type="rfcommConnection"/>
               <Task Type="gattCharacteristicNotification"/>
    </BackgroundTasks>
    </Extension>
    ```

     **NOVINKA:** Pomocí úlohy typ Bluetooth.

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
               <Task Type="bluetooth"/>
    </BackgroundTasks>
    </Extension>
    ```

14. Vyměňte možnosti zařízení Bluetooth Bluetooth. RFCOMM a Bluetooth. genericAttributeProfile pomocí Obecné funkce Bluetooth. Příklad:

     **PŮVODNÍM**

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

     **NOVINKA:** Nahradila obecnou funkcí Bluetooth.

    ```xml
    <Capabilities>
      <uap:DeviceCapability Name="bluetooth"/>
    </Capabilities>

    ```

15. Odebere všechny zastaralé prvky.

    1. Tyto atributy pro \<VisualElements > jsou zastaralé a měly by se odebrat:

       - Atributy \<VisualElements >: ForegroundText, ToastCapable

       - Atribut \<DefaultTile > DefaultSize

       - Element \<ApplicationView >

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

    2. Odeberte rozšíření Windows. Contact a Windows. contactPicker a všechny prvky v těchto rozšířeních.

16. Uložte soubor Package. appxmanifest. Pak zavřete Visual Studio.

17. Než budete moct řešení znovu otevřít, musíte odstranit některé skryté soubory.

    1. Otevřete Průzkumníka souborů, klikněte na tlačítko **Zobrazit** na panelu nástrojů a vyberte položku **skryté položky** a **přípony názvů souborů**. Otevřete tuto složku na vašem počítači: \<path umístění vašeho řešení > \\. vs \\ {Project Name} \v14. Pokud existuje soubor s příponou souboru. suo, odstraňte ho.

    2. Teď se vraťte do složky, kde se nachází vaše řešení. Otevřete všechny složky pro projekty, které existují ve vašem řešení. Pokud má soubor v některé z těchto složek projektu příponu. csproj. User nebo. vbproj. User a pak ho odstraňte.

         Nyní můžete řešení znovu otevřít v aplikaci Visual Studio. Jste připraveni k vytváření kódu, sestavování a ladění aplikace pomocí Univerzální platforma Windows.

         Naučte se, jak [přizpůsobit svůj kód](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) , abyste mohli využít výhod, co je nového v Univerzální platforma Windows.

## <a name="PreviousVersions"></a>Změny požadované pro existující univerzální aplikace pro Windows vytvořené pomocí sady Visual Studio 2015 RC
 Pokud jste vytvořili univerzální aplikace pro Windows 10 pomocí sady Visual Studio 2015 RC, je třeba změnit cílení projektu na použití verze Univerzální platforma Windows nainstalovaného s nejnovější vydanou verzí sady Visual Studio 2015. Žádná předchozí verze není podporována. Požadované změny se liší v závislosti na jazyku, který jste použili k vytvoření aplikace:

- [C#Aplikace/VB](#RCUpdate10CSharp)

- [C++můžou](#RCUpdate10CPlusPlus)

### <a name="RCUpdate10CSharp"></a>Aktualizujte C#své projekty/VB tak, aby používaly nejnovější Univerzální platforma Windows
 Když otevřete řešení pro existující aplikaci, uvidíte, že vaše aplikace vyžaduje aktualizaci:

 ![Zobrazit projekt v Průzkumník řešení](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Pokud se rozhodnete tento projekt znovu načíst z Průzkumník řešení, zobrazí se toto dialogové okno:

 ![Změna cílení aplikace tak, aby používala správnou sadu SDK](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Vzhledem k tomu, že sada SDK Univerzální platforma Windows pro váš projekt není teď podporovaná, nebudete ji moct instalovat. Stačí kliknout na OK a pak postupovat podle následujících pokynů.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Aktualizujte C#své projekty/VB tak, aby používaly nejnovější Univerzální platforma Windows

1. Pokud chcete zjistit, která Univerzální platforma Windows máte nainstalovanou, otevřete tuto složku: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Obsahuje seznam složek pro každou nainstalovanou Univerzální platforma Windows. Název složky je Univerzální platforma Windows verze, kterou jste nainstalovali. Například toto zařízení s Windows 10 má nainstalovanou verzi 10.0.10240.0 Univerzální platforma Windows.

    ![Otevřete složku pro zobrazení nainstalovaných verzí](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

    Je možné nainstalovat více než jednu verzi Univerzální platforma Windows. Doporučujeme, abyste pro svou aplikaci používali nejnovější verzi.

2. Pomocí Průzkumníka souborů přejdete do složky, ve které je váš projekt UWP uložený. Odstraňte soubor Packages. config a v této složce vytvořte nový soubor. JSON. Zadejte název souboru: Project. JSON a přidejte následující obsah do tohoto souboru:

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

3. V aplikaci Visual Studio otevřete řešení, které obsahuje vaši C#/VB univerzální aplikaci pro Windows. Uvidíte, že soubor projektu (soubor. csproj nebo. vbproj) se musí aktualizovat. Klikněte pravým tlačítkem myši na soubor projektu a vyberte možnost upravit tento soubor.

    ![Klikněte na projekt pravým tlačítkem a vyberte Upravit.](../misc/media/uap-editproject.png "UAP_EditProject")

4. Vyhledejte prvek \<PropertyGroup >, který obsahuje \<TargetPlatformVersion > a \<TargetPlatformMinVersion > prvky. Změňte existující hodnotu \<TargetPlatformVersion > a \<TargetPlatformMinVersion > prvky tak, aby byly stejné jako verze Univerzální platforma Windows, kterou jste nainstalovali.

    Výchozí škála assetů pro univerzální aplikace pro Windows je 200. Projekty vytvořené pomocí sady Visual Studio 2015 RC zahrnují prostředky škálované na 100, bude nutné přidat \<UapDefaultAssetScale > prvek s hodnotou 100 do této třídy Property. Přečtěte si další informace o [prostředcích a škálování](https://msdn.microsoft.com/library/jj679352.aspx).

5. Pokud jste přidali jakékoli odkazy na sady SDK rozšíření UWP (například: Windows Mobile SDK), bude nutné aktualizovat verzi sady SDK. Například \<SDKReference > prvek:

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

6. Vyhledejte prvek \<Target > s atributem Name, který má hodnotu: EnsureNuGetPackageBuildImports. Odstranit tento element a všechny jeho podřízené položky.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Vyhledejte a odstraňte prvky \<Import > s atributy projektu a podmínky odkazující na Microsoft. Diagnostics. Tracing. EventSource a Microsoft. ApplicationInsights, například:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. Vyhledejte \<ItemGroup >, které mají \<Reference > podřízených prvků do balíčků NuGet. Poznamenejte si balíčky NuGet, na které se odkazuje, protože tyto informace budete potřebovat pro budoucí krok. Jedním z významných rozdílů mezi formátem projektu Windows 10 mezi Visual Studio 2015 RC a Visual Studio 2015 RTM je, že formát RTM používá [NuGet](http://docs.nuget.org/) verze 3.

    Odeberte > \<ItemGroup a všechny její podřízené položky. Například projekt UWP vytvořený pomocí sady Visual Studio RC bude mít následující balíčky NuGet, které je třeba odebrat:

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

9. Vyhledejte prvek \<ItemGroup >, který obsahuje prvek \<AppxManifest >. Pokud existuje \<None > element s atributem include nastaveným na: Packages. config, odstraňte jej. Přidejte také prvek \<None > s atributem include a nastavte jeho hodnotu na: Project. JSON.

10. Uložte provedené změny. Pak zavřete soubor projektu.

11. V Průzkumník řešení klikněte pravým tlačítkem na soubor projektu a v místní nabídce vyberte znovu načíst projekt. Všechny soubory v projektu by se teď měly zobrazit v Průzkumník řešení.

12. V Průzkumník řešení vyberte soubor ApplicationInsights. config a otevřete jeho vlastnosti. Nastavte vlastnost Akce sestavení na obsah a vlastnost kopírovat do výstupního adresáře na kopírovat, pokud je novější.

13. Otevřete v projektu soubor Package. appxmanifest.

    1. Vyhledejte prvek \<TargetDeviceFamily >. Změňte jeho atributy MinVersion a MaxVersionTested tak, aby odpovídaly verzi Univerzální platforma Windows, kterou jste nainstalovali. Nějak tak:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Uložte provedené změny.

14. Pomocí Správce NuGet přidejte balíčky, které jste odstranili v předchozím kroku. Jedním z významných rozdílů mezi formátem projektu Windows 10 mezi Visual Studio 2015 RC a Visual Studio 2015 RTM je, že formát RTM používá [NuGet](http://docs.nuget.org/) verze 3.

    Nyní můžete vytvářet kód, sestavovat a ladit aplikaci.

    Pokud máte projekty testování částí pro univerzální aplikace pro Windows, musíte postupovat také podle [těchto kroků](#MigrateUnitTest).

### <a name="RCUpdate10CPlusPlus"></a>Aktualizujte C++ projekty tak, aby používaly nejnovější Univerzální platforma Windows

1. Pokud chcete zjistit, která Univerzální platforma Windows máte nainstalovanou, otevřete tuto složku: **\Program Files (x86) \Windows Kits\10\Platforms\UAP**. Obsahuje seznam složek pro každou nainstalovanou Univerzální platforma Windows. Název složky je Univerzální platforma Windows verze, kterou jste nainstalovali. Například toto zařízení s Windows 10 má nainstalovanou verzi 10.0.10240.0 Univerzální platforma Windows.

     ![Otevřete složku pro zobrazení nainstalovaných verzí](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Je možné nainstalovat více než jednu verzi Univerzální platforma Windows. Doporučujeme, abyste pro svou aplikaci používali nejnovější verzi.

2. Otevřete řešení, které obsahuje univerzální C++ aplikaci pro Windows. Klikněte pravým tlačítkem na soubor Project. vcxproj a vyberte možnost uvolnit soubor projektu. Po uvolnění projektu klikněte pravým tlačítkem myši na soubor projektu a vyberte možnost jej upravit.

     ![Uvolněte projekt a pak upravte soubor projektu.](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Vyhledejte jakékoli \<PropertyGroup > prvky, které neobsahují atribut podmínky, ale obsahují prvek \<ApplicationTypeRevision >. Aktualizujte hodnotu ApplicationTypeRevision z 8,2 na 10,0. Přidejte \<WindowsTargetPlatformVersion > a \<WindowsTargetPlatformMinVersion prvek > a nastavte jejich hodnoty tak, aby se staly hodnotou Univerzální platforma Windows verze, kterou jste nainstalovali.

     Přidejte prvek \<EnableDotNetNativeCompatibleProfile > a nastavte jeho hodnotu na true, pokud prvek ještě neexistuje.

     Výchozí škála assetů pro univerzální aplikace pro Windows je 200. Projekty vytvořené pomocí sady Visual Studio 2015 RC zahrnují prostředky škálované na 100, bude nutné přidat \<UapDefaultAssetScale > prvek s hodnotou 100 do této třídy Property. Přečtěte si další informace o [prostředcích a škálování](https://msdn.microsoft.com/library/jj679352.aspx).

     Takže tento \<PropertyGroup > prvek bude nyní podobný tomuto:

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

4. Pro každý zbývající \<PropertyGroup > prvek ověřte, zda element má atribut Condition s konfigurací vydání. Pokud má, ale neobsahuje \<UseDotNetNativeToolchain > element, pak ho přidejte. Nastavte hodnotu prvku \<UseDotNetNativeToolchain > na hodnotu true, například:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. Je nutné aktualizovat prvek \<EnableDotNetNativeCompatibleProfile > a prvek \<UseDotNetNativeToolchain > pro povolení .NET Native, ale v C++ šablonách není povolená možnost .NET Native.

     Uložte provedené změny. Pak zavřete soubor projektu.

6. V Průzkumník řešení klikněte pravým tlačítkem na soubor projektu a v místní nabídce vyberte znovu načíst projekt. Všechny soubory v projektu by se teď měly zobrazit v Průzkumník řešení.

7. Otevřete v projektu soubor Package. appxmanifest.

    1. Vyhledejte prvek \<TargetDeviceFamily >. Změňte jeho atributy MinVersion a MaxVersionTested tak, aby odpovídaly verzi Univerzální platforma Windows, kterou jste nainstalovali. Nějak tak:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Uložte provedené změny.

         Nyní můžete vytvářet kód, sestavovat a ladit aplikaci.

         Pokud máte projekty testování částí pro univerzální aplikace pro Windows, musíte postupovat také podle [těchto kroků](#MigrateUnitTest).

## <a name="MigrateUnitTest"></a>Změny požadované pro existující projekty testů jednotek pro univerzální aplikace pro Windows vytvořené pomocí sady Visual Studio 2015 RC
 Pokud jste vytvořili projekty testování částí pro univerzální aplikace pro Windows 10 se sadou Visual Studio 2015 RC, je nutné provést tyto dodatečné změny v souborech projektu pro použití těchto testovacích projektů s nejnovější verzí sady Visual Studio 2015. Požadované změny se liší v závislosti na jazyku, který jste použili k vytvoření aplikace:

- [C#Aplikace/VB](#UnitTestRCUpdate10CSharp)

- [C++můžou](#UnitTestRCUpdate10CPlusPlus)

### <a name="UnitTestRCUpdate10CSharp"></a>Aktualizace projektů C#testů jednotek/VB

1. V aplikaci Visual Studio otevřete řešení, které obsahuje projekt C#testů jednotek/VB. Změňte hodnotu \<OuttputType > elementu na: AppContainerExe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Nahraďte tento element \<EnableCoreRuntime > false \</EnableCoreRuntime > s následujícím elementem:

   ```xml

   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>

   ```

3. Odeberte následující řádky:

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

4. Přidejte tento prvek \<UseDotNetNativeToolchain > hodnotu true \</UseDotNetNativeToolchain > jako podřízený prvek do těchto skupin vlastností:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Odstraňte následující \<ItemGroup > prvky:

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

    Nahraďte je těmito prvky:

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

6. Vytvořte nový projekt testování částí a zkopírujte soubory UnitTestApp. XAML a UnitTestApp.xaml.cs z tohoto nového projektu do existujícího projektu testů jednotek, který aktualizujete.

7. Zkopírujte soubor UnitTestApp. Rd. XML ze složky Properties (nový projekt testu jednotky) do složky Properties (existující projekt testů jednotek), kterou aktualizujete.

8. Otevřete v projektu soubor Package. appxmanifest. Pak z něj odstraňte tyto prvky:

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

    Nahraďte tyto odstraněné elementy následujícími prvky. Použijte odpovídající hodnotu pro ProjectName na základě názvu projektu místo UnitTestProject1 v níže uvedených prvcích:

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

   Nyní můžete spustit testy jednotek.

### <a name="UnitTestRCUpdate10CPlusPlus"></a>Aktualizujte C++ projekty tak, aby používaly nejnovější Univerzální platforma Windows

1. V aplikaci Visual Studio otevřete řešení, které obsahuje projekt C++ testování částí. Odeberte následující prvky:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Přidejte následující \<ProjectConfiguration > prvky pod tento element \<ItemGroup jmenovka = "ProjectConfigurations" >, pokud již nejsou v této fille:

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

3. Nahraďte všechny výskyty tohoto prvku:

    ```xml

    <ConfigurationType>DynamicLibrary</ConfigurationType>

    ```

     tímto kódem:

    ```xml

    <ConfigurationType>Application</ConfigurationType>

    ```

4. Přidejte tyto \<PropertyGroup > prvky, pokud ještě nejsou v souboru:

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

5. Nahraďte všechny výskyty tohoto prvku:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
    ```

     tímto kódem:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>

    ```

6. Nahraďte všechny výskyty tohoto prvku:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

     tímto kódem:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

7. Přidejte tyto \<ItemDefinitionGroup > prvky do oddílu, který již obsahuje jiné prvky \<ItemDefinitionGroup >:

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

8. Odstraňte následující > prvek \< položky:

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Nahraďte tímto \<ItemGroup > elementu:

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

9. Odstraňte následující > prvek \< položky:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Nahraďte je těmito \<ItemGroup > prvky:

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

     Nahraďte je těmito \<CICompile > prvky:

    ```xml

    <ClCompile Include="UnitTestApp.xaml.cpp">
       <DependentUpon>UnitTestApp.xaml</DependentUpon>
    </ClCompile>
    <ClCompile Include="UnitTest.cpp"/>

    ```

11. Přidat tento element:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
    ```

     Nad tento prvek v souboru:

    ```xml

    <ItemGroup>
       <Xml Include="UnitTestApp.rd.xml" />
    </ItemGroup>
    ```

12. Vytvořte nový projekt testování C++ částí a zkopírujte soubory UnitTestApp. XAML, UnitTestApp. XAML. cpp, UnitTestApp. XAML. h a UnitTestApp. Rd. XML z tohoto projektu do existujícího projektu, který aktualizujete.

13. Otevřete v projektu soubor Package. appxmanifest. Pak z něj odstraňte tyto prvky:

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

     Nahraďte tyto odstraněné elementy následujícími prvky. Použijte odpovídající hodnotu pro ProjectName na základě názvu projektu místo UnitTestProject1 v níže uvedených prvcích:

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