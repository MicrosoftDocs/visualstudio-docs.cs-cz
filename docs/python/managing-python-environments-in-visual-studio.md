---
title: Správa prostředí Pythonu a interprety
description: Použijte okno prostředí Pythonu ke správě globální, virtuální a prostředí conda, instalace interpretů Pythonu a balíčky a přiřazení prostředí do projektů sady Visual Studio.
ms.date: 12/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 887776b3a3f1275b97b2abee26c4613d8aad39fc
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063206"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak vytvořit a spravovat prostředí Pythonu v sadě Visual Studio

Python *prostředí* je kontext, ve kterém spuštění kódu Pythonu a zahrnuje globální, virtuální a prostředí conda. Prostředí se skládá z interpretu, knihovny (obvykle standardní knihovny Pythonu) a sada nainstalované balíčky. Společně tyto komponenty určují, syntaxi a jazykové konstrukce jsou platné, spouštění jaký operační systém funkce můžete přistupovat a které balíčky, můžete použít.

V sadě Visual Studio na Windows, můžete použít **prostředí Pythonu** okna, jak je popsáno v tomto článku se ke správě prostředí a vyberte jednu z nich jako výchozí pro nové projekty. Další aspekty prostředí se nacházejí v následujících článcích:

- U každého projektu, můžete [vyberte konkrétní prostředí](selecting-a-python-environment-for-a-project.md) místo použití výchozí.

