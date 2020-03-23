---
title: Visual Studio pro Mac Tour
description: Visual Studio for Mac poskytuje integrované vývojové prostředí pro vytváření aplikací .NET na macOS, včetně ASP.NET základních webů a projektů Xamarin pro iOS, Android, Mac a Xamarin.Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 3d25fced1e9c9dd6431f4056b5b561f476eecb28
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984984"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Prohlídka Visual Studia 2017 pro Mac

> [!NOTE]
> Visual Studio 2019 pro Mac je [teď k dispozici](installation.md).

Visual Studio pro Mac je _vývojové prostředí integrované_ .NET na Macu, které se dá použít k úpravám, ladění a sestavení kódu a následnému publikování aplikace. Kromě očekávaných funkcí, jako je například standardní editor a ladicí program, visual studio pro Mac obsahuje kompilátory, nástroje pro dokončení kódu, grafické návrháře a správu zdrojového kódu pro proces vývoje softwaru.

Visual Studio for Mac podporuje mnoho stejných typů souborů `.csproj` `.fsproj`jako `.sln` jeho protějšek systému Windows, například , nebo soubory, a podporuje funkce, jako je EditorConfig, což znamená, že můžete použít rozhraní IDE, které vám nejlépe vyhovuje.
Vytváření, otevírání a vývoj aplikace bude známé prostředí pro každého, kdo dříve používal Visual Studio v systému Windows. Kromě toho Visual Studio pro Mac využívá mnoho výkonných nástrojů, které dělají jeho protějšek Windows tak výkonné IDE. Platforma kompilátoru Roslyn se používá pro refaktoring a IntelliSense. Jeho projektový systém a sestavení motoru používají MSBuild a jeho zdrojový editor podporuje svazky TextMate. Používá stejné ladicí moduly pro aplikace Xamarin a .NET Core a stejné návrháře pro Xamarin.iOS a Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Co můžu dělat ve Visual Studiu pro Mac

Visual Studio pro Mac podporuje následující typy vývoje:

- ASP.NET základní webové aplikace s C#, F#, a podpora pro Razor stránky, JavaScript a TypeScript
- Aplikace konzoly .NET Core s c# nebo F #
- Hry a aplikace Unity napříč platformami s C #
- Android, iOS, tvOS a watchOS aplikace v Xamarinu s C# nebo F# a XAML
- Aplikace pro kakaové plochy v C# nebo F #

Tento článek zkoumá různé části Visual Studio pro Mac, poskytuje podívejte se na některé funkce, které z něj činí výkonný nástroj pro vytváření těchto aplikací.

## <a name="ide-tour"></a>Prohlídka integrovaného vývojového prostředí (IDE)

Visual Studio for Mac je uspořádáno do několika částí pro správu souborů a nastavení aplikací, vytváření kódu aplikace a ladění.

## <a name="welcome-screen"></a>Uvítací obrazovka

Když se spustí, Visual Studio pro Mac zobrazí *úvodní obrazovku*:

![Uvítací obrazovka](media/ide-tour-image1.png)

Uvítací obrazovka obsahuje následující části:

- **Panel nástrojů** – poskytuje rychlý přístup k panelu hledání. Při načtení řešení se panel nástrojů používá k nastavení konfigurací aplikací, pro ladění a zobrazení chyb.
- **Začínáme** – Poskytuje rychlý přístup k užitečným tématům pro vývojáře, kteří začínají s Visual Studio pro Mac.
- **Nedávná řešení** – Poskytuje rychlý přístup k nedávno otevřeným řešením a také k pohodlným tlačítkům pro otevírání nebo vytváření projektů.
- **Zprávy pro vývojáře** – informační kanál, který vás bude aktualizovat o nejnovějších informacích o vývojáři microsoftu.

## <a name="solutions-and-projects"></a>Řešení a projekty

Následující obrázek znázorňuje Visual Studio pro Mac s načtenou aplikací:

![Visual Studio pro Mac s načtenou aplikací](media/ide-tour-image17.png)

Následující části poskytují přehled hlavních oblastí v Sadě Visual Studio pro Mac.

