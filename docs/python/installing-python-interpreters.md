---
title: Vyberte a instalace interpretů Pythonu
description: Úplný seznam interpretů Pythonu, které jsou podporovány v sadě Visual Studio s stručné pokyny, ve kterém můžete najít jejich instalační programy.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: de7bd0dcbdd36b9d30ea252a70a380b190adcce2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063558"
---
# <a name="install-python-interpreters"></a>Instalace interpretů Pythonu

Ve výchozím nastavení při instalaci úlohy vývoj pro Python v sadě Visual Studio 2017 také nainstaluje Python 3 (64 bitů). Volitelně můžete nainstalovat 32bitové a 64bitové verze Python 2, Python 3, Anaconda 2 a 3 programu Anaconda, jak je popsáno v [instalace](installing-python-support-in-visual-studio.md).

Můžete nainstalovat také ručně žádné interprety uvedené v následující tabulce mimo instalačního programu sady Visual Studio. Například pokud jste nainstalovali Anaconda 3 před instalací sady Visual Studio, není nutné znovu nainstalovat pomocí instalačního programu sady Visual Studio. Můžete také nainstalovat interpretu ručně pokud, třeba novější verzi k dispozici, který ještě se nezobrazí v instalačním programu sady Visual Studio.

Pro **sady Visual Studio 2015 a starší**, musíte ručně nainstalovat jeden interprety.

Visual Studio (všechny verze) automaticky rozpozná každý nainstalovaný interpret Pythonu a její prostředí tak, že zkontrolujete registru podle [období 514 - Python registraci v registru Windows](https://www.python.org/dev/peps/pep-0514/). Instalace Pythonu se většinou nacházejí ve skupinovém rámečku **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32 bitů) a **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-bit), pak v rámci uzly, aby se distribuce, jako **PythonCore** (CPython) a **ContinuumAnalytics** (Anaconda).

Pokud aplikace Visual Studio nerozpozná nainstalované prostředí, přečtěte si téma [ručně identifikovat existující prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Sada Visual Studio zobrazí všechny známé prostředí v [ **prostředí Pythonu** ](managing-python-environments-in-visual-studio.md#the-python-environments-window) okna a automaticky zjišťuje aktualizace existující interpretů.

| Interpret | Popis |
| --- | --- |
| [CPython](https://www.python.org/) | "Nativní" a nejčastěji používaná interpret, dostupné v 32bitové a 64bitové verze (32bitová verze doporučeno). Zahrnuje nejnovější funkce jazyků, maximální kompatibility balíček Pythonu, plná podpora ladění a zprostředkovatele komunikace s [IPython](https://ipython.org/). Viz také: [použít Python 2 nebo Python 3?](https://wiki,python.org/moin/Python2orPython3). Mějte na paměti, že Visual Studio 2015 a starší nepodporují Python 3.6 + a může dojít k chybám jako **nepodporované python verze 3.6**. Použití Pythonu 3.5 nebo starší místo. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Implementace .NET jazyka Python, dostupné v 32bitové a 64bitové verze poskytuje C#/F#/zprostředkovatele komunikace s objekty jazyka Visual Basic, přístup k rozhraní API pro .NET, standardní ladění Pythonu (ale není C++ ladění v kombinovaném režimu) a smíšené IronPython /C# ladění. IronPython, ale nepodporuje virtuální prostředí. |
| [Anaconda](https://www.continuum.io) | Platforma pro otevřete datovou vědu službu Python a obsahuje nejnovější verzi CPython a většina obtížné instalační balíčky. Doporučujeme, abyste ho rozhodnete nemůže jinak. |
| [PyPy](https://www.pypy.org/) | Vysoce výkonné trasování JIT, provádění Python, který je vhodný pro dlouho běžící programy a situacích, kde identifikujete výkonu problémy, ale nemůžu najít další řešení. Funguje s Visual Studio, ale s omezenou podporu pro pokročilé funkce ladění. |
| [Jython](http://www.jython.org/) | Implementace jazyka Python na virtuální počítač Java (JVM). Podobný Ironpythonu, kód spuštěný v Jython může komunikovat s třídami jazyka Java a knihoven, ale nemusí být možné používat mnoho knihoven určené pro CPython. Funguje s Visual Studio, ale s omezenou podporu pro pokročilé funkce ladění. |

Vývojáři, kteří chtěli poskytnout nové formy zjišťování pro prostředí Pythonu najdete v článku [PTVS prostředí detekce](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (webu github.com).

## <a name="move-an-interpreter"></a>Přesunout interpretu

Pokud přesouváte existující překladač do nového umístění pomocí systému souborů, Visual Studio nerozpozná automaticky změny.

- Pokud jste původně zadali umístění překladač prostřednictvím **prostředí Pythonu** okna, upravte svoje prostředí pomocí **konfigurovat** karty v tomto okně identifikovat nové umístění. Zobrazit [ručně identifikovat existující prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Pokud jste nainstalovali překladač pomocí instalačního programu, použijte následující kroky k přeinstalování interpret v novém umístění:

  1. Interpret Pythonu obnovte do původního umístění.
  2. Odinstalujte překladač pomocí jeho instalační program, který vymaže položky registru.
  3. Znovu nainstalujte překladač do požadovaného umístění.
  4. Restartujte sadu Visual Studio, který by měl automaticky rozpoznat nové umístění, namísto původní umístění.

Následující tento proces zajistí, že jsou správně aktualizovat položky registru, které identifikují na překladač umístění, které používá sada Visual Studio. Pomocí instalačního programu také zpracovává všechny vedlejší účinky, které mohou existovat.

## <a name="see-also"></a>Viz také:

- [Správa prostředí Pythonu](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Používání souboru requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
- [Odkaz na okno prostředí Pythonu](python-environments-window-tab-reference.md)
