---
title: Visual Studio pro Mac pro uživatele Windows
description: Představení funkcí pro usnadnění přístupu v Visual Studio pro Mac a jak je možné je povolit.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/25/2019
ms.assetid: 61CB6883-08CE-470F-8599-6F7570DB756E
ms.openlocfilehash: b414026ba7297dd6c93fecdf56d9a9c58c99f294
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984268"
---
# <a name="visual-studio-for-mac-for-windows-users"></a>Visual Studio pro Mac pro uživatele Windows

Migrace z jednoho operačního systému na jiný může být těžké. V aplikacích pro různé platformy jsou často drobné rozdíly, od uživatelského rozhraní po kategorizaci položek nabídky. Uživatelé budou mít také výukovou křivku acclimatizing k novému uživatelskému rozhraní operačního systému. Tady se dozvíte o nejběžnějších rozdílech mezi Visual Studio pro Mac a Visual Studiem pro Windows. Naučíte se také několik různých konvencí mezi macOS a Windows.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Jako vývojáři, mnohé z vás budou zvyklí používat pro vaše úkoly a navigaci používání klávesnice. Některé klávesy na klávesnici jsou společné mezi počítači Mac a Windows. Mohli byste být forgiveni, že klávesové zkratky, jako je kopírování a vkládání, používají stejné kombinace kláves. Nejedná se vždy o případ. Naštěstí můžete změnit klíčové vazby v Visual Studio pro Mac tak, aby přesně odpovídaly možnostem sady Visual Studio ve Windows.

Při prvním spuštění Visual Studio pro Mac uvidíte okno pro výběr klávesových zkratek: ![ okno vazby klíčů](media/ide-tour-2019-keyboard-shortcut.png)

Pokud chcete změnit klíčové vazby později, můžete najít nastavení v části Předvolby: ![ klíčové vazby.](media/customizing-the-ide-image10a.png)

Je důležité si uvědomit, že macOS používá pro Windows různé systémové zástupce. Změna předvoleb klíčových vazeb vám umožní používat v Visual Studio pro Mac známé zástupce Windows. V jiných oblastech macOS ale budete muset být obeznámeni s macOS zástupci.

Modifikační klávesa příkazu macOS (⌘) může běžně nahradit řídicí klíč ve Windows. Tady jsou některé příklady a jiné běžně používané zkratky:

|Úkol                   |Zástupce Windows         |Zástupce macOS      |
|-----------------------|-------------------------|--------------------|
|Kopírovat                   |`Ctrl + C`               |`⌘ + C`             |
|Vložit                  |`Ctrl + V`               |`⌘ + V`             |
|Vyjmout                    |`Ctrl + X`               |`⌘ + X`             |
|Zpět                   |`Ctrl + Z`               |`⌘ + Z`             |
|Opakovat                   |`Ctrl + Shift + Z`       |`⌘ + Shift + Z`     |
|Odstranit napravo od kurzoru |`Delete`                 |`fn + Backspace`    |
|Odstranit slovo            |`Ctrl + Delete`          |`fn + ⌥ + Backspace`|

> [!TIP]
> Úplný seznam macOSch zástupců najdete na [webu podpory společnosti Apple](https://support.apple.com/en-us/HT201236).

## <a name="menus"></a>Nabídky

Nabídky v macOS jsou uspořádány jinak než nabídky ve Windows. Visual Studio pro Mac není žádná výjimka. Některé z nejběžnějších možností nabídky najdete tady:

|Úkol                   |Visual Studio (Windows)                                              |Visual Studio for Mac                |
|-----------------------|---------------------------------------------------------------------|-------------------------------------|
|Předvolby (možnosti)  |Možnosti > nástrojů...                                                   |Visual Studio – předvolby pro >...       |
|Rozšíření             |Rozšíření > Správa rozšíření                                       |Rozšíření Visual studia >...        |
|Rozložení                |Okno > použít rozložení okna > [vybrat rozložení]                       |Zobrazit > [vybrat rozložení]               |
|Aktualizace                |Help > vyhledat aktualizace                                             |Visual Studio > vyhledat aktualizace... |
|Správce balíčků NuGet  |Nástroje > správce balíčků NuGet > spravovat balíčky nebo řešení NuGet... |Projekt > spravovat balíčky NuGet...   |
|Panely nebo okna         |Zobrazení > [vybrat panel nebo okno]                                         |Zobrazení >ových >ů [vybrat plochu/okno]  |
|Nástroje pro hledání             |Upravit > najít a nahradit > [vybrat nástroj]                              |Search > [vybrat nástroj]               |
|O sadě Visual Studio    |Help > o Microsoft Visual Studio                                 |Visual Studio > o aplikaci Visual Studio  

> [!NOTE]
> Přehled nejběžnějších funkcí najdete v Visual Studio pro Mac v [prohlídce IDE](ide-tour.md) .