---
title: Odkaz na okno prostředí Pythonu
description: Informace o jednotlivých karet, které se zobrazí v okně prostředí Pythonu v sadě Visual Studio.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409923"
---
# <a name="python-environments-window-tabs-reference"></a>Odkaz na kartách okno prostředí Pythonu

Otevření okna **prostředí Pythonu** :

- Vyberte příkaz **zobrazit** > **jiných prostředí Windows** > **Pythonu** .
- Klikněte pravým tlačítkem myši na uzel **prostředí Pythonu** pro projekt v **Průzkumník řešení** a vyberte **Zobrazit všechna prostředí Pythonu**.

Pokud rozbalíte okno **prostředí Pythonu** dostatečně v širším rozsahu, tyto možnosti se zobrazí jako karty, které vám mohou být užitečné při práci s nástrojem. Pro přehlednost karty v tomto článku jsou uvedeny v rozbalené zobrazení.

::: moniker range="vs-2017"
![Okno prostředí Pythonu rozšířené zobrazení](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno prostředí Pythonu rozšířené zobrazení](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Karta Přehled

Poskytuje základní informace a příkazy pro prostředí:

::: moniker range="vs-2017"
![Karta Přehled prostředí Pythonu](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Přehled prostředí Pythonu](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Příkaz | Popis |
| --- | --- |
| **Nastavit toto prostředí jako výchozí pro nové projekty** | Nastaví na aktivní prostředí, což může způsobit, že Visual Studio (2017 verze 15.5 a starší) stručně přestane reagovat při načítání databáze IntelliSense. Prostředí s mnoha balíčky je možné jako nereagující po delší dobu. |
| **Navštívit web distributora** | Otevře prohlížeč na adresu URL poskytované distribuci jazyka Python. Python 3.x, například přejde na python.org. |
| **Otevřít interaktivní okno** | Otevře [interaktivní okno (REPL)](python-interactive-repl-in-visual-studio.md) pro toto prostředí v sadě Visual Studio, přičemž použije všechny [spouštěcí skripty (viz níže)](#startup-scripts). |
| **Prozkoumat interaktivní skripty** | Viz [skripty při spuštění](#startup-scripts). |
| **Použít interaktivní režim IPython** | Při nastavení otevře **interaktivní** okno s IPython ve výchozím nastavení. Tím se umožní vložená zobrazení a také Rozšířená syntaxe IPython, jako je například `name?` pro zobrazení nápovědu a `!command` příkazů prostředí. Tato možnost se doporučuje při použití Anaconda distribuce, protože vyžaduje dodatečné balíčky. Další informace najdete v tématu [použití IPython v interaktivním okně](interactive-repl-ipython.md). |
| **Otevřít v PowerShellu** | Spuštění interpretu v příkazovém okně prostředí PowerShell. |
| (Složka a program odkazů) | Poskytněte rychlý přístup k instalační složce prostředí, Překladači *Python. exe* a interpretu *pythonw. exe* . První zobrazí v Průzkumníku Windows, druhé dvě otevřete okno konzoly. |

### <a name="startup-scripts"></a>Spouštěcí skripty

V pracovním postupu vaší každý den používáte interaktivních oken, pravděpodobně vývoj pomocných funkcí, které používáte pravidelně. Můžete například vytvořit funkci, která otevře datový rámec v aplikaci Excel, a pak tento kód Uložit jako spouštěcí skript, aby byl vždy k dispozici v **interaktivním** okně.

Spouštěcí skripty obsahují kód, který **interaktivní** okno načte a spustí automaticky, včetně importů, definic funkcí a doslova cokoli jiného. Tyto skripty jsou odkazovány dvěma způsoby:

1. Když nainstalujete prostředí, Visual Studio vytvoří složku *Documents\Visual Studio \<verze > \Python skripty\\\<prostředí >* kde &lt;verze&gt; je verze sady Visual Studio (například 2017 nebo 2019) a &lt;prostředí&gt; odpovídá názvu prostředí. Můžete snadno přejít do složky specifické pro konkrétní prostředí pomocí příkazu **prozkoumat interaktivní skripty** . Když spustíte **interaktivní** okno pro toto prostředí, načte a spustí jakékoli soubory *. py* v abecedním pořadí.

1. Ovládací prvek **skripty** v **nástrojích** > **Možnosti** > kartě **Python** > **Interactive Windows** (viz [Možnosti interaktivních možností Windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) určuje další složku pro spouštěcí skripty, které se načtou a spouštějí ve všech prostředích. Tato funkce se však nefunguje v současné době.

## <a name="configure-tab"></a>Karta Konfigurace

Pokud je k dispozici, karta **Konfigurovat** obsahuje podrobnosti, jak je popsáno v následující tabulce. Pokud tato karta není k dispozici, znamená to, že Visual Studio automaticky spravuje všechny podrobnosti.

::: moniker range="vs-2017"
![Karta Konfigurace prostředí Pythonu](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta Konfigurace prostředí Pythonu](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Pole | Popis |
| --- | --- |
| **Popis** | Název prostředí. |
| **Cesta k předponě** | Umístění složky základní překladač. Když vyplníte tuto hodnotu a kliknete na **Automatické rozpoznávání**, Visual Studio se pokusí vyplnit ostatní pole za vás. |
| **Cesta k interpretu** | Cesta ke spustitelnému souboru interpreta, obvykle cesta k předponě následovaná **Python. exe** |
| **Interpret v okně** | Cesta ke spustitelnému souboru mimo konzolu, často i cestu předpony následovanou **pythonw. exe**. |
| **Cesta ke knihovně**<br/>(Pokud je k dispozici) | Určuje kořenový standardní knihovnu, ale tato hodnota může ignorovat, pokud je schopen žádat přesnější cestu interpretu sady Visual Studio. |
| **Verze jazyka** | Vybrat z rozevírací nabídky. |
| **Architektura** | Obvykle se detekuje a vyplní automaticky, jinak určuje **32** bitů nebo **64**. |
| **Proměnná prostředí PATH** | Proměnná prostředí, která překladač používá k vyhledání cesty pro hledání. Visual Studio se změní hodnota proměnné při spuštění Pythonu tak, aby obsahoval cesty pro hledání v projektu. Obvykle by tato vlastnost měla být nastavená na **PYTHONPATH**, ale některé překladače používají jinou hodnotu. |

## <a name="packages-tab"></a>Karta balíčky

*Také označený jako PIP v dřívějších verzích.*

Spravuje balíčky nainstalované v prostředí pomocí PIP (karta **balíčky (PyPi)** ) nebo conda (karta **balíčky (conda)** pro prostředí conda ve Visual Studiu 2017 verze 15,7 a novější). Na této kartě můžete také vyhledat a nainstalovat nové balíčky, včetně jejich závislostí.

Balíčky, které jsou už nainstalované, se zobrazí s ovládacími prvky pro aktualizaci (šipka nahoru) a odinstalujte (X v kruhu), balíček:

![Karta balíčky prostředí Pythonu](media/environments/environments-pip-tab-controls.png)

Zadání vyhledávacích filtrů termín seznam nainstalovaných balíčků, jakož i balíčky, které je možné nainstalovat z PyPI.

::: moniker range="vs-2017"
![Karta balíčky prostředí Pythonu pomocí služby search na "počet"](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta balíčky prostředí Pythonu pomocí služby search na "počet"](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Jak vidíte na obrázku výše, výsledky hledání zobrazují počet balíčků, které odpovídají hledanému termínu; první položka v seznamu je však příkaz pro spuštění **\<ového > názvu příkazu PIP** přímo. Pokud se nacházíte na kartě **balíčky (conda)** , zobrazí se místo toho **instalace Conda \<název >** :

::: moniker range="vs-2017"
![Příkaz instalovat kartu balíčků Conda ukazující conda](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Příkaz instalovat kartu balíčků Conda ukazující conda](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

V obou případech můžete přizpůsobit instalaci tak, že přidáte argumenty za názvem balíčku do vyhledávacího pole. Když zadáte argumenty, zobrazí se ve výsledcích hledání **instalace PIP** nebo **conda** , následované obsahem vyhledávacího pole:

::: moniker range="vs-2017"
![Pomocí argumentů pip a conda install příkazy pro probuzení](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Pomocí argumentů pip a conda install příkazy pro probuzení](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Instalace balíčku vytvoří podsložky v rámci složky *lib* prostředí v systému souborů. Pokud máte například v *c:\Python36*nainstalované Python 3,6, balíčky jsou nainstalovány v *c:\Python36\Lib*; Pokud máte Anaconda3 nainstalované v adresáři *C:\Program Files\Anaconda3* , balíčky se nainstalují do složky *c:\Program Files\Anaconda3\Lib*. V prostředích conda se balíčky instalují do složky daného prostředí.

### <a name="grant-administrator-privileges-for-package-install"></a>Udělení oprávnění správce pro balíček nainstalovat

Při instalaci balíčků do prostředí, které je umístěné v chráněné oblasti systému souborů, jako je *C:\Program Files\Anaconda3\Lib*, musí sada Visual Studio `pip install` běžet se zvýšenými oprávněními, aby mohla vytvořit podsložky balíčku. Pokud je požadováno zvýšení oprávnění, aplikace Visual Studio zobrazí výzvu. **pro instalaci, aktualizaci nebo odebrání balíčků pro toto prostředí můžou být nutná oprávnění správce**:

![Výzvy ke zvýšení oprávnění pro instalaci balíčku](media/environments/environments-pip-elevate.png)

**Zvýšení oprávnění teď** uděluje oprávnění správce pro jednu operaci, a to v souladu s dalšími výzvami k zadání oprávnění operačního systému. Výběr možnosti **pokračovat bez oprávnění správce** se pokusí o instalaci balíčku, ale při pokusu o vytvoření složky s výstupem dojde k chybě PIP, například **Chyba: Nepodařilo se vytvořit C:\Program Files\Anaconda3\Lib\site-packages\png.py: oprávnění bylo odepřeno.**

Výběr možnosti **při instalaci nebo odebrání balíčků vždy zvýšit úroveň** zabraňuje tomu, aby se dialogové okno zobrazovalo pro dané prostředí. Pokud chcete dialog znovu zobrazit, klikněte na **nástroje** > **možnosti** > **Python** > **Obecné** a vyberte tlačítko, **resetujte všechna trvale skrytá dialogová okna**.

Na stejné kartě **Možnosti** můžete také vybrat možnost **vždy spustit PIP jako správce** a potlačit dialog pro všechna prostředí. Viz [Možnosti-karta Obecné](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Omezení zabezpečení se staršími verzemi Pythonu

Pokud používáte Python 2,6, 3,1 a 3,2, Visual Studio zobrazí upozornění **kvůli novým omezením zabezpečení, takže instalace z internetu nemusí v této verzi Pythonu fungovat**:

![Zpráva o pip nainstalovat omezení starší verze jazyka Python](media/environments/environments-old-version-restriction.png)

Důvodem upozornění je, že v těchto starších verzích Pythonu `pip install` neobsahují podporu pro TLS (Transport Security Layer) 1,2, která je nutná pro stahování balíčků ze zdroje balíčku, pypi.org. Vlastní buildy v Pythonu můžou podporovat TLS 1,2, v takovém případě může `pip install` fungovat.

Je možné stáhnout příslušné *Get-PIP.py* pro balíček z [bootstrap.pypa.IO](https://bootstrap.pypa.io/), ručně stáhnout balíček z [PyPI.org](https://pypi.org/)a pak balíček nainstalovat z této místní kopie.

Doporučení, ale stačí upgradovat na Python 2.7 nebo 3.3 +, ve kterém případ upozornění se nezobrazí.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Karta IntelliSense

Zobrazí aktuální stav databáze pro dokončování IntelliSense:

![Karta IntelliSense prostředí Pythonu](media/environments/environments-intellisense-tab.png)

- V aplikaci Visual Studio 2017 verze 15,5 a starší jsou dokončování IntelliSense závislé na databázi, která je zkompilována pro danou knihovnu. Vytváření databáze se provádí na pozadí, když knihovně je nainstalovaná, ale může nějakou dobu trvat a nemusí být úplné, když začnete psát kód.
- Visual Studio 2017 verze 15,6 a novější používá rychlejší způsob, jak zajistit doplňování, které ve výchozím nastavení nezávisí na databázi. Z tohoto důvodu je karta označena **IntelliSense [databáze zakázána]** . Databázi můžete povolit smazáním **nástrojů** možností > **možností** > **Python** > **experimentální** > **pro prostředí použít nový styl IntelliSense**.

Po zjišťuje nové prostředí sady Visual Studio (nebo přidejte jedno), automaticky se začne při kompilaci databáze díky analýze zdrojové soubory knihovny. Tento proces může trvat od minutu hodinu nebo déle v závislosti na tom, co je nainstalována. (Anaconda například obsahuje mnoho knihoven a určitou dobu potřebuje kompilovat databázi.) Po dokončení získáte detailní IntelliSense a nemusíte znovu aktualizovat databázi (pomocí tlačítka **obnovit databázi** ), dokud nenainstalujete více knihoven.

Knihovny, pro které nejsou zkompilována data, jsou označeny příznakem **!** ; Pokud databáze prostředí není dokončená, je to **!** také se vedle něj zobrazí v seznamu hlavních prostředí.

::: moniker-end

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu v aplikaci Visual Studio](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použití požadavků. txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
