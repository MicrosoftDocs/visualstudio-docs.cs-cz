---
title: Ukázka Visual Studio pro Mac
description: Visual Studio pro Mac poskytuje integrované vývojové prostředí pro sestavování aplikací .NET na macOS, včetně ASP.NET Core webů a projektů Xamarin pro iOS, Android, Mac a Xamarin. Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: a2caadd454564b389f48987e69e1bc08475affea
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190184"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Prohlídka sady Visual Studio 2019 for Mac

Visual Studio pro Mac je _integrované vývojové prostředí_ .NET na Macu, které se dá použít k úpravám, ladění a sestavování kódu a publikování aplikace. Kromě editoru kódu a ladicího programu, Visual Studio pro Mac zahrnuje kompilátory, nástroje pro dokončování kódu, grafické návrháře a funkce správy zdrojového kódu, které usnadňují proces vývoje softwaru.

Visual Studio pro Mac podporuje mnoho stejných typů souborů jako jejich protějšky v systému Windows, například `.csproj` soubory, nebo, a podporuje funkce, jako je například `.fsproj` `.sln` EditorConfig, což znamená, že můžete použít integrované vývojové prostředí (IDE), které pro vás vyhovuje nejlépe.
Vytvoření, otevření a vývoj aplikace bude známé prostředí pro kohokoli, kdo dřív používal aplikaci Visual Studio ve Windows. Navíc Visual Studio pro Mac využívá spoustu výkonných nástrojů, které jejich protějšky v systému Windows poskytují takové výkonné integrované vývojové prostředí (IDE). Platforma kompilátoru Roslyn se používá pro refaktoring a IntelliSense. Systém projektu a modul sestavení používají MSBuild a jeho zdrojový editor používá stejný základ jako Visual Studio ve Windows. Používá stejné moduly ladicího programu pro aplikace Xamarin a .NET Core a stejné návrháře pro Xamarin. iOS a Xamarin. Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Co můžu v Visual Studio pro Mac

Visual Studio pro Mac podporuje následující typy vývoje:

- ASP.NET Core webových aplikací pomocí jazyka C#, F # a podpory pro stránky Razor, JavaScript a TypeScript
- Konzolové aplikace .NET Core s C# nebo F #
- Hry a aplikace Unity pro různé platformy s využitím jazyka C #
- Aplikace pro Android, iOS, tvOS a watchOS v Xamarin pomocí C# nebo F # a XAML
- Desktopové aplikace pro kakao v C# nebo F #

V tomto článku se seznámíte s různými částmi Visual Studio pro Mac, kde se můžete podívat na některé funkce, díky kterým je vytváření těchto aplikací výkonným nástrojem.

## <a name="ide-tour"></a>Prohlídka IDE

Visual Studio pro Mac je uspořádána do několika oddílů pro správu souborů a nastavení aplikace, vytváření kódu aplikace a ladění.

## <a name="getting-started"></a>Začínáme

Při prvním spuštění sady Visual Studio 2019 pro Mac se novému uživateli zobrazí přihlašovací okno. Přihlaste se pomocí svého účet Microsoft, abyste mohli aktivovat placenou licenci (pokud ji máte) nebo propojit s předplatným Azure. Můžete stisknout **I později** a později se přihlásit pomocí položky nabídky **přihlášení k Visual Studiu >** :

![Přihlaste se ke svému účet Microsoft](media/ide-tour-2019-start-signin.png)

Pak budete mít možnost přizpůsobit IDE výběrem preferovaných klávesových zkratek: Visual Studio pro Mac, Visual Studio, Visual Studio Code nebo Xcode:

![Výběr oblíbených klávesových zkratek](media/ide-tour-2019-keyboard-shortcut.png)

Po dokončení tohoto úvodního prostředí se při každém otevření sady Visual Studio 2019 pro Mac zobrazí _okno Start_ , které zobrazuje seznam posledních projektů a tlačítka pro otevření existujícího projektu nebo vytvoření nového projektu:

