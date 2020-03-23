---
title: Odkaz na okno prostředí Pythonu
description: Podrobnosti o každé z karet, které se zobrazí v okně Prostředí Pythonu v sadě Visual Studio.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 578f73aabfb8b5a4c8336c8611f634b8947c8885
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302768"
---
# <a name="python-environments-window-tabs-reference"></a>Odkaz na karty oken prostředí Pythonu

Otevření okna **Prostředí Pythonu:**

- Vyberte příkaz **Zobrazit** > **další** > prostředí Windows**Pythonu.**
- Klepněte pravým tlačítkem myši na uzel **Prostředí Pythonu** pro projekt v **Průzkumníku řešení** a vyberte **zobrazit všechna prostředí Pythonu**.

Pokud rozbalíte okno **Prostředí Pythonu** dostatečně široké, tyto možnosti se zobrazí jako karty, které můžete najít vhodnější pro práci s. Pro přehlednost jsou karty v tomto článku zobrazeny v rozbaleném zobrazení.

::: moniker range="vs-2017"
![Rozšířené zobrazení okna Prostředí Pythonu](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozšířené zobrazení okna Prostředí Pythonu](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Karta Přehled

Poskytuje základní informace a příkazy pro životní prostředí:

::: moniker range="vs-2017"
![Karta Přehled prostředí Pythonu](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Přehled prostředí Pythonu](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Příkaz | Popis |
| --- | --- |
| **Nastavení tohoto prostředí jako výchozího pro nové projekty** | Nastaví aktivní prostředí, což může způsobit, že visual studio (2017 verze 15.5 a starší) se krátce stane nereagujícím při načítání databáze IntelliSense. Prostředí s mnoha balíčky může být non-reagovat na delší dobu. |
| **Navštivte webové stránky distributora** | Otevře prohlížeč na adresu URL poskytovanou distribucí Pythonu. Python 3.x, například, jde do python.org. |
| **Otevřít interaktivní okno** | Otevře [interaktivní okno (REPL)](python-interactive-repl-in-visual-studio.md) pro toto prostředí v sadě Visual Studio a použije všechny [spouštěcí skripty (viz níže).](#startup-scripts) |
| **Prozkoumejte interaktivní skripty** | Viz [spouštěcí skripty](#startup-scripts). |
| **Použití interaktivního režimu IPython** | Pokud je nastaveno, otevře **interaktivní** okno s IPython ve výchozím nastavení. To umožňuje vložkové obrázky, stejně `name?` jako rozšířené `!command` Syntaxe IPython, jako je zobrazení nápovědy a pro příkazy prostředí. Tato možnost se doporučuje při použití distribuce Anaconda, protože vyžaduje další balíčky. Další informace naleznete [v tématu Use IPython in the Interactive window](interactive-repl-ipython.md). |
| **Otevřít v PowerShellu** | Spustí překladač v příkazovém okně prostředí PowerShell. |
| (Odkazy na složky a program) | Poskytuje rychlý přístup k instalační složce prostředí, překladači *python.exe* a interpretu *pythonw.exe.* První se otevře v Průzkumníkovi Windows, poslední dva otevřou okno konzoly. |

### <a name="startup-scripts"></a>Spouštěcí skripty

Při používání interaktivních oken v každodenním pracovním postupu pravděpodobně vyvíjíte pomocné funkce, které používáte pravidelně. Můžete například vytvořit funkci, která otevře datový rámec v aplikaci Excel, a potom tento kód uložit jako spouštěcí skript, aby byl vždy k dispozici v **interaktivním** okně.

Spouštěcí skripty obsahují kód, který **interaktivní** okno načte a spustí automaticky, včetně importů, definice funkcí a doslova cokoli jiného. Tyto skripty jsou odkazovány dvěma způsoby:

1. Při instalaci prostředí visual studio vytvoří složku *Documents\Visual Studio \<verze\\\<>\Python Skripty prostředí>* kde &lt;verze&gt; je verze sady Visual &lt;&gt; Studio (například 2017 nebo 2019) a prostředí odpovídá názvu prostředí. Pomocí příkazu **Prozkoumat interaktivní skripty** můžete snadno přejít do složky specifické pro prostředí. Při spuštění **interaktivní** okno pro toto prostředí, načte a spustí bez ohledu *na .py* soubory jsou nalezeny zde v abecedním pořadí.

1. Ovládací prvek **Skripty** v kartě**Možnosti** >  **nástroje** > **Pythonu** > **Interaktivní systém Windows** (viz [Možnosti interaktivních oken)](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)je určen k určení další složky pro spouštěcí skripty, které jsou načteny a spuštěny ve všech prostředích. Tato funkce však v současné době nefunguje.

## <a name="configure-tab"></a>Karta Konfigurace

Pokud je k dispozici, karta **Konfigurovat** obsahuje podrobnosti, jak je popsáno v následující tabulce. Pokud tato karta není k dispozici, znamená to, že Visual Studio spravuje všechny podrobnosti automaticky.

::: moniker range="vs-2017"
![Karta Konfigurace prostředí Pythonu](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Konfigurace prostředí Pythonu](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Pole | Popis |
| --- | --- |
| **Popis** | Název, který má být v prostředí. |
| **Cesta předpony** | Umístění základní složky interpreta. Vyplněním této hodnoty a klepnutím na tlačítko **Automaticky rozpoznat**se aplikace Visual Studio pokusí vyplnit ostatní pole za vás. |
| **Cesta interpreta** | Cesta ke spustitelnému interpretu, obvykle cesta předpony následovaná **python.exe** |
| **Překladač s okny** | Cesta k spustitelnému souboru bez konzoly, často cesta předpony následovaná **pythonw.exe**. |
| **Cesta knihovny**<br/>(je-li k dispozici) | Určuje kořen standardní knihovny, ale tato hodnota může být ignorována, pokud visual studio je schopen požadovat přesnější cestu od interpretu. |
| **Jazyková verze** | Vybráno z rozevírací nabídky. |
| **Architektura** | Normálně rozpoznáno a vyplněno automaticky, jinak určuje **32bitový** nebo **64bitový**. |
| **Proměnná prostředí cesty** | Proměnná prostředí, která interpret používá k hledání vyhledávacích cest. Visual Studio změní hodnotu proměnné při spuštění Pythonu tak, aby obsahovala cesty hledání projektu. Obvykle tato vlastnost by měla být nastavena na **PYTHONPATH**, ale někteří interpreti použít jinou hodnotu. |

## <a name="packages-tab"></a>Karta Balíčky

*Také označené "pip" v dřívějších verzích.*

Spravuje balíčky nainstalované v prostředí pomocí pip **(balíčky (Karta Balíčky (PyPI)** nebo conda **(balíčky (Conda)** karta, pro prostředí conda ve Visual Studiu 2017 verze 15.7 a novější). Na této kartě můžete také vyhledávat a instalovat nové balíčky, včetně jejich závislostí.

Balíčky, které jsou již nainstalovány, se zobrazí s ovládacími prvky pro aktualizaci (šipka nahoru) a odinstalace (X v kruhu) balíček:

![Karta Balíčky prostředí Pythonu](media/environments/environments-pip-tab-controls.png)

Zadáním vyhledávacího dotazu se vyfiltruje seznam nainstalovaných balíčků a balíčků, které lze nainstalovat z pypi.

::: moniker range="vs-2017"
![Karta Balíčky prostředí Pythonu s hledáním na "num"](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Balíčky prostředí Pythonu s hledáním na "num"](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Jak můžete vidět na obrázku výše, výsledky hledání ukazují řadu balíčků, které odpovídají hledaný termín; první položka v seznamu je však příkaz ke spuštění **pip instalační \<název>** přímo. Pokud jste na kartě **Balíčky (Conda),** místo toho se zobrazí **název instalace \<conda>**:

::: moniker range="vs-2017"
![Karta Conda packages zobrazující příkaz conda install](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Conda packages zobrazující příkaz conda install](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

V obou případech můžete přizpůsobit instalaci přidáním argumentů do vyhledávacího pole za název balíčku. Když zahrnete argumenty, ve výsledcích hledání se zobrazí **instalace pipu** nebo **instalace conda** následovaná obsahem vyhledávacího pole:

::: moniker range="vs-2017"
![Použití argumentů na příkazech instalace pip a conda](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Použití argumentů na příkazech instalace pip a conda](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Instalace balíčku vytvoří podsložky ve složce *Lib* prostředí v systému souborů. Pokud máte například v *c:\Python36*nainstalovaný Python 3.6 , balíčky jsou nainstalovány v *c:\Python36\Lib*; Pokud máte v *c:\Program Files\Anaconda3* nainstalovaný Anaconda3, pak jsou balíčky nainstalovány v *c:\Program Files\Anaconda3\Lib*. Pro prostředí conda jsou balíčky nainstalovány ve složce tohoto prostředí.

### <a name="grant-administrator-privileges-for-package-install"></a>Udělit oprávnění správce pro instalaci balíčku

Při instalaci balíčků do prostředí, které je umístěno v chráněné oblasti systému souborů, například *c:\Program Files\Anaconda3\Lib*, musí být visual studio spuštěno `pip install` se zvýšenými oprávněními, aby mohlo vytvářet podsložky balíčků. Pokud je požadováno zvýšení oprávnění, visual studio zobrazí výzvu, **oprávnění správce může být vyžadováno k instalaci, aktualizaci nebo odebrání balíčků pro toto prostředí**:

![Výzva ke zvýšení úrovně pro instalaci balíčku](media/environments/environments-pip-elevate.png)

**Elevate nyní** uděluje oprávnění správce pip pro jednu operaci, s výhradou také všechny výzvy operačního systému pro oprávnění. Výběr **pokračovat bez oprávnění správce** se pokusí nainstalovat balíček, ale pip selže při pokusu o vytvoření složek s výstupem, jako je **chyba: nelze vytvořit 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': Oprávnění odepřeno.**

Výběr vždy **zvýšit při instalaci nebo odebrání balíčků** zabrání dialogové okno z objevit pro dané prostředí. Chcete-li, aby se dialogové okno**Python** > znovu zobrazilo, přejděte na**obecné** >  **nastavení nástrojů** > **pythonu** a vyberte tlačítko Obnovit všechna **trvale skrytá dialogová okna**.

Na stejné kartě **Možnosti** můžete také vybrat **možnost Vždy spustit pip jako správce,** abyste potlačili dialog pro všechna prostředí. Viz [Možnosti – karta Obecné](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Bezpečnostní omezení se staršími verzemi Pythonu

Při použití Pythonu 2.6, 3.1 a 3.2 visual studio zobrazuje varování, **Vzhledem k novým bezpečnostním omezením nemusí instalace z internetu fungovat v této verzi Pythonu**:

![Zpráva o omezeních instalace pipu se starší verzí Pythonu](media/environments/environments-old-version-restriction.png)

Důvodem upozornění je, že s těmito `pip install` staršíverze Pythonu neobsahuje podporu pro transportní vrstvy zabezpečení (TLS) 1.2, který je vyžadován pro stahování balíčků ze zdroje balíčku, pypi.org. Vlastní sestavení Pythonu mohou podporovat TLS `pip install` 1.2, v takovém případě může fungovat.

Je možné stáhnout příslušný *get-pip.py* pro balíček z [bootstrap.pypa.io](https://bootstrap.pypa.io/), ručně stáhnout balíček z [pypi.org](https://pypi.org/)a potom nainstalovat balíček z této místní kopie.

Doporučujese však jednoduše upgradovat na Python 2.7 nebo 3.3+, v takovém případě se upozornění nezobrazí.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Karta IntelliSense

Zobrazuje aktuální stav databáze dokončení technologie IntelliSense:

![Karta IntelliSense prostředí Pythonu](media/environments/environments-intellisense-tab.png)

- Ve Visual Studiu 2017 verze 15.5 a starší, IntelliSense dokončení závisí na databázi, která byla zkompilována pro tuto knihovnu. Vytváření databáze se provádí na pozadí při instalaci knihovny, ale může trvat nějakou dobu a nemusí být dokončena při zahájení psaní kódu.
- Visual Studio 2017 verze 15.6 a novější používá rychlejší metodu k zajištění dokončení, které nejsou závislé na databázi ve výchozím nastavení. Z tohoto důvodu je karta označena **jako IntelliSense [databáze zakázána]**. Databázi můžete povolit vymazáním**možnosti Možnosti** >  **nástrojů** > **Pythonu** > **Experimental** > **Použijte nový styl IntelliSense pro prostředí**.

Když Visual Studio zjistí nové prostředí (nebo jej přidáte), automaticky začne kompilovat databázi analýzou zdrojových souborů knihovny. Tento proces může trvat minutu až hodinu nebo více v závislosti na tom, co je nainstalováno. (Anaconda, například, je dodáván s mnoha knihovnami a trvá nějakou dobu sestavit databázi.) Po dokončení získáte podrobné technologie IntelliSense a nemusíte databázi znovu aktualizovat (pomocí tlačítka **Aktualizovat DB),** dokud nenainstalujete další knihovny.

Knihovny, pro které nebyla data zkompilována, jsou označeny **!**; Pokud databáze prostředí není kompletní, a **!** vedle něj se zobrazí také v hlavním seznamu prostředí.

::: moniker-end

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu v sadě Visual Studio](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použití souboru requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
