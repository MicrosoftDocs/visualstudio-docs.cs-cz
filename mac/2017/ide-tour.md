---
title: Ukázka Visual Studio pro Mac
description: Visual Studio pro Mac poskytuje integrované vývojové prostředí pro sestavování aplikací .NET na macOS, včetně ASP.NET Core webů a projektů Xamarin pro iOS, Android, Mac a Xamarin. Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 1a187796f4f867d397662224509f8a5f72d1cc74
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862486"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Prohlídka sady Visual Studio 2017 for Mac

> [!NOTE]
> Visual Studio 2019 pro Mac je [teď k dispozici](installation.md).

Visual Studio pro Mac je _integrované vývojové prostředí_ .NET na Macu, které se dá použít k úpravám, ladění a sestavování kódu a publikování aplikace. Kromě očekávaných funkcí, jako je standardní editor a ladicí program, Visual Studio pro Mac zahrnuje kompilátory, nástroje pro dokončování kódu, grafické návrháře a správu zdrojového kódu pro ESE do procesu vývoje softwaru.

Visual Studio pro Mac podporuje mnoho stejných typů souborů jako jejich protějšky v systému Windows, například `.csproj` soubory, nebo, a podporuje funkce, jako je například `.fsproj` `.sln` EditorConfig, což znamená, že můžete použít integrované vývojové prostředí (IDE), které pro vás vyhovuje nejlépe.
Vytvoření, otevření a vývoj aplikace bude známé prostředí pro kohokoli, kdo dřív používal aplikaci Visual Studio ve Windows. Navíc Visual Studio pro Mac využívá spoustu výkonných nástrojů, které jejich protějšky v systému Windows poskytují takové výkonné integrované vývojové prostředí (IDE). Platforma kompilátoru Roslyn se používá pro refaktoring a IntelliSense. Systém projektu a modul sestavení používají MSBuild a jeho Editor zdrojového kódu podporuje sady TextMate. Používá stejné moduly ladicího programu pro aplikace Xamarin a .NET Core a stejné návrháře pro Xamarin. iOS a Xamarin. Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Co můžu v Visual Studio pro Mac

Visual Studio pro Mac podporuje následující typy vývoje:

- ASP.NET Core webových aplikací pomocí jazyka C#, F # a podpory pro stránky Razor, JavaScript a TypeScript
- Konzolové aplikace .NET Core s C# nebo F #
- Hry a aplikace Unity pro různé platformy s využitím jazyka C #
- Aplikace pro Android, iOS, tvOS a watchOS v Xamarin pomocí C# nebo F # a XAML
- Desktopové aplikace pro kakao v C# nebo F #

V tomto článku se seznámíte s různými částmi Visual Studio pro Mac, kde se můžete podívat na některé funkce, díky kterým je vytváření těchto aplikací výkonným nástrojem.

## <a name="ide-tour"></a>Prohlídka integrovaného vývojového prostředí (IDE)

Visual Studio pro Mac je uspořádána do několika oddílů pro správu souborů a nastavení aplikace, vytváření kódu aplikace a ladění.

## <a name="welcome-screen"></a>Úvodní obrazovka

Po spuštění Visual Studio pro Mac zobrazí *úvodní obrazovku*:

![Úvodní obrazovka](media/ide-tour-image1.png)

Úvodní obrazovka obsahuje následující oddíly:

- **Panel nástrojů** – poskytuje rychlý přístup k panelu hledání. Při načtení řešení se panel nástrojů používá k nastavení konfigurací aplikace, ladění a k zobrazování chyb.
- **Začínáme** – poskytuje rychlý přístup k užitečným tématům pro vývojáře začínáme s Visual Studio pro Mac.
- **Poslední řešení** – poskytuje rychlý přístup k nedávno otevřeným řešením a pohodlným tlačítkům pro otevírání a vytváření projektů.
- **Novinky pro vývojáře** – informační kanál, který vám zajistí aktuální informace o nejnovějších informacích o vývojářích Microsoftu.

## <a name="solutions-and-projects"></a>Řešení a projekty

Následující obrázek ukazuje Visual Studio pro Mac s načtenou aplikací:

