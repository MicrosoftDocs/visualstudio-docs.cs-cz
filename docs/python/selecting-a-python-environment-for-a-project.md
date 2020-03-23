---
title: Výběr interpreta Pythonu a prostředí pro projekt
description: Můžete konkrétně vybrat prostředí Pythonu, včetně Anaconda a virtuální prostředí, chcete-li použít pro konkrétní projekt.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 34ceb2ec7cc923f6642977cf4c70fbfae07bf523
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302726"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Jak vybrat prostředí Pythonu pro projekt

Veškerý kód v projektu Pythonu běží v kontextu konkrétního prostředí, jako je například globální prostředí Pythonu, prostředí Anaconda, virtuální prostředí nebo prostředí conda. Visual Studio také používá toto prostředí pro ladění, import a dokončení členů, kontrolu syntaxe a všechny další úkoly, které vyžadují jazykové služby, které jsou specifické pro verzi Pythonu a sadu nainstalovaných balíčků.

Všechny nové projekty Pythonu v sadě Visual Studio jsou zpočátku nakonfigurovány tak, aby používaly výchozí globální prostředí, které se zobrazí v uzlu **Prostředí Pythonu** v **Průzkumníku řešení**:

![Globální výchozí prostředí Pythonu zobrazené v Průzkumníku řešení](media/environments/environments-project.png)

::: moniker range="vs-2017"
Chcete-li změnit prostředí projektu, klepněte pravým tlačítkem myši na uzel **Prostředí Pythonu** a vyberte příkaz **Přidat nebo odebrat prostředí Pythonu**. Ze zobrazeného seznamu, který zahrnuje globální, virtuální a conda prostředí, vyberte všechny, které chcete zobrazit v uzlu **Prostředí Pythonu:**

![Dialogové okno Přidat nebo odebrat prostředí Pythonu](media/environments/environments-add-remove.png)

Jakmile vyberete **OK**, všechna vybraná prostředí se zobrazí v uzlu **Prostředí Pythonu.** Aktuálně aktivované prostředí se zobrazí tučně:

![Více prostředí Pythonu zobrazených v Průzkumníku řešení](media/environments/environments-project-multiple.png)

Chcete-li rychle aktivovat jiné prostředí, klepněte pravým tlačítkem myši na tento název prostředí a vyberte příkaz **Aktivovat prostředí**. Vaše volba je uložena s projektem a toto prostředí je aktivováno při každém otevření projektu v budoucnu. Pokud vymažete všechny možnosti v dialogovém okně **Přidat nebo odebrat prostředí Pythonu,** Visual Studio aktivuje globální výchozí prostředí.

Místní nabídka v uzlu **Prostředí Pythonu** také poskytuje další příkazy:

