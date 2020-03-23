---
title: Příkazy
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac0284ce274791f21c9c0f85d265d92a7097cb09
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596369"
---
# <a name="visual-studio-commands"></a>Příkazy sady Visual Studio

Příkazy sady Visual Studio můžete zadat v okně **Příkaz,** **V okně Okamžité** nebo **Vpoli najít/příkaz.** V každém případě větší než`>`podepsat ( ) označuje, že příkaz, spíše než hledání nebo ladění operace, následuje.

Úplný seznam příkazů a jejich syntaxi najdete na stránce **Klávesnice** v prostředí **Tools** > **Options** > **Environment**.

V lokalizovaných verzích rozhraní IDE lze názvy příkazů zadat buď v rodném jazyce rozhraní IDE, nebo v angličtině. Můžete například zadat `File.NewFile` buď `Fichier.NouveauFichier` nebo ve francouzském ide spustit stejný příkaz.

Mnoho příkazů má aliasy. Seznam aliasů příkazů naleznete v tématu [Příkaz aliasy](../../ide/reference/visual-studio-command-aliases.md). Klávesové zkratky příkazů najdete [v tématu Výchozí klávesové zkratky v sadě Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md).

## <a name="escape-character"></a>Řídicí znak

Řídicí znak pro příkazy sady Visual Studio je stříška (^). Řídicí znak znamená, že znak bezprostředně za ním je interpretován doslovně, nikoli jako řídicí znak. To lze použít k vložení rovných uvozovek (), mezery, úvodní lomítka, stříšky nebo jiné literál znaky v parametru nebo přepínač hodnoty, s výjimkou názvů přepínačů. Například:

```
>Edit.Find ^^t /regex
```

Stříška funguje stejně bez ohledu na to, zda je uvnitř nebo vně uvozovek. Pokud je stříška posledním znakem na řádku, je ignorována.

## <a name="commands-with-arguments"></a>Příkazy s argumenty

Následující příkazy přebírají argumenty nebo přepínače:

| Název příkazu | Popis |
| - | - |
| [Přidat existující položku](../../ide/reference/add-existing-item-command.md) | Přidá existující soubor do aktuálního řešení a otevře jej. |
| [Přidat existující projekt](../../ide/reference/add-existing-project-command.md) | Přidá existující projekt do aktuálního řešení. |
| [Přidat novou položku](../../ide/reference/add-new-item-command.md) | Přidá novou položku řešení, například .htm, .css, .txt nebo frameset do aktuálního řešení a otevře ji. |
| [Alias](../../ide/reference/alias-command.md) | Vytvoří nový alias pro úplný příkaz, úplný příkaz a argumenty nebo dokonce jiný alias. |
| [Vyhodnotit prohlášení](../../ide/reference/evaluate-statement-command.md) | Vyhodnotí a zobrazí daný příkaz. |
| [Najít](../../ide/reference/find-command.md) | Prohledává soubory pomocí podmnožiny možností dostupných v ovládacím prvku **Najít a nahradit.** |
| [Najít v souborech](../../ide/reference/find-in-files-command.md) | Prohledává soubory pomocí podmnožiny možností dostupných v nabídce [Najít v souborech](../../ide/find-in-files.md). |
| [Přejít na](../../ide/reference/go-to-command.md) | Přesune kurzor na zadaný řádek. |
| [Zásobník volání seznamu](../../ide/reference/list-call-stack-command.md) | Zobrazí aktuální zásobník volání. |
| [Rozebrání seznamu](../../ide/reference/list-disassembly-command.md) | Zahájí proces ladění a umožňuje určit způsob zpracování chyb. |
| [Paměť seznamu](../../ide/reference/list-memory-command.md) | Zobrazí obsah zadaného rozsahu paměti. |
| [Seznam modulů](../../ide/reference/list-modules-command.md) | Zobrazí seznam modulů pro aktuální proces. |
| [Seznam žurnálů](../../ide/reference/list-registers-command.md) | Zobrazí seznam žurnálu. |
| [Zdroj seznamu](../../ide/reference/list-source-command.md) | Zobrazí zadané řádky zdrojového kódu. |
| [Seznam vláken](../../ide/reference/list-threads-command.md) | Zobrazí seznam vláken v aktuálním programu. |
| [Výstup okna příkazu protokolu](../../ide/reference/log-command-window-output-command.md) | Zkopíruje veškerý vstup a výstup z okna Příkaz do souboru. |
| [Nový soubor](../../ide/reference/new-file-command.md) | Vytvoří nový soubor a přidá jej do aktuálně vybraného projektu. |
| [Otevřít soubor](../../ide/reference/open-file-command.md) | Otevře existující soubor a umožní zadat editor. |
| [Otevřít projekt](../../ide/reference/open-project-command.md) | Otevře existující projekt a umožní přidat projekt do aktuálního řešení. |
| [Tisk](../../ide/reference/print-command.md) | Vyhodnotí výraz a zobrazí výsledky nebo zadaný text. |
| [Rychlé kukátko – příkaz](../../ide/reference/quick-watch-command.md) | Zobrazí vybraný nebo zadaný text v poli **Výraz** dialogového okna **Rychlé sledování.** |
| [Nahradit](../../ide/reference/replace-command.md) | Nahradí text v souborech pomocí podmnožiny voleb dostupných v ovládacím prvku **Najít a nahradit.** |
| [Nahradit v souborech](../../ide/reference/replace-in-files-command.md) | Nahradí text v souborech pomocí podmnožiny voleb dostupných v části [Nahradit v souborech](../../ide/replace-in-files.md). |
| [Nastavit aktuální snímek zásobníku](../../ide/reference/set-current-stack-frame-command.md) | Umožňuje zobrazit určitý rámec zásobníku. |
| [Nastavit aktuální vlákno](../../ide/reference/set-current-thread-command.md) | Umožňuje zobrazit určité vlákno. |
| [Nastavit Radix](../../ide/reference/set-radix-command.md) | Určuje počet bajtů, které chcete zobrazit. |
| [Prostředí](../../ide/reference/shell-command.md) | Spustí programy zevnitř, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jako by byl příkaz proveden z příkazového řádku. |
| [ShowWebBrowser – příkaz](../../ide/reference/showwebbrowser-command.md) | Zobrazí adresu URL zadanou v okně webového prohlížeče v integrovaném vývojovém prostředí (IDE) nebo externí prostředí IDE. |
| [Zahájení](../../ide/reference/start-command.md) | Zahájí proces ladění a umožňuje určit způsob zpracování chyb. |
| [Cesta](../../ide/reference/symbol-path-command.md) | Nastaví seznam adresářů pro ladicí program pro hledání symbolů. |
| [Přepnout zarážku](../../ide/reference/toggle-breakpoint-command.md) | Zapne nebo vypne zarážku v závislosti na aktuálním stavu v aktuálním umístění v souboru. |
| [Kukátko – příkaz](../../ide/reference/watch-command.md) | Vytvoří a otevře zadanou instanci okna **Kukátka.** |

## <a name="see-also"></a>Viz také

- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/Příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů Visual Studia](../../ide/reference/visual-studio-command-aliases.md)
