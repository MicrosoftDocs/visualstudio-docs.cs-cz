---
title: Jak se používají cesty pro vyhledávání v Pythonu
description: Visual Studio poskytuje konkrétnější prostředky pro určení cest hledání pro prostředí a projekty, aby nedocházelo k používání proměnných v rámci systému.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 10430c6eba57c97dd46a706d0ec2f532cd08d4f3
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801162"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Jak Visual Studio používá cesty hledání v Pythonu

Při typickém použití Pythonu `PYTHONPATH` poskytuje proměnná prostředí (nebo `IRONPYTHONPATH` atd.) výchozí cestu pro hledání souborů modulů. To znamená, že když použijete `from <name> import...` `import <name>` příkaz nebo, Python vyhledá odpovídající název v následujících umístěních:

1. Vestavěné moduly Pythonu.
1. Složka obsahující kód Pythonu, který používáte.
1. "Cesta hledání modulu" definovaná příslušnou proměnnou prostředí. (Podívejte [se na cestu hledání modulu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) a [proměnné prostředí](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) v základní dokumentaci k Pythonu.)

Sada Visual Studio ignoruje proměnnou prostředí vyhledávacích cest, ale i když je proměnná nastavena pro celý systém. Ve skutečnosti se ignoruje, *protože* je nastavený pro celý systém, a proto vyvolává určité otázky, na které se nedá automaticky odpovědět: jsou odkazované moduly určeny pro Python 2,7 nebo Python 3.6 +? Chystá se přepsat standardní moduly knihovny? Zná vývojář toto chování nebo se jedná o škodlivý pokus o zneužití?

Visual Studio proto poskytuje způsob, jak určit cesty hledání přímo v prostředích a projektech. Kód spouštěný nebo ladění v aplikaci Visual Studio přijímá cesty hledání v hodnotě `PYTHONPATH` (a dalších ekvivalentních proměnných). Když přidáte cesty pro hledání, Visual Studio v těchto umístěních zkontroluje knihovny a v případě potřeby vytvoří databáze IntelliSense (Visual Studio 2017 verze 15,5 a starší). vytváření databáze může v závislosti na počtu knihoven trvat delší dobu.

Chcete-li přidat cestu pro hledání, přejděte na **Průzkumník řešení**, rozbalte uzel projektu, klikněte pravým tlačítkem na **cesty pro hledání**a vyberte **Přidat složku do cesty pro hledání**:

::: moniker range="vs-2017"
![Přidat složku do cesty pro hledání na cestách pro hledání v Průzkumník řešení](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Přidat složku do cesty pro hledání na cestách pro hledání v Průzkumník řešení](media/search-paths-command-2019.png)
::: moniker-end

Tento příkaz zobrazí prohlížeč, ve kterém pak vyberete složku, která se má zahrnout.

Pokud vaše `PYTHONPATH` Proměnná prostředí již obsahuje složky, které chcete, použijte **k hledání cest** jako pohodlný zástupce PYTHONPATH přidat.

Po přidání složek do vyhledávacích cest aplikace Visual Studio použije tyto cesty pro jakékoli prostředí přidružené k projektu. (Chyby se můžou zobrazit, pokud je prostředí založené na Pythonu 3 a pokusíte se přidat cestu pro hledání k modulům Pythonu 2,7.)

Soubory s příponou *. zip* nebo *. vaječný* se dají přidat taky jako cesty pro hledání, a to tak, že vyberete **Přidat archiv zip do příkazu pro hledání cesty** . Stejně jako u složek se obsah těchto souborů kontroluje a zpřístupňuje IntelliSense.

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu v aplikaci Visual Studio](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použít requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Referenční dokumentace okna prostředí Pythonu](python-environments-window-tab-reference.md)
