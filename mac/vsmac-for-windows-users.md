---
title: Visual Studio pro Mac pro uživatele Windows
description: Uvedení funkcí usnadnění v Sadě Visual Studio pro Mac a jak je lze povolit.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984268"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio pro Mac pro uživatele Windows

Migrace z jednoho operačního systému do druhého může být skličující. Tam jsou často jemné rozdíly v aplikacích mezi platformami, od uživatelského rozhraní až po kategorizaci položek nabídky. Uživatelé budou mít také křivku učení aklimatizace na uživatelské rozhraní nového operačního systému. Zde se dozvíte nejčastější rozdíly mezi Visual Studio pro Mac a Visual Studio pro Windows. Dozvíte se také několik různých konvencí mezi macOS a Windows.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Jako vývojáři, mnozí z vás budou zvyklí používat klávesnici pro vaše úkoly a navigaci. Některé klávesy na klávesnici jsou běžné mezi Počítači Mac a Windows. Mohlo by vám být odpuštěno, že si myslíte, že akce klávesnice, jako je kopírování a vkládání, používají stejné kombinace kláves. Není tomu tak vždy. Naštěstí můžete změnit klíče vazby v Sadě Visual Studio pro Mac tak, aby úzce odpovídaly visual studio v systému Windows.

Při prvním spuštění Visual Studia for Mac se zobrazí okno ![pro výběr klávesových zkratek: Okno Vazby kláves](media/ide-tour-2019-keyboard-shortcut.png)

Pokud chcete později změnit vazby klíčů, najdete nastavení v ![předvolbách: Předvolby vazby kláves](media/customizing-the-ide-image10a.png)

Je důležité si uvědomit, že macOS používá různé zástupce systému windows. Změna předvoleb vazby kláves vám umožní používat známé zástupce Windows ve Visual Studiu for Mac. V jiných oblastech macOS však musíte být obeznámeni se zkratkami macOS.

Modifikátor příkazu macOS (啦) může běžně nahradit klíč Control v systému Windows. Zde je několik příkladů a další běžně používané zkratky:

|Úkol                   |Zástupce systému Windows         |Zástupce macOS      |
|-----------------------|-------------------------|--------------------|
|Kopírovat                   |`Ctrl + C`               |`⌘ + C`             |
|Vložit                  |`Ctrl + V`               |`⌘ + V`             |
|Vyjmout                    |`Ctrl + X`               |`⌘ + X`             |
|Zpět                   |`Ctrl + Z`               |`⌘ + Z`             |
|Opakovat                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Odstranit pravotočné místo kurzoru |`Delete`                 |`fn + Backspace`    |
|Odstranit slovo            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Úplný seznam zkratek pro macOS najdete na [webu podpory Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Nabídky

Nabídky v macOS jsou uspořádány jinak než nabídky v systému Windows. Visual Studio pro Mac není výjimkou. Některé z nejběžnějších možností nabídky naleznete zde:

|Úkol                   |Visual Studio (Windows)                                              |Visual Studio pro Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Předvolby (volby)  |Nástroje > možnosti...                                                   |Předvolby > sady Visual Studio...       |
|Rozšíření             |Rozšíření > Spravovat rozšíření                                       |Rozšíření > sady Visual Studio...        |
|Rozložení                |Okno > Použít rozložení okna > [Vybrat rozložení]                       |Zobrazit > [Vybrat rozložení]               |
|Aktualizace                |Nápověda > Vyhledat aktualizace                                             |Visual Studio > Vyhledat aktualizace... |
|Správce balíčků NuGet  |Nástroje > Správce balíčků NuGet > spravovat balíčky NuGet nebo řešení... |Projekt > spravovat balíčky NuGet...   |
|Podložky / Windows         |Zobrazit > [Vybrat panel / okno]                                         |Zobrazit > > podložky [Vybrat podložku / okno]  |
|Najít nástroje             |Upravit > najít a nahradit > [Nástroj pro výběr]                              |Hledání > [Nástroj pro výběr]               |
|O sadě Visual Studio    |Nápověda > Microsoft Visual Studio                                 |Visual Studio > o sadě Visual Studio  

> [!NOTE]
> Přehled nejběžnějších funkcí v Sadě Visual Studio for Mac najdete v [prohlídce IDE](ide-tour.md)