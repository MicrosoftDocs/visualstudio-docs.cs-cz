---
title: Správa prostředí a interpretů Pythonu
description: Okno Prostředí Pythonu slouží ke správě globálních, virtuálních a kondičních prostředí, instalaci interpretů a balíčků Pythonu a přiřazování prostředí k projektům sady Visual Studio.
ms.date: 08/06/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e269e19a09aec157e38eaf8938b5995c2647803
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302831"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak vytvořit a spravovat prostředí Pythonu v sadě Visual Studio

*Prostředí* Pythonu je kontext, ve kterém spustíte kód Pythonu a zahrnuje globální, virtuální a conda prostředí. Prostředí se skládá z interpretu, knihovny (obvykle standardní knihovny Pythonu) a sady nainstalovaných balíčků. Tyto součásti společně určují, které jazykové konstrukce a syntaxe jsou platné, jaké funkce operačního systému můžete přistupovat a které balíčky můžete použít.

V sadě Visual Studio v systému Windows použijete okno **Prostředí Pythonu,** jak je popsáno v tomto článku, ke správě prostředí a k výběru jednoho jako výchozí pro nové projekty. Další aspekty prostředí se nacházejí v následujících článcích:

- Pro daný projekt můžete [vybrat konkrétní prostředí,](selecting-a-python-environment-for-a-project.md) nikoli použít výchozí.