![Vyberte si z posledních projektů nebo vytvořte něco nového.](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Řešení a projekty

Následující obrázek ukazuje Visual Studio pro Mac s načtenou aplikací:

![Visual Studio pro Mac s načtenou aplikací](media/ide-tour-image17.png)

Následující části obsahují přehled hlavních oblastí v Visual Studio pro Mac.

## <a name="solution-window"></a>Okno řešení

Okno řešení uspořádá projekt (y) v řešení:

![Projekty uspořádané v okně řešení](media/ide-tour-image18.png)

To je místo, kde jsou soubory zdrojového kódu, prostředků, uživatelského rozhraní a závislostí uspořádány do projektů specifických pro platformu.

Další informace o použití projektů a řešení v Visual Studio pro Mac naleznete v článku [projekty a řešení](./projects-and-solutions.md) .

## <a name="assembly-references"></a>Odkazy na sestavení

Odkazy na sestavení pro každý projekt jsou k dispozici ve složce odkazy:

![Odkazuje na složku v okně řešení.](media/ide-tour-image19.png)

Další odkazy jsou přidány pomocí dialogového okna **Upravit odkazy** , které se zobrazí Poklikáním na složku odkazy, nebo výběrem možnosti **Upravit odkazy** v jeho kontextových nabídkách:

![Dialogové okno Upravit odkazy](media/ide-tour-image20.png)

Další informace o použití odkazů v Visual Studio pro Mac naleznete v článku [Správa odkazů v projektu](./managing-references-in-a-project.md) .

## <a name="dependencies--packages"></a>Závislosti/balíčky

Všechny externí závislosti použité ve vaší aplikaci jsou uloženy ve složce závislosti nebo balíčky v závislosti na tom, zda jste v projektu .NET Core nebo Xamarin. iOS/Xamarin. Android. Tyto jsou obvykle poskytovány ve formě NuGet.

NuGet je nejoblíbenější správce balíčků pro vývoj pro .NET. Díky podpoře NuGet v aplikaci Visual Studio můžete snadno vyhledat a přidat balíčky do projektu do aplikace.

Pokud chcete do aplikace přidat závislost, klikněte pravým tlačítkem na složku závislosti/balíčky a vyberte **Přidat balíčky**:

![Přidat balíček NuGet](media/ide-tour-image21.png)

Informace o použití balíčku NuGet v aplikaci najdete v článku [zahrnutí projektu NuGet v projektu](./nuget-walkthrough.md) .

## <a name="source-editor"></a>Editor zdroje

Bez ohledu na to, zda píšete v jazyce C#, XAML nebo JavaScript, Editor kódu sdílí stejné základní komponenty se sadou Visual Studio ve Windows s zcela nativním uživatelským rozhraním.

To přináší některé z následujících funkcí:

* Nativní uživatelské rozhraní macOS (založené na verzi Cocoa) (popisky, vzhled editoru, ozdobné okraje, vykreslování textu, IntelliSense)
* Filtrování typu IntelliSense a "Zobrazit položky importu"
* Podpora nativního zadávání textu
* Podpora jazyků psaných zprava doleva a obousměrných jazyků
* Roslyn 3
* Podpora více míst vložení
* Zalamování řádků
* Aktualizované uživatelské rozhraní technologie IntelliSense
* Vylepšené hledání a nahrazování
* Podpora fragmentů kódu 
* Formátování výběru
* Vložené nabídky Návrhy

Další informace o použití editoru zdrojového kódu v Visual Studio pro Mac naleznete v dokumentaci ke [zdrojovému editoru](./source-editor.md) .

Pokud chcete, aby se karty zobrazovaly stále, můžete je využít k jejich připnutí. Tím zajistíte, že při každém spuštění projektu se vždy zobrazí karta, kterou potřebujete. Pokud chcete kartu připnout, najeďte myší na kartu a klikněte na ikonu _připnutí_ :

![Připnutí karty](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Refaktoring

Visual Studio pro Mac poskytuje dva užitečné způsoby refaktorování kódu: kontextové akce a zdrojová analýza. Další informace o těchto možnostech si můžete přečíst v článku [refaktoringu](./refactoring.md) .

## <a name="debugging"></a>Ladění

Visual Studio pro Mac mají ladicí programy, které podporují projekty .NET Core, .NET Framework, Unity a Xamarin. Visual Studio pro Mac používá ladicí program .NET Core a monofonní měkký ladicí program umožňující rozhraní IDE ladit spravovaný kód napříč všemi platformami. Další informace o ladění naleznete v článku [ladění](./debugging.md) .

Ladicí program obsahuje bohatých vizualizací pro speciální typy, jako jsou například řetězce, barvy, adresy URL a také velikosti, souřadnice a Bézierovy křivky.

Další informace o vizualizacích dat ladicího programu najdete v článku [vizualizace dat](./data-visualizations.md) .

## <a name="version-control"></a>Správa verzí

Visual Studio pro Mac se integruje se systémy správy zdrojového kódu Git a subverze. Projekty pod správou zdrojových kódů jsou označeny větví uvedenou vedle názvu řešení:

![Název větve, který označuje projekt pod správou zdrojových kódů](media/ide-tour-image22.png)

Soubory s nepotvrzenými změnami mají v okně řešení anotaci se svými ikonami, jak je znázorněno na následujícím obrázku:

![Nepotvrzené soubory v okně řešení](media/ide-tour-image23.png)

Další informace o použití správy verzí v aplikaci Visual Studio naleznete v článku Správa [verzí](./version-control.md) .

## <a name="next-steps"></a>Další kroky

- [Instalace sady Visual Studio pro Mac](installation.md)
- [Kontrola dostupných úloh](workloads.md)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Viz také

- [Rozhraní IDE sady Visual Studio (ve Windows)](/visualstudio/ide/visual-studio-ide)