---
title: Referenční dokumentace okna prostředí Pythonu
description: Podrobnosti o jednotlivých kartách, které se zobrazují v okně prostředí Pythonu v aplikaci Visual Studio.
ms.date: 03/18/2019
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: f08709c5231b2981db67900f47b49503269e948b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545493"
---
# <a name="python-environments-window-tabs-reference"></a>Referenční dokumentace karet oken prostředí Pythonu

Otevření okna **prostředí Pythonu** :

- Vyberte příkaz nabídky **Zobrazit**  >  **Další**  >  **prostředí Windows Python** .
- Klikněte pravým tlačítkem myši na uzel **prostředí Pythonu** pro projekt v **Průzkumník řešení** a vyberte **Zobrazit všechna prostředí Pythonu**.

Pokud rozbalíte okno **prostředí Pythonu** dostatečně v širším rozsahu, tyto možnosti se zobrazí jako karty, které vám mohou být užitečné při práci s nástrojem. Pro přehlednost jsou karty v tomto článku zobrazeny v rozbaleném zobrazení.

::: moniker range="vs-2017"
![Rozšířená zobrazení okna prostředí Pythonu](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozšířená zobrazení okna prostředí Pythonu](media/environments/environments-expanded-view-2019.png)
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
| **Nastavit toto prostředí jako výchozí pro nové projekty** | Nastaví aktivní prostředí, což může způsobit, že sada Visual Studio (2017 verze 15,5 a starší) krátce přestane reagovat při načtení databáze IntelliSense. Prostředí s mnoha balíčky nemusí reagovat déle. |
| **Navštívit web distributora** | Otevře prohlížeč na adrese URL, kterou poskytuje distribuce Pythonu. Python 3. x, například odkazuje na python.org. |
| **Otevřít interaktivní okno** | Otevře [interaktivní okno (REPL)](python-interactive-repl-in-visual-studio.md) pro toto prostředí v sadě Visual Studio, přičemž použije všechny [spouštěcí skripty (viz níže)](#startup-scripts). |
| **Prozkoumat interaktivní skripty** | Viz [skripty při spuštění](#startup-scripts). |
| **Použít interaktivní režim IPython** | Při nastavení otevře **interaktivní** okno s IPython ve výchozím nastavení. Tím povolíte vložené zobrazení a také rozšířenou syntaxi IPython, například `name?` zobrazení nápovědu a `!command` příkazů prostředí. Tato možnost se doporučuje při použití Anaconda distribuce, protože vyžaduje dodatečné balíčky. Další informace najdete v tématu [použití IPython v interaktivním okně](interactive-repl-ipython.md). |
| **Otevřít v PowerShellu** | Spustí překladač v příkazovém okně prostředí PowerShell. |
| (Odkazy složky a programu) | Poskytněte rychlý přístup k instalační složce prostředí, interpretu *python.exe* a interpretu *pythonw.exe* . První se otevře v Průzkumníkovi Windows, druhá z nich otevře okno konzoly. |

### <a name="startup-scripts"></a>Spouštěcí skripty

Při používání interaktivních oken v rámci každodenního pracovního postupu pravděpodobně vyvíjíte pomocné funkce, které pravidelně používáte. Můžete například vytvořit funkci, která otevře datový rámec v aplikaci Excel, a pak tento kód Uložit jako spouštěcí skript, aby byl vždy k dispozici v **interaktivním** okně.

Spouštěcí skripty obsahují kód, který **interaktivní** okno načte a spustí automaticky, včetně importů, definic funkcí a doslova cokoli jiného. Na tyto skripty se odkazuje dvěma způsoby:

1. Při instalaci prostředí Visual Studio vytvoří složku *Documents\Visual Studio \<version> \\ \<environment> \Python* , kde &lt; verze &gt; je verze sady Visual Studio (například 2017 nebo 2019) a &lt; prostředí &gt; odpovídá názvu prostředí. Můžete snadno přejít do složky specifické pro konkrétní prostředí pomocí příkazu **prozkoumat interaktivní skripty** . Když spustíte **interaktivní** okno pro toto prostředí, načte a spustí jakékoli soubory *. py* v abecedním pořadí.

1. Ovládací prvek **skripty** v **nabídce**  >  **Možnosti**nástrojů  >  karta interaktivní okna**Pythonu**  >  **Interactive Windows** (viz [Možnosti interaktivního Windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) je určena k určení další složky pro spouštěcí skripty, které se načítají a spouštějí ve všech prostředích. Tato funkce ale v současné době nefunguje.

## <a name="configure-tab"></a>Karta konfigurovat

Pokud je k dispozici, karta **Konfigurovat** obsahuje podrobnosti, jak je popsáno v následující tabulce. Pokud tato karta není k dispozici, znamená to, že Visual Studio spravuje všechny podrobnosti automaticky.

::: moniker range="vs-2017"
![Karta konfigurace prostředí Pythonu](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta konfigurace prostředí Pythonu](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Pole | Popis |
| --- | --- |
| **Popis** | Název, který má prostředí poskytnout. |
| **Cesta k předponě** | Umístění základní složky překladače. Když vyplníte tuto hodnotu a kliknete na **Automatické rozpoznávání**, Visual Studio se pokusí vyplnit ostatní pole za vás. |
| **Cesta k interpretu** | Cesta ke spustitelnému souboru interpreta, obvykle cesta k předponě následovaný **python.exe** |
| **Interpret v okně** | Cesta ke spustitelnému souboru bez konzoly, často i cestu předpony, za kterou následuje **pythonw.exe**. |
| **Cesta ke knihovně**<br/>(Pokud je k dispozici) | Určuje kořen standardní knihovny, ale tato hodnota se může ignorovat, pokud Visual Studio dokáže vyžádat přesnější cestu od překladače. |
| **Verze jazyka** | Vybráno z rozevírací nabídky. |
| **Architektura** | Obvykle se detekuje a vyplní automaticky, jinak určuje **32** bitů nebo **64**. |
| **Proměnná prostředí PATH** | Proměnná prostředí, kterou interpret používá k nalezení cest hledání. Visual Studio změní hodnotu proměnné při spuštění Pythonu, aby obsahovala cesty pro hledání projektu. Obvykle by tato vlastnost měla být nastavená na **PYTHONPATH**, ale některé překladače používají jinou hodnotu. |

## <a name="packages-tab"></a>Karta balíčky

*Také označený jako PIP v dřívějších verzích.*

Spravuje balíčky nainstalované v prostředí pomocí PIP (karta **balíčky (PyPi)** ) nebo conda (karta **balíčky (conda)** pro prostředí conda ve Visual Studiu 2017 verze 15,7 a novější). Na této kartě můžete také vyhledat a nainstalovat nové balíčky, včetně jejich závislostí.

Balíčky, které jsou už nainstalované, se zobrazují s ovládacími prvky pro aktualizaci (šipka nahoru) a odinstalování (X v kruhu) balíčku:

![Karta balíčky prostředí Pythonu](media/environments/environments-pip-tab-controls.png)

Při zadání hledaného výrazu se vyfiltruje seznam nainstalovaných balíčků a balíčků, které se dají nainstalovat z PyPI.

::: moniker range="vs-2017"
![Karta balíčky prostředí Pythonu s hledáním na "číslo"](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta balíčky prostředí Pythonu s hledáním na "číslo"](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Jak vidíte na obrázku výše, výsledky hledání zobrazují počet balíčků, které odpovídají hledanému termínu; první položka v seznamu je však příkaz ke spuštění **instalace \<name> PIP** přímo. Pokud se nacházíte na kartě **balíčky (conda)** , zobrazí se místo toho **instalace \<name> conda **:

::: moniker range="vs-2017"
![Karta balíčky conda zobrazující příkaz pro instalaci conda](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Karta balíčky conda zobrazující příkaz pro instalaci conda](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

V obou případech můžete instalaci přizpůsobit přidáním argumentů do vyhledávacího pole za název balíčku. Když zadáte argumenty, zobrazí se ve výsledcích hledání **instalace PIP** nebo **conda** , následované obsahem vyhledávacího pole:

::: moniker range="vs-2017"
![Použití argumentů v PIP a conda Install Commands](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Použití argumentů v PIP a conda Install Commands](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Instalace balíčku vytvoří podsložky v rámci složky *lib* prostředí v systému souborů. Pokud máte například v *c:\Python36*nainstalované Python 3,6, balíčky jsou nainstalovány v *c:\Python36\Lib*; Pokud máte Anaconda3 nainstalované v adresáři *C:\Program Files\Anaconda3* , balíčky se nainstalují do složky *c:\Program Files\Anaconda3\Lib*. V prostředích conda se balíčky instalují do složky daného prostředí.

### <a name="grant-administrator-privileges-for-package-install"></a>Udělení oprávnění správce pro instalaci balíčku

Při instalaci balíčků do prostředí, které je umístěné v chráněné oblasti systému souborů, jako je *C:\Program Files\Anaconda3\Lib*, musí sada Visual Studio běžet `pip install` se zvýšenými oprávněními, aby mohla vytvořit podsložky balíčku. Pokud je požadováno zvýšení oprávnění, aplikace Visual Studio zobrazí výzvu. **pro instalaci, aktualizaci nebo odebrání balíčků pro toto prostředí můžou být nutná oprávnění správce**:

![Výzva ke zvýšení oprávnění pro instalaci balíčku](media/environments/environments-pip-elevate.png)

**Zvýšení oprávnění teď** uděluje oprávnění správce pro jednu operaci, a to v souladu s dalšími výzvami k zadání oprávnění operačního systému. Výběr možnosti **pokračovat bez oprávnění správce** se pokusí o instalaci balíčku, ale při pokusu o vytvoření složky s výstupem dojde k chybě PIP, například **Chyba: Nepodařilo se vytvořit C:\Program Files\Anaconda3\Lib\site-packages\png.py: oprávnění bylo odepřeno.**

Výběr možnosti **při instalaci nebo odebrání balíčků vždy zvýšit úroveň** zabraňuje tomu, aby se dialogové okno zobrazovalo pro dané prostředí. Pokud chcete dialog znovu zobrazit, klikněte na **nástroje**  >  **Možnosti**jazyka  >  **Python**  >  **Obecné** a vyberte tlačítko a **obnovte všechna trvale skrytá dialogová okna**.

Na stejné kartě **Možnosti** můžete také vybrat možnost **vždy spustit PIP jako správce** a potlačit dialog pro všechna prostředí. Viz [Možnosti-karta Obecné](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Omezení zabezpečení ve starších verzích Pythonu

Pokud používáte Python 2,6, 3,1 a 3,2, Visual Studio zobrazí upozornění **kvůli novým omezením zabezpečení, takže instalace z internetu nemusí v této verzi Pythonu fungovat**:

![Zpráva o omezeních instalace PIP se starší verzí Pythonu](media/environments/environments-old-version-restriction.png)

Důvodem upozornění je, že tyto starší verze Pythonu `pip install` neobsahují podporu pro TLS (Transport Security Layer) 1,2, která je nutná pro stahování balíčků ze zdroje balíčku PyPI.org. Vlastní buildy v Pythonu můžou podporovat protokol TLS 1,2, který `pip install` může fungovat.

Je možné stáhnout příslušné *Get-PIP.py* pro balíček z [bootstrap.pypa.IO](https://bootstrap.pypa.io/), ručně stáhnout balíček z [PyPI.org](https://pypi.org/)a pak balíček nainstalovat z této místní kopie.

Doporučení je ale jednoduše upgradovat na Python 2,7 nebo 3.3 +. v takovém případě se upozornění nezobrazí.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Karta IntelliSense

Zobrazuje aktuální stav databáze dokončování technologie IntelliSense:

![Prostředí Pythonu – karta technologie IntelliSense](media/environments/environments-intellisense-tab.png)

- V aplikaci Visual Studio 2017 verze 15,5 a starší jsou dokončování IntelliSense závislé na databázi, která je zkompilována pro danou knihovnu. Sestavování databáze se provádí na pozadí, když je knihovna nainstalovaná, ale může nějakou dobu trvat a nemusí být dokončená, když začnete psát kód.
- Visual Studio 2017 verze 15,6 a novější používá rychlejší způsob, jak zajistit doplňování, které ve výchozím nastavení nezávisí na databázi. Z tohoto důvodu je karta označena **IntelliSense [databáze zakázána]**. Databázi můžete povolit smazáním možností **nástroje**  >  **Možnosti**pro  >  použití**Python**  >  **experimentální**  >  **použít nový styl IntelliSense pro prostředí**.

Když Visual Studio rozpozná nové prostředí (nebo ho přidáte), automaticky začne kompilovat databázi analýzou zdrojových souborů knihovny. Tento proces může trvat několik minut až hodinu, a to v závislosti na tom, co je nainstalováno. (Anaconda například obsahuje mnoho knihoven a určitou dobu potřebuje kompilovat databázi.) Po dokončení získáte detailní IntelliSense a nemusíte znovu aktualizovat databázi (pomocí tlačítka **obnovit databázi** ), dokud nenainstalujete více knihoven.

Knihovny, pro které nejsou zkompilována data, jsou označeny příznakem **!**; Pokud databáze prostředí není dokončená, je to **!** zobrazí se také vedle sebe v seznamu hlavní prostředí.

::: moniker-end

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu v aplikaci Visual Studio](managing-python-environments-in-visual-studio.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použít requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