| Příkaz | Popis |
| --- | --- |
| **Přidat virtuální prostředí** | Zahájí proces vytváření nového virtuálního prostředí v projektu. Viz [Vytvoření virtuálního prostředí](#create-a-virtual-environment). |
| **Přidat existující virtuální prostředí** | Zobrazí výzvu k výběru složky obsahující virtuální prostředí a přidá ji do seznamu v části **Prostředí Pythonu**, ale neaktivuje ji. Viz [Aktivace existujícího virtuálního prostředí](#activate-an-existing-virtual-environment). |
| **Vytvořit prostředí Conda** | Přepne do *okna* **Prostředí Pythonu,** ve kterém zadáte název prostředí a zadáte jeho základní interpret. Viz [Prostředí Conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Chcete-li změnit prostředí projektu, klepněte pravým tlačítkem myši na uzel **Prostředí Pythonu** a vyberte **přidat prostředí**nebo vyberte přidat **prostředí** z rozbalovacího okna prostředí na panelu nástrojů Pythonu.

V dialogovém okně **Přidat prostředí** vyberte kartu **Existující prostředí** a v rozevíracím seznamu **Prostředí** vyberte nové prostředí:

![Výběr prostředí projektu v dialogovém okně Přidat prostředí](media/environments/environments-project-2019.png)

Pokud jste již do projektu přidali jiné prostředí než globální výchozí prostředí, bude pravděpodobně nutné aktivovat nově přidané prostředí. Klepněte pravým tlačítkem myši na toto prostředí v uzlu **Prostředí Pythonu** a vyberte **možnost Aktivovat prostředí**. Chcete-li z projektu odebrat prostředí, vyberte **odebrat**.

![Aktivace a odebrání projektového prostředí](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Použití virtuálních prostředí

Virtuální prostředí je jedinečná kombinace konkrétního interpretu Pythonu a konkrétní sady knihoven, která se liší od jiných globálních prostředí a prostředí conda. Virtuální prostředí je specifické pro projekt a je udržováno ve složce projektu. Tato složka obsahuje nainstalované knihovny prostředí spolu se souborem *pyvenv.cfg,* který určuje cestu k *základnímu interpretu* prostředí jinde v systému souborů. (To znamená, že virtuální prostředí neobsahuje kopii interpreta, pouze odkaz na něj.)

Výhodou použití virtuálního prostředí je, že při vývoji projektu v průběhu času virtuální prostředí vždy odráží přesné závislosti projektu. (Sdílené globální prostředí na druhé straně obsahuje libovolný počet knihoven, ať už je používáte v projektu nebo ne.) Potom můžete snadno vytvořit soubor *requirements.txt* z virtuálního prostředí, který se pak používá k přeinstalaci těchto závislostí na jiném vývojovém nebo produkčním počítači. Další informace naleznete v [tématu Správa požadovaných balíčků pomocí souboru requirements.txt](managing-required-packages-with-requirements-txt.md).

Při otevření projektu v sadě Visual Studio, který obsahuje soubor *requirements.txt,* Visual Studio automaticky poskytuje možnost znovu vytvořit virtuální prostředí. V počítačích, kde visual studio není `pip install -r requirements.txt` nainstalován, můžete použít k obnovení balíčků.

Vzhledem k tomu, že virtuální prostředí obsahuje pevně zakódolou cestu k základnímu interpretu a protože můžete znovu vytvořit prostředí pomocí *souboru requirements.txt*, obvykle vynechejte celou složku virtuálního prostředí ze správy zdrojového kódu.

V následujících částech je vysvětleno, jak aktivovat existující virtuální prostředí v projektu a jak vytvořit nové virtuální prostředí.

V sadě Visual Studio lze aktivovat virtuální prostředí pro projekt jako každý jiný prostřednictvím uzlu **Prostředí Pythonu** v **Průzkumníku řešení**.

Jakmile je virtuální prostředí přidáno do projektu, zobrazí se v okně **Prostředí Pythonu.** Poté jej můžete aktivovat jako jakékoli jiné prostředí a spravovat jeho balíčky.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Vytvoření virtuálního prostředí

Nové virtuální prostředí můžete vytvořit přímo v sadě Visual Studio následujícím způsobem:

1. Klepněte pravým tlačítkem myši na **položku Prostředí Pythonu** v **Průzkumníku řešení** a vyberte **přidat virtuální prostředí**, které vyvolá následující dialogové okno:

    ![Vytvoření virtuálního prostředí](media/environments/environments-add-virtual-1.png)

1. V poli **Umístění virtuálního prostředí** zadejte cestu pro virtuální prostředí. Pokud zadáte pouze název, virtuální prostředí se vytvoří v rámci aktuálního projektu v podsložce s tímto názvem.

1. Vyberte prostředí jako základní interpret a vyberte **vytvořit**. Visual Studio zobrazí indikátor průběhu při konfiguraci prostředí a stáhne všechny potřebné balíčky. Po dokončení se virtuální prostředí zobrazí v okně **Prostředí Pythonu** pro obsahující projekt.

1. Virtuální prostředí není ve výchozím nastavení aktivováno. Chcete-li jej aktivovat pro projekt, klepněte na něj pravým tlačítkem myši a vyberte **příkaz Aktivovat prostředí**.

> [!Note]
> Pokud cesta k umístění identifikuje existující virtuální prostředí, visual studio automaticky detekuje základní interpret (pomocí souboru *orig-prefix.txt* v adresáři *lib* prostředí) a změní tlačítko **Vytvořit** na **Přidat**.
>
> Pokud při přidávání virtuálního prostředí existuje soubor *requirements.txt,* zobrazí se v dialogovém okně **Přidat virtuální prostředí** možnost automatické instalace balíčků, což usnadňuje opětovné vytvoření prostředí v jiném počítači:
>
> ![Vytvoření virtuálního prostředí s souborem requirements.txt](media/environments/environments-requirements-txt.png)
>
> Ať tak či onak, výsledek je stejný, jako kdybyste použili **příkaz Přidat existující virtuální prostředí.**

### <a name="activate-an-existing-virtual-environment"></a>Aktivace existujícího virtuálního prostředí

Pokud jste již vytvořili virtuální prostředí jinde, můžete ho aktivovat pro projekt následujícím způsobem:

1. Klepněte v **Průzkumníku řešení** pravým tlačítkem myši na **prostředí Pythonu** a vyberte **přidat existující virtuální prostředí**.

1. V zobrazeném dialogovém okně **Procházet** přejděte do složky obsahující virtuální prostředí a vyberte ji **OK**. Pokud Visual Studio zjistí soubor *requirements.txt* v tomto prostředí, zeptá se, zda chcete nainstalovat tyto balíčky.

1. Po několika okamžicích se virtuální prostředí zobrazí pod uzětem **Prostředí Pythonu** v **Průzkumníku řešení**. Virtuální prostředí není ve výchozím nastavení aktivováno, takže na něj klepněte pravým tlačítkem myši a vyberte **možnost Aktivovat prostředí**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Vytvoření virtuálního prostředí

Nové virtuální prostředí můžete vytvořit přímo v sadě Visual Studio následujícím způsobem:

1. Klikněte pravým tlačítkem myši na **prostředí Pythonu** v **Průzkumníkovi řešení** a vyberte **Přidat prostředí**nebo vyberte Přidat **prostředí** z rozevíracího seznamu prostředí na panelu nástrojů Pythonu. V zobrazeném dialogovém **okně Přidat prostředí** vyberte kartu Virtuální **prostředí:**

    ![Karta Virtuální prostředí v dialogovém okně Přidat prostředí](media/environments/environments-add-virtual-1-2019.png)

1. Zadejte název virtuálního prostředí, vyberte základní interpret a ověřte jeho umístění. V části **Instalovat balíčky ze souboru**poskytněte v případě potřeby cestu k souboru *requirements.txt.*

1. Prohlédněte si další možnosti v dialogovém okně:

    | Možnost | Popis |
    | --- | --- |
    | Nastavit jako aktuální prostředí | Aktivuje nové prostředí ve vybraném projektu po vytvoření prostředí. |
    | Nastavit jako výchozí prostředí pro nové projekty | Automaticky nastaví a aktivuje virtuální prostředí ve všech nových projektech vytvořených v sadě Visual Studio. Při použití této možnosti by mělo být virtuální prostředí umístěno v umístění mimo konkrétní projekt.  |
    | Zobrazení v okně Prostředí Pythonu | Určuje, zda se má po vytvoření prostředí otevřít okno **Prostředí Pythonu.** |
    | Zpřístupnit toto prostředí globálně | Určuje, zda virtuální prostředí funguje také jako globální prostředí. Při použití této možnosti by mělo být virtuální prostředí umístěno v umístění mimo konkrétní projekt. |

1. Vyberte **Vytvořit,** chcete-li dokončit virtuální prostředí. Visual Studio zobrazí indikátor průběhu při konfiguraci prostředí a stáhne všechny potřebné balíčky. Po dokončení se aktivuje virtuální prostředí a zobrazí se v uzlu **Prostředí Pythonu** v **Průzkumníku řešení** a v okně **Prostředí Pythonu** pro obsahující projekt.

### <a name="activate-an-existing-virtual-environment"></a>Aktivace existujícího virtuálního prostředí

Pokud jste již vytvořili virtuální prostředí jinde, můžete ho aktivovat pro projekt následujícím způsobem:

1. Klepněte v **Průzkumníku řešení** pravým tlačítkem myši na **položku Prostředí Pythonu** a vyberte přidat **prostředí**.

1. V zobrazeném dialogovém okně **Procházet** přejděte do složky obsahující virtuální prostředí a vyberte ji **OK**. Pokud Visual Studio zjistí soubor *requirements.txt* v tomto prostředí, zeptá se, zda chcete nainstalovat tyto balíčky.

1. Po několika okamžicích se virtuální prostředí zobrazí pod uzětem **Prostředí Pythonu** v **Průzkumníku řešení**. Virtuální prostředí není ve výchozím nastavení aktivováno, takže na něj klepněte pravým tlačítkem myši a vyberte **možnost Aktivovat prostředí**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Odebrání virtuálního prostředí

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na virtuální prostředí a vyberte **příkaz Odebrat**.

1. Visual Studio se zeptá, zda chcete odebrat nebo odstranit virtuální prostředí. Výběrem **možnosti Odebrat** jej projekt neznepřístupní, ale ponechá jej v systému souborů. Výběrem **možnosti Odstranit** odeberete prostředí z projektu a odstraníte ho ze systému souborů. Základní tlumočník není ovlivněn.

## <a name="view-installed-packages"></a>Zobrazit nainstalované balíčky

V Průzkumníku řešení rozbalte uzel libovolného konkrétního prostředí a rychle zobrazit balíčky, které jsou nainstalovány v tomto prostředí (což znamená, že tyto balíčky můžete importovat a používat v kódu, když je prostředí aktivní):

![Balíčky Pythonu pro prostředí v Průzkumníku řešení](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Chcete-li nainstalovat nové balíčky, klepněte pravým tlačítkem myši na prostředí a vyberte **možnost Nainstalovat balíček Pythonu** a přepněte na příslušnou kartu **Balíčky** v okně **Prostředí Pythonu.** Zadejte hledaný termín (obvykle název balíčku) a Visual Studio zobrazí odpovídající balíčky.
::: moniker-end
::: moniker range=">=vs-2019"
Chcete-li nainstalovat nové balíčky, klepněte pravým tlačítkem myši na prostředí a vyberte **spravovat balíčky Pythonu** (nebo pomocí tlačítka balíčku na panelu nástrojů Pythonu) přepněte na příslušnou kartu **Balíčky** v okně **Prostředí Pythonu.** Na kartě **Balíčky** zadejte hledaný výraz (obvykle název balíčku) a Visual Studio zobrazí odpovídající balíčky.
::: moniker-end

V rámci sady Visual Studio se balíčky (a závislosti) pro většinu prostředí stahují z [indexu balíčků Pythonu (PyPI),](https://pypi.org)kde můžete také vyhledat dostupné balíčky. Stavový řádek visual studia a výstupní okno zobrazují informace o instalaci. Chcete-li balíček odinstalovat, klepněte na něj pravým tlačítkem myši a vyberte příkaz **Odebrat**.

Správce balíčků conda `https://repo.continuum.io/pkgs/` obvykle používá jako výchozí kanál, ale jiné kanály jsou k dispozici. Další informace naleznete v [tématu Správa kanálů](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.conda.io).

Uvědomte si, že zobrazené položky nemusí být vždy přesné a instalace a odinstalace nemusí být spolehlivé nebo dostupné. Visual Studio používá správce balíčků pip, pokud je k dispozici, a v případě potřeby jej stáhne a nainstaluje. Visual Studio můžete také použít správce balíčků easy_install. Zobrazí se `pip` `easy_install` také balíčky nainstalované pomocí příkazového řádku nebo z příkazového řádku.

Všimněte si také, že Visual `conda` Studio v současné době nepodporuje použití k instalaci balíčků do prostředí conda. Místo `conda` toho použijte z příkazového řádku.

> [!Tip]
> Běžná situace, kdy pip nepodaří nainstalovat balíček je, když balíček obsahuje zdrojový kód pro nativní součásti v * \*souborech .pyd.* Bez nainstalované požadované verze sady Visual Studio nemůže pip tyto součásti zkompilovat. Chybová zpráva zobrazená v této situaci je **chyba: Nelze najít vcvarsall.bat**. `easy_install`je často schopen stáhnout předkompilované binární soubory a můžete si stáhnout vhodný [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266)kompilátor pro starší verze Pythonu z . Další podrobnosti naleznete v [tématu Jak se vypořádat s bolestí "nelze najít vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) na blogu týmu nástrojů Pythonu.

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu v sadě Visual Studio](managing-python-environments-in-visual-studio.md)
- [Použití souboru requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
- [Odkaz na okno prostředí Pythonu](python-environments-window-tab-reference.md)
