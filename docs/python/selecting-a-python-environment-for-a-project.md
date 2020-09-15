---
title: Výběr prostředí Pythonu pro projekt
description: Konkrétně můžete vybrat prostředí Pythonu, včetně Anaconda a virtuálních prostředí, která se použijí pro konkrétní projekt.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 46b0a8005ea76445a1d6205c8635963dbaedd0d4
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2020
ms.locfileid: "90097031"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Jak vybrat prostředí Pythonu pro projekt

Veškerý kód v projektu Python běží v kontextu konkrétního prostředí, jako je globální prostředí Pythonu, prostředí Anaconda, virtuální prostředí nebo prostředí conda. Sada Visual Studio také používá toto prostředí pro ladění, dokončování importu a dokončování členů, kontrolu syntaxe a jakékoli další úlohy, které vyžadují jazykové služby specifické pro verzi Pythonu a sadu nainstalovaných balíčků.

Všechny nové projekty v Pythonu v aplikaci Visual Studio jsou zpočátku nakonfigurované tak, aby používaly výchozí globální prostředí, které se zobrazí v uzlu **prostředí Pythonu** v **Průzkumník řešení**:

![Globální výchozí prostředí Pythonu zobrazené v Průzkumník řešení](media/environments/environments-project.png)

::: moniker range="vs-2017"
Pokud chcete změnit prostředí pro projekt, klikněte pravým tlačítkem myši na uzel **prostředí Pythonu** a vyberte **Přidat nebo odebrat prostředí Pythonu**. V zobrazeném seznamu, který zahrnuje globální, virtuální a conda prostředí, vyberte všechny ty, které se mají zobrazit pod uzlem **prostředí Pythonu** :

![Dialog Přidat nebo odebrat prostředí Pythonu](media/environments/environments-add-remove.png)

Jakmile vyberete **OK**, všechna vybraná prostředí se zobrazí v uzlu **prostředí Pythonu** . Aktuálně aktivované prostředí se zobrazuje tučně:

![Několik prostředí Pythonu zobrazených v Průzkumník řešení](media/environments/environments-project-multiple.png)

Pokud chcete rychle aktivovat jiné prostředí, klikněte pravým tlačítkem na název prostředí a vyberte **aktivovat prostředí**. Vaše volba se uloží spolu s projektem a toto prostředí se aktivuje při každém otevření projektu v budoucnu. Pokud zrušíte zaškrtnutí všech možností v dialogu **Přidat nebo odebrat prostředí Pythonu** , Visual Studio aktivuje globální výchozí prostředí.

Kontextová nabídka uzlu **prostředí Pythonu** také nabízí další příkazy:

