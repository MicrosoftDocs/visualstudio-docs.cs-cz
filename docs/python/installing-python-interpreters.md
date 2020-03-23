---
title: Výběr a instalace interpretů Pythonu
description: Úplný seznam interpretů Pythonu, které jsou podporovány v sadě Visual Studio se stručným návodem, kde najít své instalační programy.
ms.date: 06/05/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 13290aef7acfe599c7693af4be771c625e713596
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75735815"
---
# <a name="install-python-interpreters"></a>Instalace interpretů Pythonu

Ve výchozím nastavení instalace úlohy vývoje Pythonu ve Visual Studiu 2017 a novější také nainstaluje Python 3 (64bitový). Volitelně můžete nainstalovat 32bitové a 64bitové verze Pythonu 2 a Pythonu 3 spolu s Minicondou (Visual Studio 2019) nebo Anacondou 2/Anaconda 3 (Visual Studio 2017), jak je popsáno v [aplikaci Installation](installing-python-support-in-visual-studio.md).

::: moniker range=">=vs-2019"
Alternativně můžete nainstalovat standardní interprety pythonu z dialogového okna **Přidat prostředí.** Vyberte příkaz **Přidat prostředí** v okně **Prostředí Pythonu** nebo na panelu nástrojů Pythonu, vyberte kartu **Instalace pythonu,** označte, které interprety chcete nainstalovat, a vyberte **Instalovat**.
::: moniker-end

Můžete také ručně nainstalovat některý z tlumočníků uvedených v tabulce níže mimo instalační program sady Visual Studio. Pokud jste například před instalací sady Visual Studio nainstalovali Anaconda 3, není nutné ji znovu instalovat prostřednictvím instalačního programu sady Visual Studio. Interpreta můžete nainstalovat také ručně, pokud například novější verze dostupné, která se ještě nezobrazuje v instalačním programu sady Visual Studio.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio podporuje Python verze 2.7, stejně jako verze 3.5 a vyšší. I když je možné použít Visual Studio k úpravám kódu napsaného v jiných verzích Pythonu, tyto verze nejsou oficiálně podporovány a funkce, jako je IntelliSense a ladění nemusí fungovat.
::: moniker-end

Pro **Visual Studio 2015 a starší**, je nutné ručně nainstalovat jeden z tlumočníků.

Visual Studio (všechny verze) automaticky detekuje každý nainstalovaný překladač Pythonu a jeho prostředí kontrolou registru podle [PEP 514 - Python registrace v registru Windows](https://www.python.org/dev/peps/pep-0514/). Instalace pythonu se obvykle nacházejí pod **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-bit) a **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-bit), pak v uzlech pro distribuci, jako je **PythonCore** (CPython) a **ContinuumAnalytics** (Anaconda).

Pokud Visual Studio nerozpozná nainstalované prostředí, [přečtěte si informace o ruční identifikaci existujícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio zobrazuje všechna známá prostředí v okně [**Prostředí Pythonu**](managing-python-environments-in-visual-studio.md#the-python-environments-window) a automaticky detekuje aktualizace stávajících interpretů.

| Tlumočník | Popis |
| --- | --- |
| [CPython](https://www.python.org/) | "Nativní" a nejčastěji používaný interpret, který je k dispozici v 32bitových a 64bitových verzích (doporučeno 32bitový). Obsahuje nejnovější funkce jazyka, maximální kompatibilitu balíčků Pythonu, plnou podporu ladění a interop s [IPython](https://ipython.org/). Viz také: [Mám použít Python 2 nebo Python 3?](https://wiki.python.org/moin/Python2orPython3). Všimněte si, že Visual Studio 2015 a starší nepodporují Python 3.6+ a může dát chyby jako **nepodporované python verze 3.6**. Místo toho použijte Python 3.5 nebo starší. |
| [Ironpython](https://github.com/IronLanguages/ironpython2) | Implementace Pythonu .NET, dostupná v 32bitových a 64bitových verzích, poskytující interop jazyka C#/F#/Visual Basic, přístup k rozhraní MAÚ API .NET, standardní ladění Pythonu (ale ne ladění v kombinovaném režimu Jazyka C++) a kombinované ladění IronPython/C#. IronPython však nepodporuje virtuální prostředí. |
| [Anaconda](https://www.continuum.io) | Platforma pro vědu o otevřených datech poháněná Pythonem a obsahuje nejnovější verzi CPython a většinu obtížně instalovatelné balíčky. Doporučujeme, pokud se nemůžete rozhodnout jinak. |
| [PyPy](https://www.pypy.org/) | Vysoce výkonná trasování jit implementace Pythonu, která je vhodná pro dlouhotrvající programy a situace, kdy identifikujete problémy s výkonem, ale nemůžete najít jiná řešení. Pracuje s Visual Studio, ale s omezenou podporou pro pokročilé funkce ladění. |
| [Jython](https://www.jython.org/) | Implementace Pythonu na Java Virtual Machine (JVM). Podobně jako IronPython, kód spuštěný v Jython můžete komunikovat s Java třídy a knihovny, ale nemusí být schopen používat mnoho knihoven určených pro CPython. Pracuje s Visual Studio, ale s omezenou podporou pro pokročilé funkce ladění. |

Vývojáři, kteří chtějí poskytovat nové formy detekce pro prostředí Pythonu, viz [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## <a name="move-an-interpreter"></a>Přesunutí tlumočníka

Pokud přesunete existující interpreta do nového umístění pomocí systému souborů, Visual Studio automaticky nerozpozná změnu.

- Pokud jste původně zadali umístění interpreta prostřednictvím okna **Prostředí Pythonu,** upravte jeho prostředí pomocí karty **Konfigurovat** v tomto okně k identifikaci nového umístění. Viz [Ruční identifikace existujícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Pokud jste interpreta nainstalovali pomocí instalačního programu, přeinstalujte jej v novém umístění pomocí následujících kroků:

  1. Obnovte překladač Pythonu do původního umístění.
  2. Odinstalujte interpreta pomocí instalačního programu, který vymaže položky registru.
  3. Přeinstalujte interpreta v požadovaném umístění.
  4. Restartujte visual studio, které by mělo automaticky rozpoznat nové umístění místo starého umístění.

Po tomto procesu zajišťuje, že položky registru, které identifikují umístění tlumočníka, který používá Visual Studio, jsou řádně aktualizovány. Použití instalačního programu také zpracovává všechny další vedlejší účinky, které mohou existovat.

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použití souboru requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
- [Odkaz na okno prostředí Pythonu](python-environments-window-tab-reference.md)