## <a name="solution-pad"></a>Podložka pro řešení

Panel řešení organizuje projekty v řešení:

![Projekty organizované v panelu řešení](media/ide-tour-image18.png)

Toto je místo, kde jsou soubory pro zdrojový kód, prostředky, uživatelské rozhraní a závislosti uspořádány do projektů specifických pro platformu.

Další informace o použití projektů a řešení v Sadě Visual Studio pro Mac najdete v článku [Projekty a řešení.](/visualstudio/mac/projects-and-solutions)

## <a name="assembly-references"></a>Odkazy na sestavení

Odkazy na sestavení pro každý projekt jsou k dispozici ve složce References:

![Složka Odkazuje na panel řešení](media/ide-tour-image19.png)

Další odkazy jsou přidány pomocí dialogového okna **Upravit odkazy,** které se zobrazí poklepáním na složku Reference nebo výběrem **možnosti Upravit odkazy** v akcích kontextové nabídky:

![Dialogové okno Upravit odkazy](media/ide-tour-image20.png)

Další informace o použití odkazů ve Visual Studiu pro Mac najdete v článku [Správa odkazů v článku projectu.](/visualstudio/mac/managing-references-in-a-project)

## <a name="dependencies--packages"></a>Závislosti / balíčky

Všechny externí závislosti používané ve vaší aplikaci jsou uloženy ve složce Závislosti nebo balíčky, v závislosti na tom, zda jste v projektu .Net Core nebo Xamarin.iOS/Xamarin.Android. Tyto jsou obvykle k dispozici ve formě NuGet.

NuGet je nejoblíbenější správce balíčků pro vývoj rozhraní .NET. S podporou NuGet sady Visual Studio můžete snadno vyhledávat a přidávat balíčky do projektu do aplikace.

Chcete-li do aplikace přidat závislost, klikněte pravým tlačítkem myši na složku Závislosti / balíčky a vyberte **přidat balíčky**:

![Přidání balíčku NuGet](media/ide-tour-image21.png)

Informace o použití balíčku NuGet v aplikaci lze nalézt v [včetně projektu NuGet v](/visualstudio/mac/nuget-walkthrough) článku projektu.

## <a name="refactoring"></a>Refaktoring

Visual Studio pro Mac poskytuje dva užitečné způsoby, jak refaktorovat váš kód: kontextové akce a zdrojová analýza. Můžete si přečíst více o nich v článku [Refaktoring.](/visualstudio/mac/refactoring)

## <a name="debugging"></a>ladění

Visual Studio pro Mac má nativní ladicí program umožňující podporu ladění pro aplikace Xamarin.iOS, Xamarin.Mac a Xamarin.Android. Visual Studio pro Mac používá Mono Soft Debugger, který je implementován do mono runtime, což umožňuje IDE ladit spravovaný kód na všech platformách. Další informace o ladění naleznete v článku [ladění.](/visualstudio/mac/debugging)

Ladicí program obsahuje bohaté vizualizéry pro speciální typy, jako jsou řetězce, barvy, adresy URL, stejně jako velikosti, souřadnice a bézierovy křivky.

Další informace o vizualizacích dat ladicího programu naleznete v článku [Vizualizace dat.](/visualstudio/mac/data-visualizations)

## <a name="version-control"></a>Správa verzí

Visual Studio pro Mac se integruje se zdrojovými řídicími systémy Git a Subversion. Projekty pod správou zdrojového kódu jsou označeny větví uvedenou vedle názvu řešení:

![Název větve pro označení projektu pod správou zdrojového kódu](media/ide-tour-image22.png)

Soubory s nepotvrzenými změnami mají poznámku o svých ikonách v podokně řešení, jak je znázorněno na následujícím obrázku:

![Nesvěřené soubory v panelu řešení](media/ide-tour-image23.png)

Další informace o použití správy verzí v sadě Visual Studio naleznete v článku [Správa verzí.](/visualstudio/mac/version-control)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Viz také

- [IDE sady Visual Studio (ve Windows)](/visualstudio/ide/visual-studio-ide)