- Podrobnosti o vytváření a používání virtuální prostředí pro projekty v Pythonu najdete v tématu [použít virtuální prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Pokud chcete nainstalovat balíčky v prostředí, podívejte se na [balíčky kartě odkaz](python-environments-window-tab-reference.md#packages-tab).

- Instalaci jiný překladač Pythonu najdete v tématu [interpretů Pythonu nainstalujte](installing-python-interpreters.md). Obecně platí, pokud stáhněte a spusťte instalační program pro hlavní linii distribuci jazyka Python, sada Visual Studio zjistí, že nové instalace a prostředí se zobrazí v **prostředí Pythonu** okno a můžete ho vybrat pro projekty.

Pokud pro Python v sadě Visual Studio začínáte, následující články poskytují také z obecné na pozadí:

- [Práce s využitím Pythonu v sadě Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalace podpory Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md)

> [!Note]
> Nelze spravovat prostředí pro kód Python, která je otevřena pouze jako složky pomocí **souboru** > **otevřít** > **složky** příkazu. Místo toho [vytvoření projektu Pythonu z existujícího kódu](quickstart-01-python-in-visual-studio-project-from-existing-code.md) mohli využívat funkce prostředí sady Visual Studio.

## <a name="the-python-environments-window"></a>Okno prostředí Pythonu

*(Na snímcích obrazovky uvedené v této části představují Visual Studio 15.8. Může se zobrazit různé uživatelské rozhraní v závislosti na vaší verzi sady Visual Studio.)*

V prostředí, která sadě Visual Studio ví o jsou zobrazeny v **prostředí Pythonu** okna. Otevřete okno, použijte jednu z následujících metod:

- Vyberte **zobrazení** > **ostatní Windows** > **prostředí Pythonu** příkazu nabídky.
- Klikněte pravým tlačítkem myši **prostředí Pythonu** uzel projektu v **Průzkumníka řešení** a vyberte **zobrazit všechna prostředí Pythonu**:

    ![Zobrazit všechna prostředí příkazu v Průzkumníku řešení](media/environments-view-all.png)

V obou případech **prostředí Pythonu** okna se zobrazí vedle **Průzkumníka řešení**:

![Okno prostředí Pythonu](media/environments-default-view.png)

Visual Studio vyhledá nainstalovaných globální prostředí pomocí registru (následující [období 514](https://www.python.org/dev/peps/pep-0514/)), společně s virtuálními prostředími, která a prostředí conda (naleznete v tématu [typy prostředí](#types-of-environments)). Pokud nevidíte očekávanému prostředí v seznamu, přečtěte si téma [ručně identifikovat existující prostředí](#manually-identify-an-existing-environment).

Když v seznamu vyberte prostředí, sada Visual Studio zobrazí na různých vlastností a příkazy pro toto prostředí **přehled** kartu. Například je vidět na obrázku výše, je umístění na překladač *C:\Python36-32*. Čtyř příkazů v dolní části **přehled** kartu každý otevřete příkazový řádek s překladač systémem. Další informace najdete v tématu [kartu odkaz na okno prostředí Pythonu – přehled](python-environments-window-tab-reference.md#overview-tab).

Přepnout na různých záložkách například pomocí rozevíracího seznamu pod seznamem prostředí **balíčky**, a **IntelliSense**. Tyto karty jsou také popsány v [odkaz na kartě okno prostředí Pythonu](python-environments-window-tab-reference.md).

Výběr prostředí se nezmění jejich vztah na všechny projekty. Výchozího prostředí se zobrazí v tučné písmo v seznamu, je ten, který sada Visual Studio používá pro všechny nové projekty. Pokud chcete použít jiné prostředí pomocí nových projektů, použijte **nastavit výchozí prostředí pro nové projekty** příkazu. V rámci projektu můžete vždy vyberte konkrétní prostředí. Další informace najdete v tématu [vyberte prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

Vpravo od každé uvedené prostředí je ovládací prvek, který se otevře **interaktivní** okna pro toto prostředí. (Visual Studio 2017 15.5 a dřívějších verzí jiný ovládací prvek zobrazí se aktualizuje databáze technologie IntelliSense pro příslušné prostředí. Zobrazit [odkaz na kartě okno prostředí](python-environments-window-tab-reference.md#intellisense-tab) podrobnosti o databázi.)

> [!Tip]
> Po rozbalení **prostředí Pythonu** okno dost široké, získat kompletnější pohled prostředí, které může být pro vás být vhodnější pro práci s.
>
> ![Okno prostředí Pythonu rozšířené zobrazení](media/environments-expanded-view.png)

> [!Note]
> I když Visual Studio respektuje možnost balíčků systému lokality, neposkytuje způsob, jak změnit ho z Visual Studia.

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) na prostředí Pythonu v sadě Visual Studio (2 miliony 35s).|

### <a name="what-if-no-environments-appear"></a>Co když se nezobrazí žádná prostředí?

Pokud se nezobrazí žádná prostředí, znamená to, že Visual Studio se nepodařilo zjistit všechny instalace Pythonu ve standardním umístění. Například možná máte nainstalované Visual Studio 2017, ale vymazat všechny možnosti interpret v možnostech instalačního programu pro úlohu Pythonu. Podobně může mít nainstalované Visual Studio 2015 nebo starší, ale nenainstalovala interpretu ručně (viz [interpretů Pythonu nainstalujte](installing-python-interpreters.md)).

Pokud znáte mají překladač Pythonu ve vašem počítači, ale Visual Studio (všechny verze) není rozpoznat je a pak použít **+ vlastní** příkaz a zadejte jeho umístění ručně. Viz následující část [ručně identifikovat existující prostředí](#manually-identify-an-existing-environment).

> [!Tip]
> Sada Visual Studio zjistí aktualizace existující interpret, jako je například upgrade Python 2.7.11 k 2.7.14 pomocí instalačních programů z python.org. Během procesu instalace starší prostředí dané zařízení zmizí z **prostředí Pythonu** seznamu předtím, než aktualizace se zobrazí na jeho místo.
>
> Pokud přesunete ručně interpretu a její prostředí pomocí systému souborů, ale Visual Studio nepoznáte nové umístění. Další informace najdete v tématu [přesunout interpretu](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Typy prostředí

Visual Studio můžete pracovat s globální, virtuální a prostředí conda.

#### <a name="global-environments"></a>Globální prostředí

Každé instalaci Pythonu (například, použije se Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 atd., naleznete v tématu [interpretů Pythonu nainstalujte](installing-python-interpreters.md)) udržuje svůj vlastní *globálního prostředí*. Každé prostředí se skládá z konkrétní interpret Pythonu, jeho standardní knihovny, sadu předem nainstalované balíčky a další balíčky, které nainstalujete, když se aktivuje toto prostředí. Instalaci balíčku do globálního prostředí je k dispozici pro všechny projekty pomocí daného prostředí. Pokud se prostředí nachází v chráněné části systému souborů (v rámci *c:\program files*, například), pak instalace balíčků vyžaduje oprávnění správce.

Globální prostředí jsou k dispozici pro všechny projekty v počítači. V sadě Visual Studio vyberte jednoho globálního prostředí jako výchozí, který se používá pro všechny projekty, pokud zvolíte jiný pro projekt. Další informace najdete v tématu [vyberte prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Virtuální prostředí

I když se práce v globálním prostředí je snadný způsob, jak začít pracovat, daného prostředí bude v průběhu času zaplní mnoho různých balíčcích, které jste nainstalovali pro různé projekty. Takové nepořádku ztěžuje důkladně otestovat aplikaci proti konkrétní sadu balíčků pomocí známé verze, což je přesně typ prostředí, ve kterém byste nastavili na server sestavení nebo webového serveru. Je v konfliktu může dojít, když dva projekty vyžadují, aby se nekompatibilní balíčky nebo různými verzemi stejného balíčku.

Z tohoto důvodu vývojáři často vytvářet *virtuální prostředí* pro projekt. Virtuální prostředí již není podsložkou projekt, který obsahuje kopii konkrétní překladač. Při aktivaci virtuální prostředí jsou nainstalovány všechny balíčky, které můžete nainstalovat pouze v podsložce daného prostředí. Když pak spustíte program v Pythonu v tomto prostředí, víte, že je spuštěn s jenom konkrétní balíčky.

Visual Studio poskytuje přímou podporu pro vytvoření virtuálního prostředí pro projekt. Například, pokud otevřete projekt, který obsahuje *souboru requirements.txt*, nebo vytvořte projekt ze šablony, která obsahuje tento soubor, Visual Studio vás vyzve, abyste automaticky vytvořit virtuální prostředí a nainstalujte tyto závislosti .

Kdykoli v otevřeném projektu můžete vytvořit nové virtuální prostředí. V **Průzkumníka řešení**, rozbalte uzel projektu, klikněte pravým tlačítkem na **prostředí Pythonu**a vyberte "Přidat virtuální prostředí." Další informace najdete v tématu [vytvořit virtuální prostředí](selecting-a-python-environment-for-a-project.md#create-a-virtual-environment).

Visual Studio také poskytuje příkazu, který bude generovat *souboru requirements.txt* soubor ve virtuálním prostředí, což usnadňuje znovu vytvořte prostředí v jiných počítačích. Další informace najdete v tématu [použít virtuální prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Prostředí Conda

Prostředí conda je vytvořené využitím `conda` nástroje, nebo pomocí integrovaného systému conda management v sadě Visual Studio 2017 verze 15.7 nebo novější. (Vyžaduje Anaconda nebo Miniconda; Anaconda je k dispozici prostřednictvím instalačního programu sady Visual Studio, naleznete v tématu [instalace – Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017).)

1. Vyberte **+ vytvořit prostředí conda** v **prostředí Pythonu** okno, které se otevře **vytvořit nové prostředí conda** kartu:

    ![Vytvoření karty pro nové prostředí conda](media/environments-conda-1.png)

1. Zadejte název prostředí **název** vyberte základní interpret Pythonu v **Python** pole a vyberte **vytvořit**.

1. **Výstup** okno zobrazuje průběh pro nové prostředí s několika pokyny příkazového řádku po dokončení vytváření:

    ![Po úspěšném vytvoření prostředí conda](media/environments-conda-2.png)

1. V sadě Visual Studio, můžete aktivovat prostředí conda pro projekt, jako byste jiné prostředí, jak je popsáno na [vyberte prostředí pro projekt](selecting-a-python-environment-for-a-project.md).

1. Chcete-li instalovat balíčky v prostředí, použijte [balíčky kartu](python-environments-window-tab-reference.md#packages-tab).

> [!Note]
> Chcete-li dosáhnout optimálních výsledků při prostředí conda, použijte conda 4.4.8 nebo novější (verze systému conda se liší od Anaconda verze). Anaconda 5.1 nainstalujte z instalačního programu sady Visual Studio 2017.

Verze systému conda, kde jsou uložené prostředí conda, a další informace zobrazíte spuštěním `conda info` na příkazovém řádku programu Anaconda (to znamená, že příkazový řádek se Anaconda v cestě):

```cli
conda info
```

Složky prostředí conda vypadat následovně:

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Protože prostředí conda nejsou uložena s projektem, působí podobně do globálního prostředí. Například instalace nového balíčku do prostředí conda zpřístupňuje tohoto balíčku do všech projektů pomocí daného prostředí.

Pro Visual Studio 2017 verze 15.6 a starší, můžete použít prostředí conda tak, že je označíte ručně, jak je popsáno v části [ručně identifikovat existující prostředí](#manually-identify-an-existing-environment).

Visual Studio 2017 verze 15.7 nebo novější prostředí conda automaticky zjistí a zobrazí je v **prostředí Pythonu** okna, jak je popsáno v další části.

## <a name="manually-identify-an-existing-environment"></a>Ručně identifikovat existující prostředí

Prostředí, ve kterém je nainstalovaný v nestandardním umístění (včetně prostředí conda v sadě Visual Studio 2017 verze 15.6 a starší) pomocí následujících kroků:

1. Vyberte **+ vlastní** v **prostředí Pythonu** okno, které se otevře **konfigurovat** kartu:

    ![Výchozí zobrazení pro nový vlastní prostředí](media/environments-custom-1.png)

1. Zadejte název prostředí **popis** pole.

1. Zadejte nebo vyhledejte (pomocí **...** ) na cestu interpretu v **Předponovou cestu** pole.

1. Pokud sada Visual Studio zjistí interpret Pythonu v tomto umístění (jako je například cesta pro prostředí conda najdete níž), umožňuje **automaticky rozpoznat** příkazu. Výběr **automaticky rozpoznat** dokončí zbývající pole. Tato pole lze dokončit také ručně.

    ![Povolení příkazu automaticky rozpoznat](media/environments-custom-2.png)

    ![Dokončení pole prostředí po dokončení automaticky rozpoznat](media/environments-custom-3.png)

1. Jakmile pole obsahují hodnoty požadujete, vyberte **použít** uložte konfiguraci. Teď můžete použít prostředí jako u všech ostatních v sadě Visual Studio.

1. Pokud budete muset odebrat ručně zjištěné prostředí, vyberte **odebrat** příkaz **konfigurovat** kartu. Tato možnost se neposkytuje automaticky rozpoznané prostředí. Další informace najdete v tématu [kartu konfigurovat](python-environments-window-tab-reference.md#configure-tab).

## <a name="fix-or-delete-invalid-environments"></a>Opravte nebo odstraňte neplatný prostředí

Pokud sada Visual Studio najde položky registru pro prostředí, ale cesta k interpretu je neplatný, pak bude **prostředí Pythonu** okno zobrazuje název s přeškrtnuté písmo:

![Okno prostředí Pythonu neplatný prostředí](media/environments-invalid-entry.png)

Chcete-li chcete zachovat prostředí, nejprve zkuste použít jeho instalační program **opravit** procesu. Instalační programy pro standardní Python 3.x, například zahrnout tuto možnost.

Chcete-li prostředí, které nemá možnost opravit nebo odebrat neplatný prostředí, použijte následující kroky úprava registr přímo. Visual Studio automaticky aktualizuje **prostředí Pythonu** okno když provedete změny do registru.

1. Spustit *regedit.exe*.
1. Přejděte do **HKEY_LOCAL_MACHINE\SOFTWARE\Python** u 32-bit interpretů nebo **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** pro interprety 64-bit. Pro IronPython, vyhledejte **IronPython** místo.
1. Rozbalte uzel, který odpovídá distribuce, jako například **PythonCore** pro CPython nebo **ContinuumAnalytics** pro Anaconda. Pro IronPython rozbalte uzel číslo verze.
1. Zkontrolovat hodnoty v rámci **InstallPath** uzlu:

    ![Položky registru pro typické instalace Cpythonu](media/environments-registry-entries.png)

    - Pokud prostředí stále existuje ve vašem počítači, změňte hodnotu vlastnosti **ExecutablePath** do správného umístění. Také opravte **(výchozí)** a **WindowedExecutablePath** hodnoty podle potřeby.
    - Pokud prostředí už existuje v počítači a chcete ho odebrat **prostředí Pythonu** okně odstranit nadřazený uzel **InstallPath**, jako například **3.6** na obrázku výše.

## <a name="see-also"></a>Viz také:

- [Instalace interpretů Pythonu](installing-python-interpreters.md)
- [Výběr interpretu pro projekt](selecting-a-python-environment-for-a-project.md)
- [Používání souboru requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
- [Odkaz na okno prostředí Pythonu](python-environments-window-tab-reference.md)
