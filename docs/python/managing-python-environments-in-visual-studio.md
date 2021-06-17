---
title: Správa prostředí a překladačů v Pythonu
description: Použijte okno prostředí Pythonu ke správě globálních, virtuálních a conda prostředí, instalaci překladačů a balíčků Pythonu a přiřazení prostředí k projektům sady Visual Studio.
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 26bcf0fa4d56d4e8df100a0d3e65904d065d8757
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254872"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak vytvářet a spravovat prostředí Pythonu v aplikaci Visual Studio

**Prostředí Python** je kontext, ve kterém spouštíte kód Pythonu a zahrnuje globální, virtuální a conda prostředí. Prostředí se skládá z překladače, knihovny (obvykle standardní knihovny Pythonu) a sady nainstalovaných balíčků. Tyto komponenty společně určují, jaké jazykové konstrukce a syntaxi jsou platné, k jakým funkcím operačního systému máte přístup a které balíčky můžete použít.

V aplikaci Visual Studio ve Windows můžete pomocí okna **prostředí Pythonu** , jak je popsáno v tomto článku, spravovat prostředí a vybrat ho jako výchozí pro nové projekty. Další aspekty prostředí najdete v následujících článcích:

- Pro libovolný daný projekt můžete místo použití výchozího nastavení [vybrat konkrétní prostředí](selecting-a-python-environment-for-a-project.md) .