- Podrobnosti o vytváření a používání virtuálních prostředí pro projekty Pythonu najdete v tématu [Použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Pokud chcete nainstalovat balíčky v prostředí, podívejte se na [odkaz na kartu Balíčky](python-environments-window-tab-reference.md#packages-tab).

- Chcete-li nainstalovat další interpret Pythonu, [přečtěte si informace o instalaci interpretů Pythonu](installing-python-interpreters.md). Obecně platí, že pokud stáhnete a spustíte instalační program pro hlavní distribuci Pythonu, Visual Studio zjistí, že nová instalace a prostředí se zobrazí v okně **Prostředí Pythonu** a může být vybráno pro projekty.

Pokud python utečte v Sadě Visual Studio, následující články také poskytují obecné pozadí:

- [Práce s Pythonem v Sadě Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalace podpory Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Prostředí pro kód Pythonu, který je otevřen pouze jako složka, nelze spravovat pomocí příkazu > **Otevřít** > **Folder** **složku.** Místo toho [vytvořte projekt Pythonu z existujícího kódu,](quickstart-01-python-in-visual-studio-project-from-existing-code.md) abyste si vychutnali funkce prostředí sady Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Pomocí příkazu **Otevřít** > **Open** > **složku** můžete spravovat prostředí pro kód Pythonu, který je otevřen jako složka. Panel nástrojů Pythonu umožňuje přepínat mezi všemi zjištěnými prostředími a také přidávat nové prostředí. Informace o prostředí jsou uloženy v souboru PythonSettings.json ve složce Workspace .vs.
::: moniker-end

## <a name="the-python-environments-window"></a>Okno Prostředí Pythonu

Prostředí, o kterých visual studio ví, jsou zobrazena v okně **Prostředí Pythonu.** Chcete-li otevřít okno, použijte jednu z následujících metod:

- Vyberte příkaz **Zobrazit** > **další** > prostředí Windows**Pythonu.**
- Klikněte pravým tlačítkem myši na uzel **Prostředí Pythonu** pro projekt v **Průzkumníku řešení** a vyberte **Zobrazit všechna prostředí Pythonu**:

    ::: moniker range="vs-2017"
    ![Příkaz Zobrazit všechna prostředí v Průzkumníku řešení](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Příkaz Zobrazit všechna prostředí v Průzkumníku řešení](media/environments/environments-view-all-2019.png)
    ::: moniker-end

V obou případech se vedle **Průzkumníka řešení**zobrazí okno Prostředí **Pythonu** :

::: moniker range="vs-2017"
![Okno Prostředí Pythonu](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno Prostředí Pythonu](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio hledá nainstalované globální prostředí pomocí registru (následující [PEP 514](https://www.python.org/dev/peps/pep-0514/)), spolu s virtuální prostředí a conda prostředí (viz [Typy prostředí](#types-of-environments)). Pokud v seznamu nevidíte očekávané prostředí, přečtěte [si informace o ruční identifikaci existujícího prostředí](#manually-identify-an-existing-environment).

Když vyberete prostředí v seznamu, Visual Studio zobrazí různé vlastnosti a příkazy pro toto prostředí na kartě **Přehled.** Na obrázku naobrázku například vidíte, že umístění interpreta je *C:\Python36-32*. Čtyři příkazy v dolní části karty **Přehled** otevřou příkazový řádek se spuštěným tlumočníkem. Další informace naleznete v [tématu Odkaz na kartu okna prostředí Pythonu – Přehled](python-environments-window-tab-reference.md#overview-tab).

Pomocí rozevíracího seznamu pod seznamem prostředí můžete přepnout na různé karty, jako jsou **balíčky**a **technologie IntelliSense**. Tyto karty jsou také popsány v [odkazu na kartu okna prostředí Pythonu](python-environments-window-tab-reference.md).

Výběr prostředí nezmění jeho vztah k žádné projekty. Výchozí prostředí, zobrazené tučným písmem v seznamu, je to, které visual studio používá pro všechny nové projekty. Chcete-li použít jiné prostředí s novými projekty, použijte **příkaz Nastavit toto výchozí prostředí pro nové projekty.** V rámci projektu můžete vždy vybrat konkrétní prostředí. Další informace naleznete v [tématu Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

Vpravo od každého uvedeného prostředí je ovládací prvek, který otevře **interaktivní** okno pro toto prostředí. (V sadě Visual Studio 2017 15.5 a starší se zobrazí jiný ovládací prvek, který aktualizuje databázi IntelliSense pro toto prostředí. Podrobnosti o databázi naleznete v [tématu Odkaz na kartu okna Prostředí.)](python-environments-window-tab-reference.md)

::: moniker range="vs-2017"
> [!Tip]
> Když rozbalíte okno **prostředí Pythonu** dostatečně široké, získáte úplnější zobrazení prostředí, se kterým můžete pracovat lépe.
>
> ![Rozšířené zobrazení okna Prostředí Pythonu](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Když rozbalíte okno **prostředí Pythonu** dostatečně široké, získáte úplnější zobrazení prostředí, se kterým můžete pracovat lépe.
>
> ![Rozšířené zobrazení okna Prostředí Pythonu](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Přestože Visual Studio respektuje možnost balíčky systémových webů, neposkytuje způsob, jak ji změnit z v rámci sady Visual Studio.

### <a name="what-if-no-environments-appear"></a>Co když se neobjeví žádná prostředí?

Pokud se nezobrazí žádná prostředí, znamená to, že Visual Studio nepodařilo rozpoznat žádné instalace Pythonu ve standardních umístěních. Například jste například nainstalovali Visual Studio 2017 nebo novější, ale zrušili všechny možnosti překladače v možnostech instalačního programu pro zatížení Pythonu. Podobně jste možná nainstalovali Visual Studio 2015 nebo starší, ale nenainstalovali jste interpret ručně (viz [Instalace překladačů Pythonu](installing-python-interpreters.md)).

Pokud víte, že máte v počítači interpret pythonu, ale Visual Studio (libovolná verze) ho nezjistilo, použijte příkaz **+ Custom** k ručnímu zadání jeho umístění. Viz další část [Ručně identifikovat existující prostředí](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio detekuje aktualizace existujícího interpreta, jako je například upgrade Pythonu 2.7.11 na 2.7.14 pomocí instalačních programů z python.org. Během procesu instalace starší prostředí zmizí ze seznamu **prostředí Pythonu** před aktualizace se zobrazí na jeho místě.
>
> Pokud však ručně přesunete interpreta a jeho prostředí pomocí systému souborů, visual studio nebude znát nové umístění. Další informace naleznete v [tématu Přesunutí tlumočníka](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Typy prostředí

Visual Studio může pracovat s globálními, virtuálními a conda prostředími.

#### <a name="global-environments"></a>Globální prostředí

Každá instalace Pythonu (například Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 atd., viz [Instalace interpretů Pythonu](installing-python-interpreters.md)) udržuje své vlastní *globální prostředí*. Každé prostředí se skládá z konkrétního interpretu Pythonu, jeho standardní knihovny, sady předinstalovaných balíčků a všech dalších balíčků, které nainstalujete, když je toto prostředí aktivováno. Instalace balíčku do globálního prostředí je k dispozici všem projektům používajícím toto prostředí. Pokud je prostředí umístěno v chráněné oblasti systému souborů (například v rámci *souborů c:\program),* vyžaduje instalace balíčků oprávnění správce.

Globální prostředí jsou k dispozici pro všechny projekty v počítači. V sadě Visual Studio vyberete jedno globální prostředí jako výchozí, které se používá pro všechny projekty, pokud pro projekt výslovně nezvolíte jiné prostředí. Další informace naleznete v [tématu Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Virtuální prostředí

I když práce v globálním prostředí je snadný způsob, jak začít, toto prostředí bude v průběhu času přeplněno mnoha různými balíčky, které jste nainstalovali pro různé projekty. Takový nepořádek ztěžuje důkladně otestovat aplikaci proti určité sadě balíčků se známými verzemi, což je přesně ten typ prostředí, které byste nastavili na serveru sestavení nebo webovém serveru. Ke konfliktům může dojít také v případě, že dva projekty vyžadují nekompatibilní balíčky nebo různé verze stejného balíčku.

Z tohoto důvodu vývojáři často vytvořit *virtuální prostředí* pro projekt. Virtuální prostředí je podsložka v projektu, která obsahuje kopii konkrétního interpreta. Při aktivaci virtuálního prostředí jsou všechny balíčky, které nainstalujete, nainstalovány pouze v podsložce tohoto prostředí. Když pak spustíte program Pythonu v tomto prostředí, víte, že je spuštěn pouze proti těmto konkrétním balíčkům.

Visual Studio poskytuje přímou podporu pro vytvoření virtuálního prostředí pro projekt. Pokud například otevřete projekt, který obsahuje *soubor requirements.txt*, nebo vytvoříte projekt ze šablony, která tento soubor obsahuje, zobrazí aplikace Visual Studio výzvu k automatickému vytvoření virtuálního prostředí a instalaci těchto závislostí.

Kdykoli v rámci otevřeného projektu můžete vytvořit nové virtuální prostředí. V **Průzkumníku řešení**rozbalte uzel projektu, klikněte pravým tlačítkem myši na **prostředí Pythonu**a vyberte "Přidat virtuální prostředí". Další informace naleznete [v tématu Vytvoření virtuálního prostředí](/visualstudio/python/selecting-a-python-environment-for-a-project?view=vs-2019#create-a-virtual-environment-1).

Visual Studio také poskytuje příkaz pro generování souboru *requirements.txt* z virtuálního prostředí, což usnadňuje opětovné vytvoření prostředí v jiných počítačích. Další informace naleznete v tématu [Použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Prostředí Conda

Prostředí conda je prostředí `conda` vytvořené pomocí nástroje nebo s integrovanou správou conda ve Visual Studiu 2017 verze 15.7 a vyšší. (Vyžaduje Anaconda nebo Miniconda, které jsou k dispozici prostřednictvím instalačního programu sady Visual Studio, viz [Instalace](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017).)

::: moniker range="vs-2017"

1. Vyberte **+ Vytvořit prostředí conda** v okně **Prostředí Pythonu,** které otevře kartu **Vytvořit nové prostředí conda:**

    ![Vytvořit kartu pro nové prostředí conda](media/environments/environments-conda-1.png)

1. Do pole **Název** zadejte název prostředí, v poli **Python** vyberte základní interpret Pythonu a vyberte **Vytvořit**.

1. Okno **Výstup** zobrazuje průběh pro nové prostředí s několika pokyny příkazového příkazu po dokončení vytváření:

    ![Úspěšné vytvoření prostředí conda](media/environments/environments-conda-2.png)

1. V rámci sady Visual Studio můžete aktivovat prostředí conda pro projekt stejně jako jakékoli jiné prostředí, jak je popsáno v [možnosti Vybrat prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

1. Chcete-li instalovat balíčky v prostředí, použijte [kartu Balíčky](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Vyberte **+ Přidat prostředí** v okně Prostředí **Pythonu** (nebo na panelu nástrojů Pythonu), který otevře dialogové okno **Přidat prostředí.** V tomto dialogovém okně vyberte kartu **Prostředí Conda:**

    ![Karta Prostředí Conda v dialogovém okně Přidat prostředí](media/environments/environments-conda-1-2019.png)

1. Nakonfigurujte následující pole:

    | Pole | Popis |
    | --- | --- |
    | Project | Projekt, ve kterém chcete vytvořit prostředí (pokud máte více projektů ve stejném řešení sady Visual Studio). |
    | Name (Název) | Název prostředí conda. |
    | Přidání balíčků z | Pokud máte soubor *environment.yml* popisující vaše závislosti, zvolte **Soubor prostředí** nebo zvolte Jeden nebo více názvů **balíčků Anaconda** a uveďte alespoň jeden balíček Pythonu nebo verzi Pythonu v poli níže. Seznam balíčků instruuje conda k vytvoření prostředí Pythonu. Chcete-li nainstalovat nejnovější verzi `python`Pythonu, použijte ; chcete-li nainstalovat určitou verzi, použijte `python=,major>.<minor>` jako v `python=3.7`. Pomocí tlačítka balíčku můžete také vybrat verze Pythonu a běžné balíčky z řady nabídek. |
    | Nastavit jako aktuální prostředí | Aktivuje nové prostředí ve vybraném projektu po vytvoření prostředí. |
    | Nastavit jako výchozí prostředí pro nové projekty | Automaticky nastaví a aktivuje prostředí conda ve všech nových projektech vytvořených v sadě Visual Studio. Tato možnost je stejná jako použití **provést toto výchozí prostředí pro nové projekty** v okně **Prostředí Pythonu.** |
    | Zobrazení v okně Prostředí Pythonu | Určuje, zda se má po vytvoření prostředí zobrazit okno **Prostředí Pythonu.** |

    > [!Important]
    > Při vytváření prostředí conda nezapomeňte zadat alespoň jednu verzi Pythonu nebo balíček Pythonu pomocí jednoho `environments.yml` nebo seznamu balíčků, který zajišťuje, že prostředí obsahuje modul runtime Pythonu. V opačném případě Visual Studio ignoruje prostředí: prostředí se nezobrazí nikde v okně **prostředí Pythonu,** není nastavena jako aktuální prostředí pro projekt a není k dispozici jako globální prostředí.
    >
    > Pokud náhodou vytvoříte prostředí conda bez verze `conda info` Pythonu, pomocí příkazu zobetřete umístění složek prostředí conda a pak ručně odeberte podsložku pro prostředí z tohoto umístění.

1. Vyberte **Vytvořit**a sledujte průběh v okně **Výstup.** Výstup obsahuje několik pokynů cli po dokončení vytváření:

    ![Úspěšné vytvoření prostředí conda](media/environments/environments-conda-2-2019.png)

1. V rámci sady Visual Studio můžete aktivovat prostředí conda pro projekt stejně jako jakékoli jiné prostředí, jak je popsáno v [možnosti Vybrat prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

1. Chcete-li nainstalovat další balíčky v prostředí, použijte [kartu Balíčky](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Pro dosažení nejlepších výsledků v prostředí conda použijte conda 4.4.8 nebo novější (verze conda se liší od verzí Anaconda). Vhodné verze Miniconda (Visual Studio 2019) a Anaconda (Visual Studio 2017) můžete nainstalovat prostřednictvím instalačního programu Visual Studia.

Chcete-li zobrazit verzi conda, kde jsou uložena prostředí `conda info` conda a další informace, spusťte na příkazovém řádku Anaconda (to znamená příkazový řádek, kde je Anaconda v cestě):

```cli
conda info
```

Složky prostředí conda se zobrazují takto:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Vzhledem k tomu, že prostředí conda nejsou uloženy s projektem, fungují podobně jako globální prostředí. Například instalace nového balíčku do prostředí conda zpřístupní tento balíček všem projektům používajícím toto prostředí.

Pro Visual Studio 2017 verze 15.6 a starší, můžete použít prostředí conda tak, že ukazuje na ně ručně, jak je popsáno v [ručně identifikovat existující prostředí](#manually-identify-an-existing-environment).

Visual Studio 2017 verze 15.7 a novější automaticky detekuje prostředí conda a zobrazí je v okně **Prostředí Pythonu,** jak je popsáno v další části.

## <a name="manually-identify-an-existing-environment"></a>Ruční identifikace existujícího prostředí

Pomocí následujících kroků můžete identifikovat prostředí, které je nainstalované v nestandardním umístění (včetně prostředí conda ve Visual Studiu 2017 verze 15.6 a starší):

::: moniker range="vs-2017"

1. Vyberte **+ Vlastní** v okně **Prostředí Pythonu,** které otevře kartu **Konfigurovat:**

    ![Výchozí zobrazení pro nové vlastní prostředí](media/environments/environments-custom-1.png)

1. Do pole **Popis** zadejte název prostředí.

1. Zadejte nebo procházejte (pomocí **...**) na cestu interpreta v poli **Předpona cesty.**

1. Pokud Visual Studio zjistí interpret pythonu v tomto umístění (například cesta uvedená níže pro prostředí conda), povolí příkaz **Automatické rozpoznání.** Výběrem **možnosti Automatické rozpoznání** se dokončí zbývající pole. Tato pole můžete také vyplnit ručně.

    ![Povolení příkazu Automatické rozpoznání](media/environments/environments-custom-2.png)

    ![Dokončení polí prostředí po použití automatického rozpoznání](media/environments/environments-custom-3.png)

1. Jakmile pole obsahují požadované hodnoty, vyberte **Použít pro** uložení konfigurace. Nyní můžete použít prostředí jako jakékoli jiné v rámci sady Visual Studio.

1. Pokud potřebujete odebrat ručně identifikované prostředí, vyberte příkaz **Odebrat** na kartě **Konfigurovat.** Automaticky zjištěná prostředí tuto možnost neposkytují. Další informace naleznete v tématu [Konfigurace karty](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Vyberte **+ Přidat prostředí** v okně Prostředí **Pythonu** (nebo na panelu nástrojů Pythonu), který otevře dialogové okno **Přidat prostředí.** V tomto dialogovém okně vyberte kartu **Existující prostředí:**

    ![Karta Existující prostředí v dialogovém okně Přidat prostředí](media/environments/environments-custom-1-2019.png)

1. Vyberte rozevírací seznam **Prostředí** a pak vyberte **Vlastní**:

    ![Možnost vlastní prostředí v dialogovém okně Přidat prostředí](media/environments/environments-custom-2-2019.png)

1. Do zadaných polí v dialogovém okně zadejte nebo procházejte (pomocí **...**) na cestu interpreta v části **Cesta předpony**, která vyplňuje většinu ostatních polí. Po kontrole těchto hodnot a podle potřeby je upravte vyberte **Přidat**. 

    ![Pole pro určení podrobností pro možnost vlastního prostředí v dialogovém okně Přidat prostředí](media/environments/environments-custom-3-2019.png)

1. Podrobnosti o prostředí lze kdykoli zkontrolovat a upravit v okně **Prostředí Pythonu.** V tomto okně vyberte prostředí a pak vyberte kartu **Konfigurovat.** Po provedení změn vyberte příkaz **Použít.** Prostředí můžete také odebrat pomocí příkazu **Odebrat** (není k dispozici pro automaticky zjištěná prostředí). Další informace naleznete v tématu [Konfigurace karty](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Oprava nebo odstranění neplatných prostředí

Pokud Visual Studio najde položky registru pro prostředí, ale cesta k interpretu je neplatná, pak se v okně **Prostředí Pythonu** zobrazí název s přeškrtnutím písma:

::: moniker range="vs-2017"
![Okno Prostředí Pythonu zobrazující neplatné prostředí](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno Prostředí Pythonu zobrazující neplatné prostředí](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Chcete-li opravit prostředí, které chcete zachovat, zkuste nejprve použít proces **opravy** instalačního programu. Instalátory pro standardní Python 3.x, například, zahrnout tuto možnost.

Chcete-li opravit prostředí, které nemá možnost opravy, nebo odebrat neplatné prostředí, použijte následující kroky k přímé úpravě registru. Visual Studio automaticky aktualizuje okno **Prostředí Pythonu** při provádění změn v registru.

1. Spusťte *program regedit.exe*.
1. Přejděte na **HKEY_LOCAL_MACHINE\SOFTWARE\Python**. Pro IronPython, podívejte se na **IronPython** místo.
1. Rozbalte uzel, který odpovídá distribuci, například **Python Core** pro CPython nebo **ContinuumAnalytics** pro Anaconda. Pro IronPython rozbalte uzel číslo verze.
1. Zkontrolujte hodnoty v uzlu **InstallPath:**

    ![Položky registru pro typickou instalaci CPython](media/environments/environments-registry-entries.png)

    - Pokud prostředí v počítači stále existuje, změňte hodnotu **aplikace ExecutablePath** na správné umístění. Podle potřeby opravte také hodnoty **(Výchozí)** a **WindowedExecutablePath.**
    - Pokud prostředí v počítači již neexistuje a chcete jej odebrat z okna **Prostředí Pythonu,** odstraňte nadřazený uzel **InstallPath**, například **3.6** ve výše uvedeném obrázku.

## <a name="see-also"></a>Viz také

- [Instalace interpretů Pythonu](installing-python-interpreters.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použití souboru requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
- [Odkaz na okno prostředí Pythonu](python-environments-window-tab-reference.md)
