---
title: Potlačit upozornění kompilátoru pro projekty a balíčky NuGet
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b604f6a1392353d304897a233b74c0d81fc258df
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114505"
---
# <a name="how-to-suppress-compiler-warnings"></a>Postup: Potlačení upozornění kompilátoru

Protokol sestavení můžete odstranit tak, že odfiltrujete jeden nebo více druhů upozornění kompilátoru. Můžete například zkontrolovat pouze část výstupu, který je generován při nastavení podrobnosti protokolu sestavení na **normální**, **podrobné**nebo **diagnostické**. Další informace o podrobnostech naleznete v [tématu Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Potlačit specifická upozornění pro visual c# nebo f\#

Stránka vlastností **Sestavení** slouží k potlačení konkrétních upozornění pro projekty Jazyka C# a F#.

1. V **Průzkumníku řešení**zvolte projekt, ve kterém chcete potlačit upozornění.

1. Na řádku nabídek zvolte **Zobrazit** > **stránky vlastností**.

1. Zvolte stránku **Sestavení.**

1. V poli **Potlačit upozornění** zadejte chybové kódy upozornění, která chcete potlačit, oddělená středníky.

1. Znovu sestavte řešení.

## <a name="suppress-specific-warnings-for-c"></a>Potlačit konkrétní upozornění pro C++

Stránka **vlastností Vlastnosti konfigurace** slouží k potlačení konkrétních upozornění pro projekty jazyka C++.

1. V **Průzkumníku řešení**zvolte projektový nebo zdrojový soubor, ve kterém chcete potlačit upozornění.

1. Na řádku nabídek zvolte **Zobrazit** > **stránky vlastností**.

1. Zvolte kategorii **Vlastnosti konfigurace,** zvolte kategorii **C/C++** a pak zvolte stránku **Upřesnit.**

1. Proveďte jeden z následujících kroků:

    - V poli **Zakázat konkrétní upozornění** zadejte kódy chyb upozornění, která chcete potlačit, oddělená středníkem.

    - V poli **Zakázat specifická upozornění** zvolte **Upravit,** chcete-li zobrazit další možnosti.

1. Zvolte tlačítko **OK** a potom znovu vytvořte řešení.

## <a name="suppress-warnings-for-visual-basic"></a>Potlačit upozornění pro jazyk Visual Basic

Konkrétní upozornění kompilátoru pro visual basic můžete skrýt úpravou souboru *.vbproj* pro projekt. Chcete-li potlačit upozornění podle *kategorie*, můžete použít [stránku vlastností Kompilace](../ide/reference/compile-page-project-designer-visual-basic.md). Další informace naleznete [v tématu Konfigurace upozornění v jazyce Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Potlačení konkrétních upozornění pro jazyk Visual Basic

Tento příklad ukazuje, jak upravit soubor *.vbproj* potlačit konkrétní upozornění kompilátoru.

1. V **Průzkumníku řešení**zvolte projekt, ve kterém chcete potlačit upozornění.

1. Na řádku nabídek zvolte **Project** > **Unload Project**.

1. V **Průzkumníku řešení**otevřete nabídku projektu pravým tlačítkem nebo místní a pak zvolte ** \<Upravit název_projektu>.vbproj**.

    Soubor projektu XML se otevře v editoru kódu.

1. Vyhledejte `<NoWarn>` prvek pro konfiguraci sestavení, se kterou vytváříte, a přidejte `<NoWarn>` jedno nebo více čísel upozornění jako hodnotu prvku. Pokud zadáte více čísel upozornění, oddělte je čárkou.

     Následující příklad ukazuje `<NoWarn>` prvek pro konfiguraci sestavení *ladění* na platformě x86 se dvěma upozorněními kompilátoru:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > Základní projekty rozhraní .NET ve výchozím nastavení neobsahují skupiny vlastností konfigurace sestavení. Chcete-li potlačit upozornění v projektu .NET Core, přidejte oddíl konfigurace sestavení do souboru ručně. Například:
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. Uložte změny do souboru *.vbproj.*

1. Na řádku nabídek zvolte **Project** > **Reload Project**.

1. Na řádku nabídek zvolte **Build** > **Rebuild Solution**.

    **Okno Výstup** již nezobrazuje upozornění, která jste zadali.

Další informace naleznete v [možnosti kompilátoru /nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) pro kompilátor příkazového řádku jazyka Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Potlačit upozornění pro balíčky NuGet

V některých případech můžete chtít potlačit NuGet upozornění kompilátoru pro jeden balíček NuGet, namísto pro celý projekt. Upozornění slouží účelu, takže jej nechcete potlačit na úrovni projektu. Například jedno z upozornění NuGet vám řekne, že balíček nemusí být plně kompatibilní s projektem. Pokud jej potlačíte na úrovni projektu a později přidáte další balíček NuGet, nikdy byste nevěděli, pokud vytváří upozornění kompatibility.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Potlačení konkrétního upozornění pro jeden balíček NuGet

1. V **Průzkumníku řešení**vyberte balíček NuGet, pro který chcete potlačit upozornění kompilátoru.

   ![Balíček NuGet v Průzkumníku řešení](media/nuget-package-with-warning.png)

1. V nabídce pravým tlačítkem nebo v místní nabídce vyberte **vlastnosti**.

1. Do pole **NoWarn** vlastností balíčku zadejte číslo upozornění, které chcete pro tento balíček potlačit. Chcete-li potlačit více než jedno upozornění, oddělte čísla upozornění pomocí čárky.

   ![Vlastnosti balíčku NuGet](media/nuget-properties-nowarn.png)

   Upozornění zmizí z **Průzkumníka řešení** a **seznamu chyb**.

## <a name="see-also"></a>Viz také

- [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)
- [Postup: Zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
