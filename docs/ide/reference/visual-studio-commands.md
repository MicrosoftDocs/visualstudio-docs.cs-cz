---
title: Příkazy
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3af3685288c00e27bb63cd45c682ab8b6354f4e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622101"
---
# <a name="visual-studio-commands"></a>příkazy sady Visual Studio

Příkazy sady Visual Studio můžete zadat v **příkazovém** okně, **příkazovém** okně, nebo v poli **Najít/příkaz** . V každém případě symbol větší než (`>`) značí, že příkaz místo operace hledání nebo ladění následuje.

Úplný seznam příkazů a jejich syntaxi najdete na stránce **klávesnice** v části **nástroje**  > **Možnosti**  > **prostředí**.

V lokalizovaných verzích rozhraní IDE lze názvy příkazů zadat v nativním jazyce integrovaného vývojového prostředí (IDE) nebo v angličtině. Můžete například zadat buď `File.NewFile` nebo `Fichier.NouveauFichier` ve francouzštině integrovaném vývojovém prostředí, aby se spustil stejný příkaz.

Mnoho příkazů má aliasy. Seznam aliasů příkazů najdete v tématu [Aliasy příkazů](../../ide/reference/visual-studio-command-aliases.md). Klávesové zkratky k příkazům naleznete [v tématu výchozí klávesové zkratky v aplikaci Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Řídicí znak

Řídicí znak pro příkazy sady Visual Studio je stříška (^). Řídicí znak znamená, že znak bezprostředně za ním následuje interpretovat doslova, nikoli jako řídicí znak. To lze použít k vložení přímých uvozovek ("), mezer, počátečních lomítek, znakových přepínačů nebo jiných literálových znaků v parametru nebo hodnotě přepínače s výjimkou názvů přepínačů. Příklad:

```
>Edit.Find ^^t /regex
```

Blikající kurzor funguje stejně, bez ohledu na to, zda se nachází uvnitř nebo vně uvozovek. Pokud je jako poslední znak na řádku stříška, je ignorována.

## <a name="commands-with-arguments"></a>Příkazy s argumenty

Následující příkazy přebírají argumenty nebo přepínače:

| Název příkazu | Popis |
| - | - |
| [Přidat existující položku](../../ide/reference/add-existing-item-command.md) | Přidá existující soubor do aktuálního řešení a otevře ho. |
| [Přidat existující projekt](../../ide/reference/add-existing-project-command.md) | Přidá existující projekt k aktuálnímu řešení. |
| [Přidat novou položku](../../ide/reference/add-new-item-command.md) | Přidá novou položku řešení, jako je například. htm,. CSS,. txt nebo FRAMESET, do aktuálního řešení a otevře se. |
| [Zástupný](../../ide/reference/alias-command.md) | Vytvoří nový alias pro úplný příkaz, úplný příkaz a argumenty, nebo dokonce i jiný alias. |
| [Evaluate – příkaz](../../ide/reference/evaluate-statement-command.md) | Vyhodnotí a zobrazí daný příkaz. |
| [Najít](../../ide/reference/find-command.md) | Vyhledá soubory pomocí podmnožiny možností dostupných v ovládacím prvku **Najít a nahradit** . |
| [Najít v souborech](../../ide/reference/find-in-files-command.md) | Vyhledá soubory pomocí podmnožiny možností, které jsou k dispozici v [souborech Find in](../../ide/find-in-files.md). |
| [Přejít na](../../ide/reference/go-to-command.md) | Přesune kurzor na zadaný řádek. |
| [Výpis zásobníku volání](../../ide/reference/list-call-stack-command.md) | Zobrazí aktuální zásobník volání. |
| [Výpis zpětného překladu](../../ide/reference/list-disassembly-command.md) | Zahájí proces ladění a umožňuje určit, jak se mají chyby zpracovávat. |
| [Vypsat paměť](../../ide/reference/list-memory-command.md) | Zobrazí obsah zadaného rozsahu paměti. |
| [Seznam modulů](../../ide/reference/list-modules-command.md) | Vypíše moduly pro aktuální proces. |
| [Výpis registrů](../../ide/reference/list-registers-command.md) | Zobrazí seznam registrů. |
| [Zdroj seznamu](../../ide/reference/list-source-command.md) | Zobrazí zadané řádky zdrojového kódu. |
| [Vypsat vlákna](../../ide/reference/list-threads-command.md) | Zobrazí seznam vláken v aktuálním programu. |
| [Zaznamenat výstup z příkazového okna](../../ide/reference/log-command-window-output-command.md) | Zkopíruje všechny vstupy a výstupy z okno Příkaz do souboru. |
| [Nový soubor](../../ide/reference/new-file-command.md) | Vytvoří nový soubor a přidá jej do aktuálně vybraného projektu. |
| [Otevřít soubor](../../ide/reference/open-file-command.md) | Otevře existující soubor a umožňuje určit editor. |
| [Otevřít projekt](../../ide/reference/open-project-command.md) | Otevře existující projekt a umožňuje přidat projekt do aktuálního řešení. |
| [Tisk](../../ide/reference/print-command.md) | Vyhodnotí výraz a zobrazí výsledky nebo zadaný text. |
| [Příkaz Rychlé kukátko](../../ide/reference/quick-watch-command.md) | Zobrazí vybraný nebo zadaný text v poli **výraz** dialogového okna **Rychlé kukátko** . |
| [Náhrady](../../ide/reference/replace-command.md) | Nahradí text v souborech pomocí podmnožiny možností dostupných v ovládacím prvku **Najít a nahradit** . |
| [Nahradit v souborech](../../ide/reference/replace-in-files-command.md) | Nahradí text v souborech pomocí podmnožiny možností, které jsou k dispozici v [souborech nahradit v](../../ide/replace-in-files.md). |
| [Nastavit aktuální rámec zásobníku](../../ide/reference/set-current-stack-frame-command.md) | Umožňuje zobrazit konkrétní rámec zásobníku. |
| [Nastavit aktuální vlákno](../../ide/reference/set-current-thread-command.md) | Umožňuje zobrazit konkrétní vlákno. |
| [Nastavit základ](../../ide/reference/set-radix-command.md) | Určuje počet bajtů, které se mají zobrazit. |
| [Prostředí](../../ide/reference/shell-command.md) | Spustí programy v rámci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], jako by byl příkaz proveden z příkazového řádku. |
| [Příkaz ShowWebBrowser (Zobrazit webový prohlížeč)](../../ide/reference/showwebbrowser-command.md) | Zobrazuje adresu URL, kterou zadáte v okně webového prohlížeče, a to buď v rámci integrovaného vývojového prostředí (IDE), nebo mimo rozhraní IDE. |
| [Start](../../ide/reference/start-command.md) | Zahájí proces ladění a umožňuje určit, jak se mají chyby zpracovávat. |
| [Dílčí](../../ide/reference/symbol-path-command.md) | Nastaví seznam adresářů ladicího programu pro hledání symbolů. |
| [Přepnout zarážku](../../ide/reference/toggle-breakpoint-command.md) | Zapne nebo vypne zarážku v závislosti na jejím aktuálním stavu, a to v aktuálním umístění v souboru. |
| [Příkaz Kukátko](../../ide/reference/watch-command.md) | Vytvoří a otevře zadanou instanci okna **kukátka** . |

## <a name="see-also"></a>Viz také:

- [okno Příkaz](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)