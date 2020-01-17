---
title: Potlačení upozornění kompilátoru pro projekty a balíčky NuGet
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b604f6a1392353d304897a233b74c0d81fc258df
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114505"
---
# <a name="how-to-suppress-compiler-warnings"></a>Postupy: potlačení upozornění kompilátoru

Pomocí filtrování jedné nebo více druhů upozornění kompilátoru můžete declutter protokolu sestavení. Například můžete chtít zkontrolovat jenom některé z výstupu, který se vygeneruje, když nastavíte úroveň podrobností protokolu sestavení na **normální**, **podrobné**, nebo **diagnostických**. Další informace o podrobnosti najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Potlačit specifická upozornění pro C# Visual nebo F\#

Použití **sestavení** potlačit specifická upozornění pro na stránce vlastností C# a F# projekty.

1. V **Průzkumníka řešení**, vyberte projekt, ve kterém chcete potlačit upozornění.

1. V panelu nabídky zvolte **zobrazení** > **stránky vlastností**.

1. Zvolte **sestavení** stránky.

1. V **potlačit upozornění** zadejte chybových kódů upozornění, která chcete potlačit, oddělené středníky.

1. Znovu sestavte řešení.

## <a name="suppress-specific-warnings-for-c"></a>Potlačit specifická upozornění proC++

Použití **vlastnosti konfigurace** stránku vlastností můžete potlačit specifická upozornění pro projekty C++.

1. V **Průzkumníka řešení**, vyberte projekt nebo zdrojového souboru, ve kterém chcete potlačit upozornění.

1. V panelu nabídky zvolte **zobrazení** > **stránky vlastností**.

1. Zvolte **vlastnosti konfigurace** kategorie, zvolte **C/C++** kategorie a klikněte na tlačítko **Upřesnit** stránky.

1. Proveďte jeden z následujících kroků:

    - V **zakázat specifická upozornění** zadejte chybových kódů upozornění, která chcete potlačit, oddělené středníky.

    - V **zakázat specifická upozornění** zvolte **upravit** a zobrazte další možnosti.

1. Zvolte **OK** tlačítko a pak znovu sestavte řešení.

## <a name="suppress-warnings-for-visual-basic"></a>Potlačení upozornění v jazyce Visual Basic

Upozornění kompilátoru specifické pro jazyk Visual Basic můžete skrýt tak, že upravíte *.vbproj* souboru projektu. Potlačit upozornění podle *kategorie*, můžete použít [stránce Vlastnosti kompilace](../ide/reference/compile-page-project-designer-visual-basic.md). Další informace najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Chcete-li potlačit specifická upozornění v jazyce Visual Basic

Tento příklad ukazuje, jak upravit *.vbproj* souboru můžete potlačit upozornění kompilátoru specifické.

1. V **Průzkumníka řešení**, vyberte projekt, ve kterém chcete potlačit upozornění.

1. V panelu nabídky zvolte **projektu** > **uvolnit projekt**.

1. V **Průzkumník řešení**otevřete kliknutím pravým tlačítkem myši nebo místní nabídku pro projekt a pak zvolte **upravit \<ProjectName >. vbproj**.

    XML souboru projektu se otevře v editoru kódu.

1. Vyhledejte `<NoWarn>` – element pro konfiguraci sestavení je sestavujete s a přidejte jeden nebo více čísel upozornění jako hodnotu `<NoWarn>` elementu. Pokud zadáte více čísel upozornění, oddělte je čárkami.

     Následující příklad ukazuje `<NoWarn>` – element pro *ladění* konfiguraci na x x86 sestavení platformy pomocí dvou upozornění kompilátoru potlačeno:

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
   > Projekty .NET core neobsahují skupiny vlastností konfigurace sestavení ve výchozím nastavení. Potlačit upozornění v projektu .NET Core, přidejte do souboru ručně oddíl konfigurace sestavení. Příklad:
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

1. Uložit změny *.vbproj* souboru.

1. V panelu nabídky zvolte **projektu** > **znovu načíst projekt**.

1. V panelu nabídky zvolte **sestavení** > **znovu sestavit řešení**.

    **Výstup** okno přestane zobrazovat upozornění, která jste zadali.

Další informace najdete v tématu [/nowarn – možnost kompilátoru](/dotnet/visual-basic/reference/command-line-compiler/nowarn) kompilátoru příkazového řádku jazyka Visual Basic.

## <a name="suppress-warnings-for-nuget-packages"></a>Potlačení upozornění pro balíčky NuGet

V některých případech můžete chtít potlačit upozornění kompilátoru NuGet pro jeden balíček NuGet, ne pro celý projekt. Upozornění slouží účel, takže není nutné potlačení na úrovni projektu. Například jeden z NuGet upozornění zjistíte, že balíček nemusí být plně kompatibilní s vaším projektem. Pokud potlačení na úrovni projektu a později přidat další balíčky NuGet, by nikdy nevíte, pokud bylo vytváření upozornění kompatibility.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>Pro potlačení konkrétního upozornění pro jeden balíček NuGet.

1. V **Průzkumníka řešení**, vyberte balíček NuGet, které chcete potlačit upozornění kompilátoru pro.

   ![Balíček NuGet v Průzkumníku řešení](media/nuget-package-with-warning.png)

1. V nabídce klepněte pravým tlačítkem nebo kontextu vyberte **vlastnosti**.

1. V **NoWarn** pole vlastností balíčku zadejte číslo upozornění, které chcete potlačit pro tento balíček. Pokud chcete více než jeden upozornění můžete potlačit, použijte čísel upozornění oddělte čárkou.

   ![Vlastnosti balíčku NuGet](media/nuget-properties-nowarn.png)

   Upozornění zmizí z **Průzkumníka řešení** a **seznam chyb**.

## <a name="see-also"></a>Viz také:

- [Návod: Sestavení aplikace](../ide/walkthrough-building-an-application.md)
- [Postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
