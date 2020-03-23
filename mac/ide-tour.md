---
title: Visual Studio pro Mac Tour
description: Visual Studio for Mac poskytuje integrované vývojové prostředí pro vytváření aplikací .NET na macOS, včetně ASP.NET základních webů a projektů Xamarin pro iOS, Android, Mac a Xamarin.Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/13/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: f7686efae903912b64d8692a823d6e82592cbec9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405822"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Prohlídka Visual Studia 2019 pro Mac

Visual Studio pro Mac je _vývojové prostředí integrované_ .NET na Macu, které se dá použít k úpravám, ladění a sestavení kódu a následnému publikování aplikace. Kromě očekávaných funkcí, jako je například standardní editor a ladicí program, sada Visual Studio for Mac obsahuje kompilátory, nástroje pro dokončení kódu, grafické návrháře a správu zdrojového kódu, které usnadňují proces vývoje softwaru.

Visual Studio for Mac podporuje mnoho stejných typů souborů `.csproj` `.fsproj`jako `.sln` jeho protějšek systému Windows, například , nebo soubory, a podporuje funkce, jako je EditorConfig, což znamená, že můžete použít rozhraní IDE, které vám nejlépe vyhovuje.
Vytváření, otevírání a vývoj aplikace bude známé prostředí pro každého, kdo dříve používal Visual Studio v systému Windows. Kromě toho Visual Studio pro Mac využívá mnoho výkonných nástrojů, které dělají jeho protějšek Windows tak výkonné IDE. Platforma kompilátoru Roslyn se používá pro refaktoring a IntelliSense. Jeho projektový systém a sestavení motoru používají MSBuild a jeho zdrojový editor používá stejný základ jako Visual Studio v systému Windows. Používá stejné ladicí moduly pro aplikace Xamarin a .NET Core a stejné návrháře pro Xamarin.iOS a Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Co můžu dělat ve Visual Studiu pro Mac

Visual Studio pro Mac podporuje následující typy vývoje:

- ASP.NET základní webové aplikace s C#, F#, a podporu pro Razor stránky, JavaScript a TypeScript
- Aplikace konzoly .NET Core s c# nebo F #
- Hry a aplikace Unity napříč platformami s C #
- Android, iOS, tvOS a watchOS aplikace v Xamarinu s C# nebo F# a XAML
- Aplikace pro kakaové plochy v C# nebo F #

Tento článek zkoumá různé části Visual Studio pro Mac, poskytuje podívejte se na některé funkce, které z něj činí výkonný nástroj pro vytváření těchto aplikací.

## <a name="ide-tour"></a>Prohlídka IDE

Visual Studio for Mac je uspořádáno do několika částí pro správu souborů a nastavení aplikací, vytváření kódu aplikace a ladění.

## <a name="getting-started"></a>Začínáme

Když spustíte Visual Studio 2019 pro Mac, novým uživatelům se zobrazí přihlašovací okno. Přihlaste se pomocí svého účtu Microsoft a aktivujte placenou licenci (pokud ji máte) nebo odkazujte na předplatná Azure. Můžete stisknout **Tlačítko Udělám to později** a přihlásit se později prostřednictvím **Visual Studio > Přihlásit se** položky nabídky:

![Přihlášení k účtu Microsoft](media/ide-tour-2019-start-signin.png)

Potom budete mít možnost přizpůsobit ide výběrem upřednostňované klávesové zkratky: Visual Studio pro Mac, Visual Studio, Visual Studio Code nebo Xcode:

![Výběr oblíbených klávesových zkratek](media/ide-tour-2019-keyboard-shortcut.png)

Přihlášení uživatelé uvidí nové _počáteční okno_, které zobrazuje seznam posledních projektů a tlačítka pro otevření existujícího projektu nebo vytvoření nového:

![Vyberte si z posledních projektů nebo vytvořte něco nového](media/ide-tour-2019-start-projects.png)

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

## <a name="source-editor"></a>Editor zdroje

Bez ohledu na to, pokud píšete v jazyce C#, XAML nebo Javascriptu, editor kódu sdílí stejné základní součásti se systémem Visual Studio Windows se zcela nativním uživatelským rozhraním.

To přináší některé z následujících funkcí:

* Nativní uživatelské rozhraní macOS (založené na verzi Cocoa) (popisky, vzhled editoru, ozdobné okraje, vykreslování textu, IntelliSense)
* Filtrování typu IntelliSense a zobrazení položek importu
* Podpora nativního zadávání textu
* Podpora jazyků psaných zprava doleva a obousměrných jazyků
* Roslyn 3
* Podpora více míst vložení
* Zalamování řádků
* Aktualizované ui technologie IntelliSense
* Vylepšené hledání/nahrazování
* Podpora pro Snippet 
* Formátování výběru
* Inline žárovky

Další informace o použití editoru zdrojů v Sadě Visual Studio pro Mac najdete v dokumentaci [k Editoru zdrojů.](/visualstudio/mac/source-editor)

Chcete-li mít karty viditelné po celou dobu, můžete využít jejich připnutí. Tím zajistíte, že při každém spuštění projektu se vždy zobrazí karta, kterou potřebujete. Pokud chcete připnout kartu, najeďte na ni a klikněte na ikonu _špendlíku:_

![Připnutí karty](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Refaktoring

Visual Studio pro Mac poskytuje dva užitečné způsoby, jak refaktorovat váš kód: kontextové akce a zdrojová analýza. Můžete si přečíst více o nich v článku [Refaktoring.](/visualstudio/mac/refactoring)

## <a name="debugging"></a>ladění

Visual Studio pro Mac má ladicí program, které podporují projekty .NET Core, .NET Framework, Unity a Xamarin. Visual Studio pro Mac používá ladicí program .NET Core a mono soft debugger, což umožňuje ide ladit spravovaný kód na všech platformách. Další informace o ladění naleznete v článku [ladění.](/visualstudio/mac/debugging)

Ladicí program obsahuje bohaté vizualizéry pro speciální typy, jako jsou řetězce, barvy, adresy URL, stejně jako velikosti, souřadnice a bézierovy křivky.

Další informace o vizualizacích dat ladicího programu naleznete v článku [Vizualizace dat.](/visualstudio/mac/data-visualizations)

## <a name="version-control"></a>Správa verzí

Visual Studio pro Mac se integruje se zdrojovými řídicími systémy Git a Subversion. Projekty pod správou zdrojového kódu jsou označeny větví uvedenou vedle názvu řešení:

![Název větve pro označení projektu pod správou zdrojového kódu](media/ide-tour-image22.png)

Soubory s nepotvrzenými změnami mají poznámku o svých ikonách v podokně řešení, jak je znázorněno na následujícím obrázku:

![Nesvěřené soubory v panelu řešení](media/ide-tour-image23.png)

Další informace o použití správy verzí v sadě Visual Studio naleznete v článku [Správa verzí.](/visualstudio/mac/version-control)

## <a name="next-steps"></a>Další kroky

- [Instalace sady Visual Studio pro Mac](installation.md)
- [Kontrola dostupných úloh](workloads.md)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Viz také

- [IDE sady Visual Studio (ve Windows)](/visualstudio/ide/visual-studio-ide)
