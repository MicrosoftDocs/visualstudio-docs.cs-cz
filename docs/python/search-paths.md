---
title: Jak se používají vyhledávací cesty Pythonu
description: Visual Studio poskytuje konkrétnější prostředky k určení cesty hledání pro prostředí a projekty, aby se zabránilo použití proměnných celého systému.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 37ce9d7b1853dfecc9e0ec33ca08c3c3fa0571e0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62428426"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Jak Visual Studio používá cesty hledání v Pythonu

Při typickém použití `PYTHONPATH` v Pythonu poskytuje proměnná prostředí (nebo `IRONPYTHONPATH`, atd.) výchozí cestu hledání pro soubory modulů. To znamená, že `from <name> import...` při `import <name>` použití příkazu nebo Python prohledá následující umístění, aby získal odpovídající název:

1. Vestavěné moduly Pythonu.
1. Složka obsahující kód Pythonu, který používáte.
1. "Cesta vyhledávání modulu", jak je definována příslušnou proměnnou prostředí. (Viz proměnné [Cesta hledání modulu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) a [prostředí](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) v základní dokumentaci pythonu.)

Visual Studio ignoruje proměnnou prostředí vyhledávací cesty, ale i v případě, že proměnná je nastavena pro celý systém. Ve skutečnosti je ignorována právě *proto,* že je nastavena pro celý systém, a proto vyvolává určité otázky, které nelze automaticky odpovědět: Jsou odkazované moduly určeny pro Python 2.7 nebo Python 3.6 +? Budou přepsat standardní moduly knihovny? Je vývojář vědom tohoto chování nebo je to pokus o zneužití škodlivého softwaru?

Visual Studio tedy poskytuje prostředky k určení cesty hledání přímo v prostředí i projekty. Kód, který spustíte nebo ladíte v sadě Visual `PYTHONPATH` Studio, obdrží vyhledávací cesty v hodnotě (a dalších ekvivalentních proměnných). Přidáním vyhledávacích cest Visual Studio zkontroluje knihovny v těchto umístěních a v případě potřeby pro ně vytvoří databáze IntelliSense (Visual Studio 2017 verze 15.5 a starší; sestavení databáze může nějakou dobu trvat v závislosti na počtu knihoven).

Chcete-li přidat cestu hledání, přejděte do **Průzkumníka řešení**, rozbalte uzel projektu, klikněte pravým tlačítkem myši na **Hledání cest**a vyberte Přidat složku do **cesty hledání**:

::: moniker range="vs-2017"
![Příkaz Přidat složku do cesty hledání v hledání cest v Průzkumníku řešení](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Příkaz Přidat složku do cesty hledání v hledání cest v Průzkumníku řešení](media/search-paths-command-2019.png)
::: moniker-end

Tento příkaz zobrazí prohlížeč, ve kterém pak vyberete složku, kterou chcete zahrnout.

Pokud `PYTHONPATH` proměnná prostředí již obsahuje požadované složky, použijte jako vhodný zástupce **použít funkci Přidat cestu pythonu do vyhledávacích cest.**

Jakmile jsou složky přidány do cesty hledání, Visual Studio používá tyto cesty pro všechny prostředí přidružené k projektu. (Chyby se mohou zobrazit, pokud je prostředí založeno na Pythonu 3 a pokusíte se přidat vyhledávací cestu do modulů Pythonu 2.7.)

Soubory s příponou *ZIP* nebo *.egg* lze také přidat jako vyhledávací cesty výběrem příkazu **Přidat zip archiv do příkazu Hledat cestu.** Stejně jako u složek, obsah těchto souborů jsou kontrolovány a k dispozici IntelliSense.

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu v sadě Visual Studio](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použití souboru requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Odkaz na okno prostředí Pythonu](python-environments-window-tab-reference.md)