| Příkaz | Popis |
| --- | --- |
| **Přidat virtuální prostředí** | Zahájí proces vytváření nového virtuálního prostředí v projektu. Viz [Vytvoření virtuálního prostředí](#create-a-virtual-environment). |
| **Přidat existující virtuální prostředí** | Vyzve vás k výběru složky obsahující virtuální prostředí a přidá ji do seznamu v **prostředích Pythonu**, ale neaktivuje ji. Viz [aktivovat existující virtuální prostředí](#activate-an-existing-virtual-environment). |
| **Vytvoření prostředí conda** | Přepne do *okna* **prostředí Pythonu** , ve kterém zadáte název prostředí a určíte jeho základní Interpret. Viz [prostředí conda](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Chcete-li změnit prostředí pro projekt, klikněte pravým tlačítkem myši na uzel **prostředí Python** a vyberte možnost **Přidat prostředí**. Na panelu nástrojů Python můžete také vybrat **Přidat prostředí** z rozevíracího seznamu prostředí.

Jednou v dialogovém okně **Přidat prostředí** vyberte kartu **existující prostředí** a pak v rozevíracím seznamu **prostředí** vyberte nové prostředí:

![Výběr prostředí projektu v dialogovém okně Přidat prostředí](media/environments/environments-project-2019.png)

Pokud jste už přidali jiné prostředí, než je globální výchozí nastavení projektu, možná budete muset aktivovat nově přidané prostředí. Klikněte pravým tlačítkem na toto prostředí v uzlu **prostředí Python** a vyberte **aktivovat prostředí**. Chcete-li odebrat prostředí z projektu, vyberte možnost **Odebrat**.

![Aktivace a odebrání prostředí projektu](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Použití virtuálních prostředí

Virtuální prostředí je jedinečnou kombinací konkrétního interpretu Pythonu a konkrétní sady knihoven, která se liší od ostatních globálních a conda prostředí. Virtuální prostředí je specifické pro projekt a je udržováno ve složce projektu. Tato složka obsahuje nainstalované knihovny pro prostředí spolu se souborem *pyvenv. cfg* , který určuje cestu k *základnímu interpretu* prostředí jinde v systému souborů. (To znamená, že virtuální prostředí neobsahuje kopii překladače, pouze odkaz na něj.)

Výhodou použití virtuálního prostředí je, že když vyvíjíte projekt v průběhu času, virtuální prostředí vždy odráží přesné závislosti projektu. (Sdílené globální prostředí, na druhé straně obsahuje libovolný počet knihoven, ať už je používáte v projektu, nebo ne.) Pak můžete snadno vytvořit soubor *requirements.txt* z virtuálního prostředí, který se pak použije k přeinstalování těchto závislostí na jiném vývojovém nebo produkčním počítači. Další informace najdete v tématu [Správa požadovaných balíčků pomocí requirements.txt](managing-required-packages-with-requirements-txt.md).

Když otevřete projekt v aplikaci Visual Studio, který obsahuje soubor *requirements.txt* , Visual Studio vám automaticky nabídne možnost znovu vytvořit virtuální prostředí. V počítačích, kde není nainstalována aplikace Visual Studio, můžete použít `pip install -r requirements.txt` k obnovení balíčků.

Vzhledem k tomu, že virtuální prostředí obsahuje pevně zakódovanou cestu k základnímu Překladači a protože můžete znovu vytvořit prostředí pomocí *requirements.txt*, obvykle vynecháte celou složku virtuálního prostředí ze správy zdrojového kódu.

Následující části vysvětlují, jak aktivovat existující virtuální prostředí v projektu a jak vytvořit nové virtuální prostředí.

V aplikaci Visual Studio je možné aktivovat virtuální prostředí pro projekt stejně jako v uzlu **prostředí Pythonu** v **Průzkumník řešení**.

Jakmile se do projektu přidá virtuální prostředí, zobrazí se v okně **prostředí Pythonu** . Pak ho můžete aktivovat stejně jako jakékoli jiné prostředí a můžete spravovat jeho balíčky.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Vytvoření virtuálního prostředí

Nové virtuální prostředí můžete vytvořit přímo v aplikaci Visual Studio následujícím způsobem:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **prostředí Pythonu** a vyberte **Přidat virtuální prostředí**. tím se zobrazí následující dialogové okno:

    ![Vytváření virtuálního prostředí](media/environments/environments-add-virtual-1.png)

1. V **umístění pole virtuální prostředí** zadejte cestu k virtuálnímu prostředí. Pokud zadáte pouze název, bude virtuální prostředí vytvořeno v rámci aktuálního projektu v podsložce s tímto názvem.

1. Vyberte prostředí jako základní překladač a vyberte **vytvořit**. Visual Studio zobrazí indikátor průběhu a nakonfiguruje prostředí a stáhne všechny potřebné balíčky. Po dokončení se virtuální prostředí zobrazí v okně **prostředí Pythonu** pro projekt, který ho obsahuje.

1. Virtuální prostředí není ve výchozím nastavení aktivované. Chcete-li aktivovat virtuální prostředí pro projekt, klikněte na něj pravým tlačítkem myši a vyberte **aktivovat prostředí**.

> [!Note]
> Pokud cesta k umístění identifikuje existující virtuální prostředí, Visual Studio automaticky detekuje základní interpret (pomocí *orig-prefix.txt* souboru v adresáři *lib* prostředí) a změní tlačítko **vytvořit** na **Přidat**.
>
> Pokud při přidávání virtuálního prostředí existuje *requirements.txt* soubor, zobrazí se dialogové okno **Přidat virtuální prostředí** , ve kterém se zobrazí možnost automaticky nainstalovat balíčky, což usnadňuje opětovné vytvoření prostředí v jiném počítači:
>
> ![Vytvoření virtuálního prostředí pomocí requirements.txt](media/environments/environments-requirements-txt.png)
>
> V obou případech je výsledek stejný, jako kdybyste použili příkaz **Přidat existující virtuální prostředí** .

### <a name="activate-an-existing-virtual-environment"></a>Aktivovat existující virtuální prostředí

Pokud jste již vytvořili virtuální prostředí jinde, můžete jej aktivovat pro projekt následujícím způsobem:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **prostředí Pythonu** a vyberte **Přidat existující virtuální prostředí**.

1. V zobrazeném dialogovém okně **Procházet** přejděte na složku obsahující virtuální prostředí a vyberte ji a vyberte **OK**. Pokud Visual Studio zjistí soubor *requirements.txt* v daném prostředí, zobrazí dotaz, zda chcete tyto balíčky nainstalovat.

1. Po chvíli se virtuální prostředí zobrazí pod uzlem **prostředí Pythonu** v **Průzkumník řešení**. Virtuální prostředí není ve výchozím nastavení aktivované, proto klikněte na něj pravým tlačítkem myši a vyberte **aktivovat prostředí**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Vytvoření virtuálního prostředí

Nové virtuální prostředí můžete vytvořit přímo v aplikaci Visual Studio následujícím způsobem:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **prostředí Pythonu** a vyberte **Přidat prostředí**nebo v rozevíracím seznamu prostředí na panelu nástrojů Python vyberte **Přidat prostředí** . V dialogovém okně **Přidat prostředí** , které se zobrazí, vyberte kartu **virtuální prostředí** :

    ![Karta virtuální prostředí v dialogovém okně Přidat prostředí](media/environments/environments-add-virtual-1-2019.png)

1. Zadejte název virtuálního prostředí, vyberte základní interpret a ověřte jeho umístění. V části **instalovat balíčky ze souboru**zadejte cestu k souboru *requirements.txt* v případě potřeby.

1. Projděte si další možnosti v dialogovém okně:

    | Možnost | Popis |
    | --- | --- |
    | Nastavit jako aktuální prostředí | Aktivuje nové prostředí ve vybraném projektu po vytvoření prostředí. |
    | Nastavit jako výchozí prostředí pro nové projekty | Automaticky nastaví a aktivuje virtuální prostředí v jakémkoli novém projektu vytvořeném v sadě Visual Studio. Při použití této možnosti by se mělo virtuální prostředí umístit do umístění mimo konkrétní projekt.  |
    | Zobrazit v okně prostředí Pythonu | Určuje, jestli se po vytvoření prostředí má otevřít okno **prostředí Pythonu** . |
    | Nastavit toto prostředí globálně jako dostupné | Určuje, jestli virtuální prostředí funguje taky jako globální prostředí. Při použití této možnosti by se mělo virtuální prostředí umístit do umístění mimo konkrétní projekt. |

1. Výběrem **vytvořit** dokončete virtuální prostředí. Visual Studio zobrazí indikátor průběhu a nakonfiguruje prostředí a stáhne všechny potřebné balíčky. Po dokončení se virtuální prostředí aktivuje a zobrazí se v uzlu **prostředí Pythonu** v **Průzkumník řešení** a v okně **prostředí Pythonu** pro projekt, který ho obsahuje.

### <a name="activate-an-existing-virtual-environment"></a>Aktivovat existující virtuální prostředí

Pokud jste již vytvořili virtuální prostředí jinde, můžete jej aktivovat pro projekt následujícím způsobem:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **prostředí Pythonu** a vyberte **Přidat prostředí**.

1. V zobrazeném dialogovém okně **Procházet** přejděte na složku obsahující virtuální prostředí a vyberte ji a vyberte **OK**. Pokud Visual Studio zjistí soubor *requirements.txt* v daném prostředí, zobrazí dotaz, zda chcete tyto balíčky nainstalovat.

1. Po chvíli se virtuální prostředí zobrazí pod uzlem **prostředí Pythonu** v **Průzkumník řešení**. Virtuální prostředí není ve výchozím nastavení aktivované, proto klikněte na něj pravým tlačítkem myši a vyberte **aktivovat prostředí**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Odebrání virtuálního prostředí

1. V **Průzkumník řešení**klikněte pravým tlačítkem na virtuální prostředí a vyberte **Odebrat**.

1. Visual Studio se zeptá, jestli se má odebrat nebo odstranit virtuální prostředí. Výběr možnosti **Odebrat** zpřístupňuje projekt, ale ponechá ho v systému souborů. Výběr možnosti **Odstranit** odstraní prostředí z projektu a odstraní ho ze systému souborů. Základní překladač není ovlivněn.

## <a name="view-installed-packages"></a>Zobrazit nainstalované balíčky

V Průzkumník řešení rozbalte kterýkoli uzel konkrétního prostředí pro rychlé zobrazení balíčků, které jsou nainstalované v daném prostředí (to znamená, že můžete importovat a používat tyto balíčky v kódu, když je prostředí aktivní):

![Balíčky Pythonu pro prostředí v Průzkumník řešení](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Chcete-li nainstalovat nové balíčky, klikněte pravým tlačítkem myši na prostředí a vyberte možnost **instalovat balíček python** a přepněte na kartu příslušné **balíčky** v okně **prostředí Pythonu** . Zadejte hledaný termín (obvykle název balíčku) a sada Visual Studio zobrazí vyhovující balíčky.
::: moniker-end
::: moniker range=">=vs-2019"
Pokud chcete nainstalovat nové balíčky, klikněte pravým tlačítkem na prostředí a vyberte **Spravovat balíčky Pythonu** (nebo použijte tlačítko balíček na panelu nástrojů Pythonu) a přepněte na kartu příslušné **balíčky** v okně **prostředí Pythonu** . Jednou na kartě **balíčky** zadejte hledaný termín (obvykle název balíčku) a Visual Studio zobrazí vyhovující balíčky.
::: moniker-end

V sadě Visual Studio se balíčky (a závislosti) pro většinu prostředí stahují z [indexu balíčku Pythonu (PyPi)](https://pypi.org), kde můžete také vyhledat dostupné balíčky. Stavový řádek a okno výstup sady Visual Studio zobrazují informace o instalaci. Chcete-li odinstalovat balíček, klikněte na něj pravým tlačítkem myši a vyberte možnost **Odebrat**.

Správce balíčků conda se obecně používá `https://repo.continuum.io/pkgs/` jako výchozí kanál, ale k dispozici jsou i další kanály. Další informace najdete v tématu [Správa kanálů](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.conda.IO).

Mějte na paměti, že zobrazené položky nemusí být vždy přesné a instalace a odinstalace nemusí být spolehlivá nebo dostupná. Sada Visual Studio používá správce balíčků PIP, pokud je k dispozici, a stáhne a nainstaluje v případě potřeby. Sada Visual Studio může také používat Správce balíčků easy_install. Zobrazí se také balíčky nainstalované pomocí nástroje `pip` nebo `easy_install` z příkazového řádku.

Všimněte si také, že Visual Studio předem neposílá podporu `conda` k instalaci balíčků do prostředí conda. `conda`Místo toho použijte příkaz z příkazového řádku.

> [!Tip]
> Běžným případem, kdy PIP nedokáže nainstalovat balíček, je, že balíček obsahuje zdrojový kód pro nativní komponenty v souborech * \* . PYD* . Bez nainstalované požadované verze sady Visual Studio nemůže PIP tyto součásti zkompilovat. Chybová zpráva zobrazená v této situaci je **Chyba: nepovedlo se najít vcvarsall.bat**. `easy_install` je často schopný stahovat předkompilované binární soubory a můžete si stáhnout vhodný kompilátor pro starší verze Pythonu [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266) . Další podrobnosti najdete v článku [jak řešit potíže s "nelze nalézt vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) na blogu týmu nástrojů Python Tools.

## <a name="see-also"></a>Viz také

- [Správa prostředí Pythonu v aplikaci Visual Studio](managing-python-environments-in-visual-studio.md)
- [Použít requirements.txt pro závislosti](managing-required-packages-with-requirements-txt.md)
- [Cesty pro hledání](search-paths.md)
- [Referenční dokumentace okna prostředí Pythonu](python-environments-window-tab-reference.md)
