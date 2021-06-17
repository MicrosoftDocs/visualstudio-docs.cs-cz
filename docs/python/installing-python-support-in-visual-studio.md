---
title: Instalace podpory Pythonu
description: Jak nainstalovat Python Tools for Visual Studio (PTVS) v Visual Studio 2017, 2015, 2013, 2012 a 2010, včetně možností a umístění instalace.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09fb452d579130cdf6597ada3af509b35f24ff43
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254807"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Jak nainstalovat podporu Pythonu v Visual Studio ve Windows

Pokud chcete nainstalovat podporu Pythonu pro Visual Studio (označovanou také jako Python Tools for Visual Studio nebo PTVS), postupujte podle pokynů v části, která odpovídá vaší verzi Visual Studio:

- [Visual Studio 2017 a Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 a starší](#visual-studio-2013-and-earlier)

Pokud chcete podporu Pythonu rychle otestovat po provedení instalačních kroků, otevřete interaktivní okno **Pythonu** stisknutím **klávesy Alt** I a +  zadáním `2+2` . Pokud nevidíte výstup příkazu `4` , znovu zkontrolujte kroky.

> [!Tip]
> Úloha Pythonu obsahuje užitečné rozšíření Cookiecutter, které poskytuje grafické uživatelské rozhraní pro zjišťování šablon, možností vstupních šablon a vytváření projektů a souborů. Podrobnosti najdete v tématu [Použití nástroje Cookiecutter.](using-python-cookiecutter-templates.md)

> [!Note]
> Podpora Pythonu není v současné době dostupná v Visual Studio pro Mac, ale je k dispozici v systémech Mac a Linux prostřednictvím Visual Studio Code. Podívejte [se na otázky a odpovědi.](overview-of-python-tools-for-visual-studio.md#questions-and-answers)

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 a Visual Studio 2017

1. Stáhněte a spusťte nejnovější Visual Studio instalace. Pokud jste Visual Studio nainstalovali, spusťte Instalační program pro Visual Studio, vyberte možnost  Upravit (viz Úprava Visual Studio [)](../install/modify-visual-studio.md)a přejděte ke kroku 2.

    > [!div class="nextstepaction"]
    > [Instalace Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Edice Community je edici pro jednotlivé vývojáře, výuku v učebnách, akademický výzkum a open source vývoje. Pro jiné účely nainstalujte [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) nebo [Visual Studio 2019 Enterprise.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

1. Instalační program vám zobrazí seznam úloh, což jsou skupiny souvisejících možností pro konkrétní vývojové oblasti. V případě Pythonu vyberte **úlohu Vývoj v Pythonu.**

    ![Úloha vývoj pro Python v instalačním Visual Studio souborů](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Volitelné: Pokud pracujete s datovými vědou, zvažte také úlohu Aplikace pro datovou **vědu a analýzy.** Tato úloha zahrnuje podporu jazyků Python, R a F#. Další informace najdete v tématu Úloha [Aplikace pro datovou vědu a analýzy.](data-science-and-analytical-applications-workload.md)

    > [!Note]
    > Úlohy Pythonu a datové vědy jsou k dispozici pouze Visual Studio 2017 verze 15.2 a novější.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Volitelné: Pokud pracujete s datovými vědou, zvažte také úlohu Aplikace pro datovou **vědu a analýzy.** Tato úloha zahrnuje podporu jazyků Python a F#. Další informace najdete v tématu Úloha [Aplikace pro datovou vědu a analýzy.](data-science-and-analytical-applications-workload.md)
    ::: moniker-end

1. Na pravé straně instalačního programu zvolte v případě potřeby další možnosti. Pokud chcete přijmout výchozí možnosti, přeskočte tento krok.

    ::: moniker range="vs-2017"
    ![Možnosti vývoje pro Python v instalačním programu Visual Studio.](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Možnosti vývoje pro Python v instalačním programu Visual Studio 2019](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Možnost | Popis |
    | --- | --- |
    | Distribuce Pythonu | Zvolte libovolnou kombinaci dostupných možností, například 32bitovou a 64bitovou variantu distribucí Pythonu 2, Pythonu 3, Minicondy, Anaconda2 a Anaconda3, se kterou plánujete pracovat. Každý zahrnuje interpreta distribuce, modul runtime a knihovny. Konkrétně Anaconda je otevřená platforma pro datové vědy, která obsahuje širokou škálu předinstalovaných balíčků. (K instalačnímu programu Visual Studio kdykoli vrátit a přidat nebo odebrat distribuce.)  **Poznámka:** Pokud jste nainstalovali distribuci mimo instalační program Visual Studio, není nutné zde kontrolovat ekvivalentní možnost. Visual Studio automaticky rozpozná existující instalace Pythonu. Viz [okno Prostředí Pythonu.](managing-python-environments-in-visual-studio.md#the-python-environments-window) Pokud je k dispozici novější verze Pythonu, než je vidět v instalačním programu, můžete tuto verzi nainstalovat samostatně a Visual Studio ji detekuje. |
    | **Podpora šablon Cookiecutter** | Nainstaluje grafické uživatelské rozhraní Cookiecutter ke zjišťování šablon, zadávání možností šablon a vytváření projektů a souborů. Viz [Použití rozšíření Cookiecutter.](using-python-cookiecutter-templates.md) |
    | **Webová podpora Pythonu** | Instaluje nástroje pro vývoj webů, včetně podpory úprav HTML, CSS a JavaScriptu, spolu s šablonami pro projekty používající architektury Bottle, Flask a Django. Viz [Šablony webových projektů Pythonu.](python-web-application-project-templates.md) |
    | **Podpora Pythonu pro IoT** | Podporuje vývoj pro Windows IoT Core pomocí Pythonu. |
    | **Nativní vývojové nástroje pythonu** | Nainstaluje kompilátor C++ a další nezbytné komponenty pro vývoj nativních rozšíření pro Python. Viz [Vytvoření rozšíření C++ pro Python.](working-with-c-cpp-python-in-visual-studio.md) Také nainstalujte **úlohu Vývoj desktopových aplikací pomocí jazyka C++** pro plnou podporu jazyka C++. |
    | **Azure Cloud Services core tools** | Poskytuje další podporu pro vývojářské Azure Cloud Services v Pythonu. Viz [Projekty cloudových služeb Azure.](python-azure-cloud-service-project-template.md) |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Možnost | Popis |
    | --- | --- |
    | Distribuce Pythonu | Zvolte libovolnou kombinaci dostupných možností, například 32bitovou a 64bitovou variantu distribucí Pythonu 2, Pythonu 3, Minicondy, Anaconda2 a Anaconda3, se kterou plánujete pracovat. Každý zahrnuje interpreta distribuce, modul runtime a knihovny. Konkrétně Anaconda je otevřená platforma pro datové vědy, která obsahuje širokou škálu předinstalovaných balíčků. (K instalačnímu programu Visual Studio kdykoli vrátit a přidat nebo odebrat distribuce.)  **Poznámka:** Pokud jste nainstalovali distribuci mimo instalační program Visual Studio, není nutné zde kontrolovat ekvivalentní možnost. Visual Studio automaticky rozpozná existující instalace Pythonu. Viz [okno Prostředí Pythonu.](managing-python-environments-in-visual-studio.md#the-python-environments-window) Pokud je k dispozici novější verze Pythonu, než je vidět v instalačním programu, můžete tuto verzi nainstalovat samostatně a Visual Studio ji detekuje. |
    | **Podpora šablon Cookiecutter** | Nainstaluje grafické uživatelské rozhraní Cookiecutter ke zjišťování šablon, zadávání možností šablon a vytváření projektů a souborů. Viz [Použití rozšíření Cookiecutter.](using-python-cookiecutter-templates.md) |
    | **Webová podpora Pythonu** | Instaluje nástroje pro vývoj webů, včetně podpory úprav HTML, CSS a JavaScriptu, spolu s šablonami pro projekty používající architektury Bottle, Flask a Django. Viz [Šablony webových projektů Pythonu.](python-web-application-project-templates.md) |
    | **Nativní vývojové nástroje pythonu** | Nainstaluje kompilátor C++ a další nezbytné komponenty pro vývoj nativních rozšíření pro Python. Viz [Vytvoření rozšíření C++ pro Python.](working-with-c-cpp-python-in-visual-studio.md) Také nainstalujte **úlohu Vývoj desktopových aplikací pomocí jazyka C++** pro plnou podporu jazyka C++. |
    ::: moniker-end

1. Po instalaci instalační program nabízí možnosti pro úpravu, spuštění, opravu nebo odinstalaci Visual Studio. Tlačítko **Upravit** se změní na **Aktualizovat,** když jsou Visual Studio dostupné pro všechny nainstalované součásti. (V **rozevírací** nabídce je pak k dispozici možnost Upravit.) Můžete také spustit Visual Studio a instalační program z nabídky Windows **Start** tak, že vyhledáte "Visual Studio".

    ![Spouštění, úpravy, úpravy nebo odinstalace Visual Studio z instalačního programu](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Řešení potíží

Pokud narazíte na problémy s instalací nebo spuštěním Pythonu v Visual Studio, zkuste následující postup:

- Zjistěte, jestli se stejná chyba vyskytuje v Rozhraní příkazového řádku *Pythonu,* tpython.exez příkazového řádku.
- Použijte možnost [**Opravit**](../install/repair-visual-studio.md) v instalačním Visual Studio.
- Opravte nebo přeinstalujte Python prostřednictvím **nastavení**  >  **Aplikace & funkcí** ve Windows.

**Příklad chyby:** Nepodařilo se spustit interaktivní proces: System.ComponentModel.Win32Exception (0x80004005): Neznámá chyba (0xc0000135) v Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Spusťte instalační Visual Studio prostřednictvím Ovládací panely > Programy a **funkce**, vyberte **Microsoft Visual Studio 2015** a pak **Změnit**.

1. V instalačním programu vyberte **Upravit.**

1. Vyberte **Programovací jazyky**  >  **Python Tools for Visual Studio** a pak **Další:**

    ![Možnost PTVS v instalačním Visual Studio 2015](media/installation-vs2015.png)

1. Po Visual Studio instalace [nainstalujte interpret Pythonu podle vašeho výběru.](installing-python-interpreters.md) Visual Studio 2015 podporuje pouze Python 3.5 a starší. Novější verze vygenerují zprávu jako **Unsupported Python version 3.6 ( Nepodporovaný Python verze 3.6).** Pokud už máte nainstalovaný interpret a Visual Studio ho automaticky nerozpozná, podívejte se na stránku [Ruční identifikace existujícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 a starší

1. Nainstalujte odpovídající verzi Python Tools for Visual Studio pro vaši verzi Visual Studio:

    - Visual Studio 2013: [PTVS 2.2.2 pro Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). Dialogové **okno** Soubor nového projektu v Visual Studio 2013 vám poskytne zástupce pro tento  >   proces.
    - Visual Studio 2010 a 2012: [PTVS 2.1.1 pro Visual Studio 2010 a 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Nainstalujte interpret Pythonu podle vašeho výběru.](installing-python-interpreters.md) Pokud už máte nainstalovaný interpret a Visual Studio ho automaticky nerozpozná, podívejte se na stránku [Ruční identifikace existujícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Umístění instalace

Ve výchozím nastavení se podpora Pythonu instaluje pro všechny uživatele na počítači.

Pro Visual Studio 2019 a Visual Studio 2017 se úloha Pythonu nainstaluje do složky *%ProgramFiles(x86)%\Microsoft Visual Studio \\<VS_version>\\<VS_edition>Common7\IDE\Extensions\Microsoft\Python,* kde VS_version je &lt; &gt; 2019 nebo 2017 a VS_edition je &lt; &gt; Community, Professional nebo Enterprise.

Pro Visual Studio 2015 a starší jsou instalační cesty následující:

- 32bitová verze:
  - Cesta: *%Program Files(x86)%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - Umístění cesty v registru: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64bitová verze:
  - Cesta: *%Program Files%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - Umístění cesty v registru: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

kde:

- &lt;VS_ver &gt; je:
  - 14.0 pro Visual Studio 2015
  - 12.0 pro Visual Studio 2013
  - 11.0 pro Visual Studio 2012
  - 10.0 pro Visual Studio 2010
- &lt;PTVS_ver je číslo verze, například &gt; 2.2.2, 2.1.1, 2.0, 1.5, 1.1 nebo 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalace specifické pro uživatele (1.5 a starší)

Python Tools for Visual Studio verze 1.5 a starší byla povolena pouze pro aktuálního uživatele. V takovém případě je instalační cesta *%LocalAppData%\Microsoft\VisualStudio \\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>,* kde VS_ver a PTVS_ver jsou stejné jako výše &lt; &gt; &lt; &gt; popsané.