![Visual Studio pro Mac s načtenou aplikací](media/ide-tour-image17.png)

Následující části obsahují přehled hlavních oblastí v Visual Studio pro Mac.

## <a name="solution-pad"></a>Oblast řešení

Oblast řešení uspořádá projekt (y) v řešení:

![Projekty uspořádané v Oblast řešení](media/ide-tour-image18.png)

To je místo, kde jsou soubory zdrojového kódu, prostředků, uživatelského rozhraní a závislostí uspořádány do projektů specifických pro platformu.

Další informace o použití projektů a řešení v Visual Studio pro Mac naleznete v článku [projekty a řešení](./projects-and-solutions.md) .

## <a name="assembly-references"></a>Odkazy na sestavení

Odkazy na sestavení pro každý projekt jsou k dispozici ve složce odkazy:

![Odkazuje na složku na panelu řešení.](media/ide-tour-image19.png)

Další odkazy jsou přidány pomocí dialogového okna **Upravit odkazy** , které se zobrazí Poklikáním na složku odkazy, nebo výběrem možnosti **Upravit odkazy** v jeho kontextových nabídkách:

![Dialogové okno Upravit odkazy](media/ide-tour-image20.png)

Další informace o použití odkazů v Visual Studio pro Mac naleznete v článku [Správa odkazů v projektu](./managing-references-in-a-project.md) .

## <a name="dependencies--packages"></a>Závislosti/balíčky

Všechny externí závislosti použité ve vaší aplikaci se ukládají do složky závislosti nebo balíčky v závislosti na tom, jestli jste v projektu .Net Core nebo Xamarin. iOS/Xamarin. Android. Tyto jsou obvykle poskytovány ve formě NuGet.

NuGet je nejoblíbenější správce balíčků pro vývoj pro .NET. Díky podpoře NuGet v aplikaci Visual Studio můžete snadno vyhledat a přidat balíčky do projektu do aplikace.

Pokud chcete do aplikace přidat závislost, klikněte pravým tlačítkem na složku závislosti/balíčky a vyberte **Přidat balíčky**:

![Přidat balíček NuGet](media/ide-tour-image21.png)

Informace o použití balíčku NuGet v aplikaci najdete v článku [zahrnutí projektu NuGet v projektu](./nuget-walkthrough.md) .

## <a name="refactoring"></a>Refaktoring

Visual Studio pro Mac poskytuje dva užitečné způsoby refaktorování kódu: kontextové akce a zdrojová analýza. Další informace o těchto možnostech si můžete přečíst v článku [refaktoringu](./refactoring.md) .

## <a name="debugging"></a>Ladění

Visual Studio pro Mac má nativní ladicí program umožňující ladění pro aplikace Xamarin. iOS, Xamarin. Mac a Xamarin. Android. Visual Studio pro Mac používá měkký ladicí program mono, který je implementován do Mono runtime a umožňuje rozhraní IDE ladit spravovaný kód napříč všemi platformami. Další informace o ladění naleznete v článku [ladění](./debugging.md) .

Ladicí program obsahuje bohatých vizualizací pro speciální typy, jako jsou například řetězce, barvy, adresy URL a také velikosti, souřadnice a Bézierovy křivky.

Další informace o vizualizacích dat ladicího programu najdete v článku [vizualizace dat](./data-visualizations.md) .

## <a name="version-control"></a>Správa verzí

Visual Studio pro Mac se integruje se systémy správy zdrojového kódu Git a subverze. Projekty pod správou zdrojových kódů jsou označeny větví uvedenou vedle názvu řešení:

![Název větve, který označuje projekt pod správou zdrojových kódů](media/ide-tour-image22.png)

Soubory s nepotvrzenými změnami mají pro své ikony v podokně řešení poznámku, jak je znázorněno na následujícím obrázku:

![Nepotvrzené soubory na panelu řešení](media/ide-tour-image23.png)

Další informace o použití správy verzí v aplikaci Visual Studio naleznete v článku Správa [verzí](./version-control.md) .

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Viz také

- [Rozhraní IDE sady Visual Studio (ve Windows)](/visualstudio/ide/visual-studio-ide)