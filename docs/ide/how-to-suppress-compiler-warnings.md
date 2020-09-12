---
title: Potlačit upozornění pro projekty a balíčky NuGet
ms.custom: SEO-VS-2020
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33abc359dea3e1c7982e5d1689debc1f8e881106
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038579"
---
# <a name="how-to-suppress-compiler-warnings"></a>Postupy: potlačení upozornění kompilátoru

Protokol sestavení můžete vyfiltrovat tak, že filtrujete jeden nebo více druhů upozornění kompilátoru. Například můžete chtít zkontrolovat pouze některé výstupy, které jsou generovány při nastavení podrobností protokolu sestavení na **normální**, **podrobné**nebo **diagnostické**. Další informace o podrobnostech najdete v tématu [Postup: zobrazení, uložení a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Potlačit specifická upozornění pro Visual C# nebo F\#

Na stránce vlastností **sestavení** můžete potlačit specifická upozornění pro projekty v jazyce C# a F #.

1. V **Průzkumník řešení**vyberte projekt, ve kterém chcete potlačit upozornění.

1. Na panelu nabídek vyberte možnost **Zobrazit**  >  **stránky vlastností**.

1. Vyberte stránku **sestavení** .

1. V poli **potlačit upozornění** určete chybové kódy upozornění, která chcete potlačit, a oddělte je středníky.

1. Znovu sestavte řešení.

## <a name="suppress-specific-warnings-for-c"></a>Potlačit specifická upozornění pro C++

Na stránce **Vlastnosti konfigurace** můžete potlačit specifická upozornění pro projekty v jazyce C++.

1. V **Průzkumník řešení**vyberte projekt nebo zdrojový soubor, ve kterém chcete potlačit upozornění.

1. Na panelu nabídek vyberte možnost **Zobrazit**  >  **stránky vlastností**.

1. Zvolte kategorii **Vlastnosti konfigurace** , zvolte kategorii **C/C++** a pak zvolte stránku **Upřesnit** .

1. Proveďte jeden z následujících kroků:

    - V poli **Zakázat specifická upozornění** určete chybové kódy upozornění, která chcete potlačit, a oddělte je středníkem.

    - V poli **Zakázat specifická upozornění** vyberte možnost **Upravit** a zobrazte další možnosti.

1. Klikněte na tlačítko **OK** a pak znovu sestavte řešení.

## <a name="suppress-warnings-for-visual-basic"></a>Potlačit upozornění pro Visual Basic

Můžete skrýt specifická upozornění kompilátoru pro Visual Basic úpravou souboru *. vbproj* pro projekt. Chcete-li potlačit upozornění podle *kategorie*, můžete použít [stránku vlastností kompilovat](../ide/reference/compile-page-project-designer-visual-basic.md). Další informace najdete v tématu [Konfigurace upozornění v Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Chcete-li potlačit specifická upozornění pro Visual Basic

Tento příklad ukazuje, jak upravit soubor *. vbproj* pro potlačení specifických upozornění kompilátoru.

1. V **Průzkumník řešení**vyberte projekt, ve kterém chcete potlačit upozornění.

1. Na panelu **nabídek vyberte projekt**  >  **uvolnit**projekt.

1. V **Průzkumník řešení**otevřete kliknutím pravým tlačítkem myši nebo místní nabídku pro projekt a pak zvolte **Upravit \<ProjectName> . vbproj**.

    Otevře se soubor projektu XML v editoru kódu.

1. Vyhledejte `<NoWarn>` element pro konfiguraci sestavení, pomocí které vytváříte, a přidejte jednu nebo více čísel upozornění jako hodnotu `<NoWarn>` prvku. Pokud zadáte více čísel upozornění, oddělte je čárkami.

     Následující příklad ukazuje `<NoWarn>` prvek pro konfiguraci sestavení *ladění* na platformě x86 s potlačením dvou upozornění kompilátoru:

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
   > Projekty .NET Core ve výchozím nastavení neobsahují skupiny vlastností konfigurace sestavení. Chcete-li potlačit upozornění v projektu .NET Core, přidejte do souboru oddíl konfigurace sestavení ručně. Například:
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

1. Na panelu **nabídek vyberte projekt**  >  **znovu načíst projekt**.

1. Na řádku nabídek klikněte na příkaz **sestavit znovu**  >  **Sestavit řešení**.

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

## <a name="see-also"></a>Viz také

- [Návod: Vytvoření aplikace](../ide/walkthrough-building-an-application.md)
- [Postupy: zobrazování, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