- Podrobnosti o vytváření a používání virtuálních prostředí pro projekty v Pythonu najdete v tématu [použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Pokud chcete nainstalovat balíčky do prostředí, přečtěte si [odkaz na kartu balíčky](python-environments-window-tab-reference.md#packages-tab).

- Pokud chcete nainstalovat další interpret Pythonu, přečtěte si téma [instalace překladačů Pythonu](installing-python-interpreters.md). Obecně platí, že pokud stahujete a spouštíte instalační program pro distribuci Pythonu hlavní, Visual Studio zjistí, že se nová instalace a prostředí zobrazí v okně **prostředí Pythonu** a že je možné je vybrat pro projekty.

Pokud v aplikaci Visual Studio začínáte s Pythonem, následující články také poskytují z obecného pozadí:

- [Práce s Pythonem v aplikaci Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalace podpory jazyka Python v sadě Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Prostředí pro kód Pythonu, která se otevírají jenom jako složka, se nedají spravovat pomocí  >  příkazu **otevřít**  >  **složku** v souboru. Místo toho [vytvořte projekt v Pythonu z existujícího kódu](quickstart-01-python-in-visual-studio-project-from-existing-code.md) pro využívání funkcí prostředí sady Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Prostředí pro kód Pythonu, který se otevírá jako složka, můžete spravovat pomocí   >  příkazu **otevřít**  >  **složku** v souboru. Panel nástrojů Python umožňuje přepínat mezi všemi zjištěnými prostředími a také přidat nové prostředí. Informace o prostředí jsou uloženy v PythonSettings.jssouboru ve složce Workspace. vs.
::: moniker-end

## <a name="the-python-environments-window"></a>Okno prostředí Pythonu

Prostředí, o kterých aplikace Visual Studio ví, se zobrazí v okně **prostředí Pythonu** . Chcete-li otevřít okno, použijte jednu z následujících metod:

- Vyberte příkaz nabídky **Zobrazit**  >  **Další**  >  **prostředí Windows Python** .
- Klikněte pravým tlačítkem myši na uzel **prostředí Pythonu** pro projekt v **Průzkumník řešení** a vyberte **Zobrazit všechna prostředí Pythonu**:

    ::: moniker range="vs-2017"
    ![Zobrazit všechna prostředí – příkaz v Průzkumník řešení](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Zobrazit všechna prostředí – příkaz v Průzkumník řešení](media/environments/environments-view-all-2019.png)
    ::: moniker-end

V obou případech se okno **prostředí Pythonu** zobrazuje vedle **Průzkumník řešení**:

::: moniker range="vs-2017"
![Okno prostředí Pythonu](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno prostředí Pythonu](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio hledá nainstalovaná globální prostředí pomocí registru (následující [PEP 514](https://www.python.org/dev/peps/pep-0514/)) společně s virtuálními prostředími a conda prostředími (viz [typy prostředí](#types-of-environments)). Pokud v seznamu nevidíte očekávané prostředí, přečtěte si téma [Ruční identifikace stávajícího prostředí](#manually-identify-an-existing-environment).

Když v seznamu vyberete prostředí, Visual Studio zobrazí na kartě **Přehled** různé vlastnosti a příkazy pro toto prostředí. Můžete například vidět na obrázku výše, kde je umístění interpretu *C:\Python36-32*. Čtyři příkazy v dolní části karty **Přehled** každý otevřete příkazový řádek se spuštěným překladačem. Další informace najdete v tématu [referenční materiály pro prostředí Pythonu karta okna – Přehled](python-environments-window-tab-reference.md#overview-tab).

Pomocí rozevíracího seznamu pod seznamem prostředí přepnete na různé karty, jako jsou **balíčky** a **IntelliSense**. Tyto karty jsou také popsány v [referenčních informacích o kartě okna prostředí Pythonu](python-environments-window-tab-reference.md).

Výběr prostředí nemění jeho vztah na žádné projekty. Výchozí prostředí, zobrazené tučným písmem v seznamu, je ten, který aplikace Visual Studio používá pro všechny nové projekty. Chcete-li použít jiné prostředí s novými projekty, použijte příkaz **nastavit toto výchozí prostředí pro nové projekty** . V rámci projektu můžete vždy vybrat konkrétní prostředí. Další informace najdete v tématu [Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

Napravo od každého uvedeného prostředí je ovládací prvek, který otevře **interaktivní** okno pro toto prostředí. (V aplikaci Visual Studio 2017 15,5 a starší se zobrazí jiný ovládací prvek, který aktualizuje databázi IntelliSense pro dané prostředí. Podrobnosti o databázi najdete v tématu Referenční informace o [kartě okna prostředí](python-environments-window-tab-reference.md) .)

::: moniker range="vs-2017"
> [!Tip]
> Když rozbalíte okno **prostředí Pythonu** dostatečně v celé řadě, získáte kompletní pohled na vaše prostředí, která vám můžou být pohodlnější pracovat.
>
> ![Rozšířená zobrazení okna prostředí Pythonu](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Když rozbalíte okno **prostředí Pythonu** dostatečně v celé řadě, získáte kompletní pohled na vaše prostředí, která vám můžou být pohodlnější pracovat.
>
> ![Rozšířená zobrazení okna prostředí Pythonu](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> I když Visual Studio respektuje možnost systém-site-Packages, neposkytuje způsob, jak ho změnit v sadě Visual Studio.

### <a name="what-if-no-environments-appear"></a>Co když se nezobrazí žádná prostředí?

Pokud se nezobrazí žádná prostředí, znamená to, že se aplikaci Visual Studio nepodařilo detekovat jakékoli instalace Pythonu ve standardních umístěních. Například jste nainstalovali aplikaci Visual Studio 2017 nebo novější, ale vymažete všechny možnosti překladače v možnostech instalačního programu pro úlohu Pythonu. Podobně je možné, že jste nainstalovali Visual Studio 2015 nebo starší, ale nenainstalovali jste překladač ručně (viz [instalace překladačů Pythonu](installing-python-interpreters.md)).

Pokud víte, že máte na svém počítači překladač Pythonu, ale Visual Studio (jakákoli verze) ho nerozpoznal, použijte k určení umístění ručně **vlastní příkaz +** . V další části se [ručně Identifikujte existující prostředí](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio detekuje Aktualizace existujícího překladače, jako je například upgrade Pythonu 2.7.11 na 2.7.14 pomocí instalačních programů z python.org. V průběhu instalace starší prostředí zmizí ze seznamu **prostředí Pythonu** před tím, než se aktualizace objeví na svém místě.
>
> Pokud však ručně přesunete interpret a jeho prostředí pomocí systému souborů, Visual Studio nezjistí nové umístění. Další informace najdete v tématu [Přesun překladače](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Typy prostředí

Visual Studio může pracovat s globálním, virtuálním a conda prostředími.

#### <a name="global-environments"></a>Globální prostředí

Každá instalace Pythonu (například Python 2,7, Python 3,6, Python 3,7, Anaconda 4.4.0 atd., viz [instalace překladačů Pythonu](installing-python-interpreters.md)) udržuje vlastní *globální prostředí*. Každé prostředí se skládá z konkrétního interpretu Pythonu, jeho standardní knihovny, sady předinstalovaných balíčků a všech dalších balíčků, které nainstalujete během aktivace prostředí. Instalace balíčku do globálního prostředí zpřístupňuje všechny projekty, které používají toto prostředí. Pokud se prostředí nachází v chráněné oblasti systému souborů (například v adresáři *c:\Program Files*), pak instalace balíčků vyžaduje oprávnění správce.

Globální prostředí jsou dostupná pro všechny projekty v počítači. V aplikaci Visual Studio vyberete jedno globální prostředí jako výchozí, které se používá pro všechny projekty, pokud jste si konkrétně nezvolili jiný projekt. Další informace najdete v tématu [Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Virtuální prostředí

I když práce v globálním prostředí představuje snadný způsob, jak začít, bude toto prostředí v průběhu času fungovat s mnoha různými balíčky, které jste nainstalovali pro různé projekty. Takovým zbytečným způsobem je obtížné důkladně otestovat aplikaci proti určité sadě balíčků se známými verzemi, což je přesně druh prostředí, které jste nastavili na serveru sestavení nebo na webovém serveru. Konflikty mohou nastat i v případě, že dva projekty vyžadují nekompatibilní balíčky nebo různé verze stejného balíčku.

Z tohoto důvodu vývojáři často vytvářejí *virtuální prostředí* pro projekt. Virtuální prostředí je podsložka v projektu, která obsahuje kopii konkrétního interpretu. Když aktivujete virtuální prostředí, všechny balíčky, které nainstalujete, se nainstalují jenom do podsložky tohoto prostředí. Když potom v tomto prostředí spustíte program v Pythonu, víte, že běží jenom pro konkrétní balíčky.

Visual Studio poskytuje přímou podporu pro vytváření virtuálních prostředí pro projekt. Pokud například otevřete projekt, který obsahuje *requirements.txt*, nebo vytvořte projekt ze šablony, která obsahuje tento soubor, aplikace Visual Studio zobrazí výzvu k automatickému vytvoření virtuálního prostředí a instalaci těchto závislostí.

V otevřeném projektu můžete kdykoli vytvořit nové virtuální prostředí. V **Průzkumník řešení** rozbalte uzel projekt, klikněte pravým tlačítkem na **prostředí Python** a vyberte Přidat virtuální prostředí. Další informace najdete v tématu [Vytvoření virtuálního prostředí](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1).

Visual Studio také poskytuje příkaz pro vygenerování *requirements.txt* souboru z virtuálního prostředí, což usnadňuje opětovné vytvoření prostředí v jiných počítačích. Další informace najdete v tématu [použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Prostředí conda

Prostředí conda je vytvořeno pomocí `conda` nástroje nebo s integrovanou správou conda v sadě Visual Studio 2017 verze 15,7 a vyšší. (Vyžaduje Anaconda nebo Miniconda, které jsou k dispozici prostřednictvím instalačního programu sady Visual Studio, viz [instalace](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017).)

::: moniker range="vs-2017"

1. V okně **prostředí Pythonu** vyberte **+ vytvořit conda prostředí** , ve kterém se otevře karta **vytvořit novou conda prostředí** :

    ![Vytvořit kartu pro nové prostředí conda](media/environments/environments-conda-1.png)

1. Do pole **název** zadejte název prostředí, v poli **Python** vyberte základní interpret Pythonu a vyberte **vytvořit**.

1. V okně **výstup** se zobrazí průběh nového prostředí. po dokončení vytváření se zobrazí několik instrukcí pro rozhraní příkazového řádku:

    ![Úspěšné vytvoření prostředí conda](media/environments/environments-conda-2.png)

1. V rámci sady Visual Studio můžete aktivovat prostředí conda pro projekt stejně jako jakékoli jiné prostředí, jak je popsáno v tématu [Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

1. K instalaci balíčků do prostředí použijte [kartu balíčky](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Vyberte **Přidat prostředí...** v okně **prostředí Pythonu** (nebo na panelu nástrojů Python), ve kterém se otevře dialogové okno **Přidat prostředí** . V tomto dialogovém okně vyberte kartu **prostředí conda** :

    ![Karta prostředí conda v dialogovém okně Přidat prostředí](media/environments/environments-conda-1-2019.png)

1. Nakonfigurujte následující pole:

    | Pole | Description |
    | --- | --- |
    | Project | Projekt, ve kterém má být prostředí vytvořeno (Pokud máte více projektů ve stejném řešení sady Visual Studio). |
    | Name | Název prostředí conda |
    | Přidat balíčky z | Vyberte **soubor prostředí** , pokud máte soubor *Environment. yml* popisující vaše závislosti, nebo vyberte **jeden nebo více názvů balíčků Anaconda** a v níže uvedeném poli uveďte aspoň jeden balíček Pythonu nebo verzi Pythonu. Seznam balíčků instruuje Conda, aby vytvořil prostředí Pythonu. K instalaci nejnovější verze Pythonu použijte `python` ; k instalaci konkrétní verze použijte `python=,major>.<minor>` jako v `python=3.7` . Pomocí tlačítka balíček můžete také vybrat verze Pythonu a běžné balíčky z řady nabídek. |
    | Nastavit jako aktuální prostředí | Aktivuje nové prostředí ve vybraném projektu po vytvoření prostředí. |
    | Nastavit jako výchozí prostředí pro nové projekty | Automaticky nastaví a aktivuje prostředí conda v jakémkoli novém projektu vytvořeném v sadě Visual Studio. Tato možnost je stejná jako při použití možnosti **nastavit toto výchozí prostředí pro nové projekty** v okně **prostředí Pythonu** . |
    | Zobrazit v okně prostředí Pythonu | Určuje, jestli se má po vytvoření prostředí zobrazit okno  **prostředí Pythonu** . |

    > [!Important]
    > Při vytváření prostředí conda Nezapomeňte zadat alespoň jednu verzi Pythonu nebo balíček Pythonu pomocí `environments.yml` nebo seznamu balíčků, který zajišťuje, že prostředí obsahuje modul runtime Pythonu. V opačném případě sada Visual Studio ignoruje prostředí: prostředí se nezobrazuje kdekoli v okně **prostředí Pythonu** , není nastavené jako aktuální prostředí pro projekt a není k dispozici jako globální prostředí.
    >
    > Pokud vytvoříte prostředí conda bez verze Pythonu, pomocí `conda info` příkazu Zobrazte umístění složek prostředí conda a pak z tohoto umístění ručně odeberte podsložku pro prostředí.

1. Vyberte **vytvořit** a sledujte průběh v okně **výstup** . Výstup obsahuje několik instrukcí rozhraní příkazového řádku po dokončení vytváření:

    ![Úspěšné vytvoření prostředí conda](media/environments/environments-conda-2-2019.png)

1. V rámci sady Visual Studio můžete aktivovat prostředí conda pro projekt stejně jako jakékoli jiné prostředí, jak je popsáno v tématu [Výběr prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

1. K instalaci dalších balíčků v prostředí použijte [kartu balíčky](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Pro dosažení nejlepších výsledků v prostředích conda použijte conda 4.4.8 nebo novější (verze conda se liší od verzí Anaconda). Pomocí instalačního programu sady Visual Studio můžete nainstalovat vhodné verze Miniconda (Visual Studio 2019) a Anaconda (Visual Studio 2017).

Pokud chcete zobrazit verzi Conda, kde jsou uložená prostředí conda a další informace, spusťte `conda info` na příkazovém řádku Anaconda (tj. na příkazovém řádku, kde Anaconda je v cestě):

```cli
conda info
```

Vaše složky prostředí conda se zobrazí takto:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Vzhledem k tomu, že prostředí conda nejsou uložena v projektu, fungují podobně jako globální prostředí. Například při instalaci nového balíčku do prostředí conda se tento balíček zpřístupní pro všechny projekty, které používají toto prostředí.

Pro Visual Studio 2017 verze 15,6 a starší můžete použít prostředí conda tak, že na ně najdou ručně, jak je popsáno v části [Ruční identifikace stávajícího prostředí](#manually-identify-an-existing-environment).

Visual Studio 2017 verze 15,7 a novější detekuje prostředí conda automaticky a zobrazí je v okně **prostředí Pythonu** , jak je popsáno v následující části.

## <a name="manually-identify-an-existing-environment"></a>Ruční identifikace stávajícího prostředí

Pomocí následujících kroků můžete identifikovat prostředí, které je nainstalované v nestandardním umístění (včetně prostředí conda ve Visual Studiu 2017 verze 15,6 a starší):

::: moniker range="vs-2017"

1. V okně **prostředí Pythonu** vyberte **+ vlastní** a otevřete kartu **Konfigurovat** :

    ![Výchozí zobrazení pro nové vlastní prostředí](media/environments/environments-custom-1.png)

1. Do pole **Popis** zadejte název prostředí.

1. V poli **cesta k předponě** zadejte nebo vyhledejte (pomocí **...**) cestu k interpretu.

1. Pokud Visual Studio zjistí interpret Pythonu na daném místě (například cestu zobrazenou níže pro prostředí conda), povolí příkaz **automaticky rozpoznat** . Když vyberete **Automatické rozpoznávání** , dokončí zbývající pole. Tato pole můžete také vyplnit ručně.

    ![Povolení příkazu pro automatické rozpoznávání](media/environments/environments-custom-2.png)

    ![Dokončení polí prostředí po použití automatické detekce](media/environments/environments-custom-3.png)

1. Jakmile pole obsahují požadované hodnoty, klikněte na tlačítko **použít** a uložte konfiguraci. Prostředí teď můžete používat v sadě Visual Studio jako jiné.

1. Pokud potřebujete odebrat ručně identifikované prostředí, vyberte na kartě **Konfigurovat** příkaz **Odebrat** . Automaticky zjištěná prostředí tuto možnost neposkytují. Další informace najdete v tématu [Configure a Tab](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Vyberte **Přidat prostředí...** v okně **prostředí Pythonu** (nebo na panelu nástrojů Python), ve kterém se otevře dialogové okno **Přidat prostředí** . V tomto dialogovém okně vyberte kartu **existující prostředí** :

    ![Existující karta prostředí v dialogovém okně Přidat prostředí](media/environments/environments-custom-1-2019.png)

1. Vyberte rozevírací seznam **prostředí** a pak vyberte **vlastní**:

    ![Vlastní možnost prostředí v dialogovém okně Přidat prostředí](media/environments/environments-custom-2-2019.png)

1. V zadaných polích v dialogovém okně zadejte nebo vyhledejte (pomocí **...**) cestu k interpretovi v **cestě předpony**, která vyplní většinu ostatních polí. Po kontrole těchto hodnot a úprav v případě potřeby vyberte **Přidat**.

    ![Pole pro zadání podrobností pro vlastní možnost prostředí v dialogovém okně Přidat prostředí](media/environments/environments-custom-3-2019.png)

1. Podrobnosti o prostředí můžete kdykoli zkontrolovat a upravit v okně **prostředí Pythonu** . V tomto okně vyberte prostředí a pak vyberte kartu **Konfigurovat** . Po provedení změn vyberte příkaz **použít** . Prostředí můžete odebrat také pomocí příkazu **Remove** (není k dispozici pro automaticky zjištěná prostředí). Další informace najdete v tématu [Configure a Tab](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Oprava nebo odstranění neplatných prostředí

Pokud aplikace Visual Studio najde položky registru pro prostředí, ale cesta k interpretovi je neplatná, pak okno **prostředí Pythonu** zobrazí název se přeškrtnutím písma:

::: moniker range="vs-2017"
![Okno prostředí Pythonu zobrazující neplatné prostředí](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Okno prostředí Pythonu zobrazující neplatné prostředí](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Chcete-li opravit prostředí, které chcete zachovat, zkuste použít proces **opravy** instalačního programu. Instalační programy pro standard Python 3. x, například obsahují tuto možnost.

Chcete-li opravit prostředí, které nemá možnost opravit, nebo odebrat neplatné prostředí, použijte následující postup pro úpravu registru přímo. Když provedete změny v registru, Visual Studio automaticky aktualizuje okno **prostředí Pythonu** .

1. Spusťte *regedit.exe*.
1. Přejděte na **HKEY_LOCAL_MACHINE\SOFTWARE\Python** nebo **HKEY_CURRENT_USER\SOFTWARE\Python**. Pro Ironpythonu hledejte místo toho **ironpythonu** .
1. Rozbalte uzel, který odpovídá distribuci, jako je **Python Core** pro CPython nebo **ContinuumAnalytics** pro Anaconda. V případě Ironpythonu rozbalte uzel číslo verze.
1. Zkontrolujte hodnoty v uzlu **InstallPath** :

    ![Položky registru pro typickou instalaci CPython](media/environments/environments-registry-entries.png)

    - Pokud prostředí stále v počítači existuje, změňte hodnotu **ExecutablePath** na správné umístění. V případě potřeby opravte také **(výchozí)** a **WindowedExecutablePath** hodnoty.
    - Pokud prostředí již v počítači neexistuje a chcete ho odebrat z okna **prostředí Pythonu** , odstraňte nadřazený uzel **InstallPath**, například **3,6** na obrázku výše.
    - Neplatné nastavení v **HKEY_CURRENT_USER\SOFTWARE\Python** přepsat nastavení v **HKEY_LOCAL_MACHINE\SOFTWARE\Python**

## <a name="see-also"></a>Viz také

- [Instalace interpretů Pythonu](installing-python-interpreters.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Použít requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
- [Referenční dokumentace okna prostředí Pythonu](python-environments-window-tab-reference.md)