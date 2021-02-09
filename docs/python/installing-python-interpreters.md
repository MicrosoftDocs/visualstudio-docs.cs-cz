---
title: Výběr a instalace překladačů Pythonu
description: Úplný seznam překladačů Pythonu, které jsou podporovány v aplikaci Visual Studio, a stručný návod, kde najít instalační programy.
ms.date: 06/05/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e2c4cd4c110b55837009ea9d081a95180727d331
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916520"
---
# <a name="install-python-interpreters"></a>Instalace interpretů Pythonu

Ve výchozím nastavení nainstaluje úloha vývoje v Pythonu do sady Visual Studio 2017 a později také Python 3 (64-bit). Volitelně můžete zvolit instalaci 32 a 64 bitových verzí Pythonu 2 a Python 3, společně s Miniconda (Visual Studio 2019) nebo Anaconda 2/Anaconda 3 (Visual Studio 2017), jak je popsáno v tématu [instalace](installing-python-support-in-visual-studio.md).

::: moniker range=">=vs-2019"
Alternativně můžete v dialogovém okně **Přidat prostředí** nainstalovat standardní překladače Pythonu. V okně **prostředí Pythonu** nebo na panelu nástrojů Python vyberte příkaz **Přidat prostředí** , vyberte kartu **Instalace Pythonu** , určete, které překladače se mají nainstalovat a vyberte **nainstalovat**.
::: moniker-end

Můžete také ručně nainstalovat kterýkoli z překladačů uvedených v následující tabulce mimo instalační program sady Visual Studio. Pokud jste například nainstalovali Anaconda 3 před instalací sady Visual Studio, nemusíte ho instalovat znovu prostřednictvím instalačního programu sady Visual Studio. Překladač můžete také nainstalovat ručně, pokud například není k dispozici novější verze nástroje, která se ještě nezobrazuje v instalačním programu sady Visual Studio.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio podporuje Python verze 2,7 a také verze 3,5 a vyšší. I když je možné použít sadu Visual Studio k úpravám kódu napsaného v jiných verzích Pythonu, tyto verze se oficiálně nepodporují a funkce, jako je například IntelliSense a ladění, nemusí fungovat.
::: moniker-end

V případě sady **Visual Studio 2015 a starších** verzí je nutné ručně nainstalovat jeden z překladačů.

Visual Studio (všechny verze) automaticky detekuje všechny nainstalované interprety Pythonu a jeho prostředí kontrolou registru v závislosti na [PEP 514-registraci Pythonu v registru Windows](https://www.python.org/dev/peps/pep-0514/). Instalace Pythonu se obvykle nacházejí v části **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32 bitů) a **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64 bitů), a to v uzlech pro distribuci, jako je **PythonCore** (CPython) a **ContinuumAnalytics** (Anaconda).

Pokud Visual Studio nedetekuje nainstalované prostředí, přečtěte si téma [Ruční identifikace stávajícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio zobrazí všechna známá prostředí v okně [**prostředí Pythonu**](managing-python-environments-in-visual-studio.md#the-python-environments-window) a automaticky detekuje aktualizace stávajících překladačů.

| Interpret | Description |
| --- | --- |
| [CPython](https://www.python.org/) | "Nativní" a nejčastěji používaný překladač, k dispozici v 32 bitů a 64 verze (doporučeno 32). Zahrnuje nejnovější funkce jazyků, maximální kompatibilitu balíčků Pythonu, úplnou podporu ladění a spolupráci s [IPython](https://ipython.org/). Viz také: Mám [použít Python 2 nebo Python 3?](https://wiki.python.org/moin/Python2orPython3). Všimněte si, že Visual Studio 2015 a starší nepodporují Python 3.6 + a můžou poskytovat chyby, jako je **Nepodporovaná verze pythonu 3,6**. Místo toho použijte Python 3,5 nebo starší. |
| [Ironpythonu](https://github.com/IronLanguages/ironpython2) | Implementace jazyka Python v rozhraní .NET, která je k dispozici v 32 a 64 bitových verzí, poskytuje C#/F # webový Basic Interop, přístup k rozhraním API .NET, standardní ladění v Pythonu (ale ne ladění v kombinovaném režimu C++) a smíšené ladění Ironpythonu/C#. Ironpythonu ale nepodporuje virtuální prostředí. |
| [Anaconda](https://www.continuum.io) | Otevřená platforma pro datové vědy, která využívá Python, a zahrnuje nejnovější verzi CPython a většinu obtížně instalovaných balíčků. Doporučujeme, pokud se nemůžete rozhodnout jinak. |
| [PyPy](https://www.pypy.org/) | Vysoce výkonné trasování JIT implementace Pythonu, které je vhodné pro dlouhotrvající programy a situace, kde zjistíte problémy s výkonem, ale nemůžete najít další řešení. Funguje se sadou Visual Studio, ale s omezeným podporou pro pokročilé funkce ladění. |
| [Jython](https://www.jython.org/) | Implementace Pythonu na prostředí Java Virtual Machine (JVM). Podobně jako Ironpythonu, kód spuštěný v Jython může komunikovat s třídami a knihovnami jazyka Java, ale nemusí být schopný použít spoustu knihoven, které jsou určené pro CPython. Funguje se sadou Visual Studio, ale s omezeným podporou pro pokročilé funkce ladění. |

Vývojáři, kteří chtějí poskytnout nové formy detekce prostředí Pythonu, najdete v tématu [detekce prostředí PTVS](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (GitHub.com).

## <a name="move-an-interpreter"></a>Přesunutí překladače

Pokud přesunete existující Interpret na nové umístění pomocí systému souborů, aplikace Visual Studio tuto změnu automaticky nerozpozná.

- Pokud jste původně určili umístění překladače prostřednictvím okna **prostředí Pythonu** , upravte jeho prostředí pomocí karty **Konfigurovat** v tomto okně a Identifikujte nové umístění. Viz téma [Ruční identifikace stávajícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Pokud jste Interpret instalovali pomocí instalačního programu nástroje, použijte následující postup k přeinstalování překladače v novém umístění:

  1. Obnovte interpret Pythonu do jeho původního umístění.
  2. Odinstalujte překladač pomocí instalačního programu, který vymaže položky registru.
  3. Přeinstalujte překladač na požadované místo.
  4. Restartujte sadu Visual Studio, která by měla automaticky rozpoznat nové umístění místo starého umístění.

Následující postup zajistí, že položky registru, které identifikují umístění interpretu, které používá aplikace Visual Studio, jsou správně aktualizovány. Použití instalačního programu také zpracovává všechny další vedlejší účinky, které mohou existovat.

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použít requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
- [Referenční dokumentace okna prostředí Pythonu](python-environments-window-tab-reference.md)
