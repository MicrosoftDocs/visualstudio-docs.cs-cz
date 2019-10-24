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
ms.openlocfilehash: aec3dfb45471a3349e14419671ef1fb3b5e05db5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747948"
---
# <a name="how-to-suppress-compiler-warnings"></a>Postupy: potlačení upozornění kompilátoru

Protokol sestavení můžete vyfiltrovat tak, že filtrujete jeden nebo více druhů upozornění kompilátoru. Například můžete chtít zkontrolovat pouze některé výstupy, které jsou generovány při nastavení podrobností protokolu sestavení na **normální**, **podrobné**nebo **diagnostické**. Další informace o podrobnostech najdete v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Potlačit specifická upozornění pro C# Visual nebo F \#

Na stránce vlastností **sestavení** můžete potlačit specifická upozornění pro C# projekty F# a.

1. V **Průzkumník řešení**vyberte projekt, ve kterém chcete potlačit upozornění.

1. Na panelu nabídek vyberte možnost **zobrazit**  > **stránky vlastností**.

1. Vyberte stránku **sestavení** .

1. V poli **potlačit upozornění** určete chybové kódy upozornění, která chcete potlačit, a oddělte je středníky.

1. Znovu sestavte řešení.

## <a name="suppress-specific-warnings-for-c"></a>Potlačit specifická upozornění proC++

Na stránce **Vlastnosti konfigurace** můžete potlačit specifická upozornění pro C++ projekty.

1. V **Průzkumník řešení**vyberte projekt nebo zdrojový soubor, ve kterém chcete potlačit upozornění.

1. Na panelu nabídek vyberte možnost **zobrazit**  > **stránky vlastností**.

1. Zvolte kategorii **Vlastnosti konfigurace** , zvolte kategorii **CC++ /** kategorie a potom zvolte stránku **Upřesnit** .

1. Proveďte jeden z následujících kroků:

    - V poli **Zakázat specifická upozornění** určete chybové kódy upozornění, která chcete potlačit, a oddělte je středníkem.

    - V poli **Zakázat specifická upozornění** vyberte možnost **Upravit** a zobrazte další možnosti.

1. Klikněte na tlačítko **OK** a pak znovu sestavte řešení.

## <a name="suppress-warnings-for-visual-basic"></a>Potlačit upozornění pro Visual Basic

Můžete skrýt specifická upozornění kompilátoru pro Visual Basic úpravou souboru *. vbproj* pro projekt. Chcete-li potlačit upozornění podle *kategorie*, můžete použít [stránku vlastností kompilovat](../ide/reference/compile-page-project-designer-visual-basic.md). Další informace najdete v tématu [Konfigurace upozornění v Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Chcete-li potlačit specifická upozornění pro Visual Basic

Tento příklad ukazuje, jak upravit soubor *. vbproj* pro potlačení specifických upozornění kompilátoru.

1. V **Průzkumník řešení**vyberte projekt, ve kterém chcete potlačit upozornění.

1. Na panelu nabídek vyberte položku **projekt**  > **Uvolnit projekt**.

1. V **Průzkumník řešení**otevřete kliknutím pravým tlačítkem nebo místní nabídku pro projekt a pak zvolte **Upravit \<ProjectName >. vbproj**.

    Otevře se soubor projektu XML v editoru kódu.

1. Vyhledejte prvek `<NoWarn>` pro konfiguraci sestavení, pomocí které vytváříte, a přidejte jednu nebo více čísel upozornění jako hodnotu prvku `<NoWarn>`. Pokud zadáte více čísel upozornění, oddělte je čárkami.

     Následující příklad ukazuje prvek `<NoWarn>` pro konfiguraci *ladění* sestavení na platformě x86, se dvěma upozorněními kompilátoru potlačení:

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
   > Projekty .NET Core ve výchozím nastavení neobsahují skupiny vlastností konfigurace sestavení. Chcete-li potlačit upozornění v projektu .NET Core, přidejte do souboru oddíl konfigurace sestavení ručně. Příklad:
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

1. Uložte změny do souboru *. vbproj* .

1. Na panelu nabídek vyberte **projekt**  > **znovu načíst projekt**.

1. Na panelu nabídek vyberte možnost **sestavit**  >  znovu**Sestavit řešení**.

    V okně **výstup** se již nezobrazuje upozornění, která jste zadali.

Další informace naleznete v tématu [možnost kompilátoru/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) pro kompilátor příkazového řádku Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Potlačit upozornění pro balíčky NuGet

V některých případech můžete chtít potlačit upozornění kompilátoru NuGet pro jeden balíček NuGet, a ne pro celý projekt. Upozornění slouží k tomu, takže ho nechcete potlačit na úrovni projektu. Například jedno z upozornění NuGet oznamuje, že balíček nemusí být plně kompatibilní s vaším projektem. Pokud ji potlačíte na úrovni projektu a později přidáte další balíček NuGet, nikdy nevíte, zda bylo vyprodukováno upozornění kompatibility.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Potlačení konkrétního upozornění pro jeden balíček NuGet

1. V **Průzkumník řešení**vyberte balíček NuGet, pro který chcete potlačit upozornění kompilátoru.

   ![Balíček NuGet v Průzkumník řešení](media/nuget-package-with-warning.png)

1. V místní nabídce nebo v místní nabídce klikněte na položku **vlastnosti**.

1. V poli pro **Upozornění** vlastností balíčku zadejte číslo upozornění, které chcete pro tento balíček potlačit. Chcete-li potlačit více než jedno upozornění, oddělte čísla upozornění pomocí čárky.

   ![Vlastnosti balíčku NuGet](media/nuget-properties-nowarn.png)

   Upozornění zmizí z **Průzkumník řešení** a **Seznam chyb**.

## <a name="see-also"></a>Viz také:

- [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)
- [Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)