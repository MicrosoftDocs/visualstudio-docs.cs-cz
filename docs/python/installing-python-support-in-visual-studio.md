---
title: Instalace podpory Pythonu
description: Jak nainstalovat Python Tools for Visual Studio (PTVS) v aplikaci Visual Studio 2017, 2015, 2013, 2012 a 2010, včetně možností a umístění instalace.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 910b3b5491660cbcd6132aff68ebeabafaeea0d5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540644"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Jak nainstalovat podporu Pythonu v aplikaci Visual Studio ve Windows

Pro instalaci podpory Pythonu pro Visual Studio (označované také jako Python Tools for Visual Studio nebo PTVS) postupujte podle pokynů v části, které odpovídají vaší verzi sady Visual Studio:

- [Visual Studio 2017 a Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 a starší](#visual-studio-2013-and-earlier)

Pokud chcete rychle otestovat podporu Pythonu po instalaci těchto kroků, otevřete **interaktivní okno Pythonu** stisknutím klávesy **ALT** + **i** a zadáním `2+2` . Pokud se výstup nezobrazuje, proveďte `4` znovu kontrolu vašich kroků.

> [!Tip]
> Úlohy Pythonu zahrnují užitečné rozšíření Cookiecutter, které poskytuje grafické uživatelské rozhraní pro zjišťování šablon, možnosti vstupní šablony a vytváření projektů a souborů. Podrobnosti najdete v tématu [použití Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Podpora Pythonu není v Visual Studio pro Mac v současnosti dostupná, ale je k dispozici v systému Mac a Linux prostřednictvím Visual Studio Code. Podívejte [se na otázky a odpovědi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 a Visual Studio 2017

1. Stáhněte si a spusťte nejnovější instalační program sady Visual Studio. Pokud už máte Visual Studio nainstalované, spusťte Instalační program pro Visual Studio, vyberte možnost **Upravit** (viz [Změna sady Visual Studio](../install/modify-visual-studio.md)) a přejděte ke kroku 2.

    > [!div class="nextstepaction"]
    > [Nainstalovat Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Edice Community je určená pro jednotlivé vývojáře, výukové učebny, akademické výzkumy a vývoj open source. Pro jiné účely nainstalujte [Visual studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) nebo [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Instalační program zobrazí seznam úloh, které jsou skupiny souvisejících možností pro konkrétní oblasti vývoje. V případě Pythonu vyberte úlohu **vývoje pro Python** .

    ![Úloha vývoje v Pythonu v instalačním programu sady Visual Studio](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Volitelné: Pokud pracujete s datovou vědy, zvažte také úlohu **aplikace pro datové vědy a analýzy** . Tato úloha zahrnuje podporu pro jazyky Python, R a F #. Další informace najdete v tématu [úlohy pro datové vědy a analytické aplikace](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Úlohy Pythonu a datové vědy jsou k dispozici pouze se sadou Visual Studio 2017 verze 15,2 a novější.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Volitelné: Pokud pracujete s datovou vědy, zvažte také úlohu **aplikace pro datové vědy a analýzy** . Tato úloha zahrnuje podporu pro jazyky Python a F #. Další informace najdete v tématu [úlohy pro datové vědy a analytické aplikace](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Na pravé straně instalačního programu zvolte v případě potřeby další možnosti. Pokud chcete přijmout výchozí možnosti, přeskočte tento krok.

    ::: moniker range="vs-2017"
    ![Možnosti vývoje v Pythonu v instalačním programu sady Visual Studio](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Možnosti vývoje v Pythonu v instalačním programu sady Visual Studio 2019](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Možnost | Popis |
    | --- | --- |
    | Distribuce Pythonu | Vyberte libovolnou kombinaci dostupných možností, jako jsou 32 a 64 bitových variant Pythonu 2, Python 3, Miniconda, Anaconda2 a Anaconda3 distribuce, se kterými chcete pracovat. Každá z nich zahrnuje překladač, modul runtime a knihovny distribuce. Anaconda je konkrétně otevřená platforma pro datové vědy, která zahrnuje řadu předem nainstalovaných balíčků. (V instalačním programu sady Visual Studio se můžete kdykoli vrátit a přidat nebo odebrat distribuce.)  **Poznámka**: Pokud jste nainstalovali distribuci mimo instalační program sady Visual Studio, není nutné zaškrtnout odpovídající možnost. Visual Studio automaticky detekuje existující instalace Pythonu. Podívejte [se na okno prostředí Pythonu](managing-python-environments-in-visual-studio.md#the-python-environments-window). Pokud je k dispozici novější verze Pythonu, než jaká je zobrazená v instalačním programu, můžete nainstalovat tuto verzi samostatně a aplikace Visual Studio ji detekuje. |
    | **Podpora šablon Cookiecutter** | Nainstaluje grafické uživatelské rozhraní Cookiecutter pro zjišťování šablon, možností vstupní šablony a vytváření projektů a souborů. Viz [použití rozšíření Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Podpora webu Pythonu** | Nainstaluje nástroje pro vývoj pro web, včetně podpory HTML, CSS a úprav JavaScriptu, spolu se šablonami pro projekty, které využívají láhve, baňky a Django architektury. Viz [šablony webových projektů v Pythonu](python-web-application-project-templates.md). |
    | **Podpora IoT v Pythonu** | Podporuje vývoj Windows IoT Core pomocí Pythonu. |
    | **Nástroje pro nativní vývoj v Pythonu** | Nainstaluje kompilátor C++ a další nezbytné komponenty pro vývoj nativních rozšíření pro Python. Viz [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md). Nainstalujte také úlohu **vývoj desktopových aplikací pomocí C++** pro úplnou podporu c++. |
    | **Základní nástroje pro Azure Cloud Services** | Poskytuje další podporu pro vývojáře Azure Cloud Services v Pythonu. Viz [projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Možnost | Popis |
    | --- | --- |
    | Distribuce Pythonu | Vyberte libovolnou kombinaci dostupných možností, jako jsou 32 a 64 bitových variant Pythonu 2, Python 3, Miniconda, Anaconda2 a Anaconda3 distribuce, se kterými chcete pracovat. Každá z nich zahrnuje překladač, modul runtime a knihovny distribuce. Anaconda je konkrétně otevřená platforma pro datové vědy, která zahrnuje řadu předem nainstalovaných balíčků. (V instalačním programu sady Visual Studio se můžete kdykoli vrátit a přidat nebo odebrat distribuce.)  **Poznámka**: Pokud jste nainstalovali distribuci mimo instalační program sady Visual Studio, není nutné zaškrtnout odpovídající možnost. Visual Studio automaticky detekuje existující instalace Pythonu. Podívejte [se na okno prostředí Pythonu](managing-python-environments-in-visual-studio.md#the-python-environments-window). Pokud je k dispozici novější verze Pythonu, než jaká je zobrazená v instalačním programu, můžete nainstalovat tuto verzi samostatně a aplikace Visual Studio ji detekuje. |
    | **Podpora šablon Cookiecutter** | Nainstaluje grafické uživatelské rozhraní Cookiecutter pro zjišťování šablon, možností vstupní šablony a vytváření projektů a souborů. Viz [použití rozšíření Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Podpora webu Pythonu** | Nainstaluje nástroje pro vývoj pro web, včetně podpory HTML, CSS a úprav JavaScriptu, spolu se šablonami pro projekty, které využívají láhve, baňky a Django architektury. Viz [šablony webových projektů v Pythonu](python-web-application-project-templates.md). |
    | **Nástroje pro nativní vývoj v Pythonu** | Nainstaluje kompilátor C++ a další nezbytné komponenty pro vývoj nativních rozšíření pro Python. Viz [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md). Nainstalujte také úlohu **vývoj desktopových aplikací pomocí C++** pro úplnou podporu c++. |
    | **Základní nástroje pro Azure Cloud Services** | Poskytuje další podporu pro vývojáře Azure Cloud Services v Pythonu. Viz [projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

1. Po instalaci poskytuje instalační program možnosti pro úpravu, spuštění, opravu nebo odinstalaci sady Visual Studio. Tlačítko **Upravit** se změní na **aktualizace** , když jsou k dispozici aktualizace sady Visual Studio pro všechny nainstalované součásti. (Možnost **Upravit** je pak k dispozici v rozevírací nabídce.) Můžete také spustit aplikaci Visual Studio a instalační program z nabídky **Start** v systému Windows, a to tak, že vyhledáte v aplikaci Visual Studio.

    ![Spuštění, úprava, úprava nebo odinstalace sady Visual Studio z instalačního programu](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Řešení potíží

Pokud narazíte na problémy s instalací nebo spuštěním Pythonu v aplikaci Visual Studio, zkuste následující:

- Určete, zda se ke stejné chybě dochází pomocí rozhraní příkazového řádku Python, které je spuštěno *python.exe* z příkazového řádku.
- Použijte možnost [**opravit**](../install/repair-visual-studio.md) v instalačním programu sady Visual Studio.
- Opravte nebo přeinstalujte Python prostřednictvím **Nastavení**  >  **aplikace & funkce** v systému Windows.

**Příklad chyby**: Nepodařilo se spustit interaktivní proces: System. ComponentModel. Win32Exception (0x80004005): Neznámá chyba (0xc0000135) v Microsoft. PythonTools. REPL. PythonInteractiveEvaluator. D__43. MoveNext ().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Spusťte instalační program sady Visual Studio pomocí **ovládacího panelu > programy a funkce**, vyberte **Microsoft Visual Studio 2015** a pak **změňte**.

1. V instalačním programu vyberte možnost **změnit**.

1. Vyberte **programovací jazyky**  >  **Python Tools for Visual Studio** a potom **Další**:

    ![Možnost PTVS v instalačním programu sady Visual Studio 2015](media/installation-vs2015.png)

1. Po dokončení instalace sady Visual Studio [nainstalujte interpret Python podle svého výběru](installing-python-interpreters.md). Visual Studio 2015 podporuje jenom Python 3,5 a starší; novější verze vygenerují zprávu, jako je například **Nepodporovaná verze pythonu 3,6**). Pokud již je překladač nainstalován a aplikace Visual Studio jej nerozpozná automaticky, přečtěte si téma [Ruční identifikace stávajícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 a starší

1. Nainstalujte odpovídající verzi Python Tools for Visual Studio pro vaši verzi sady Visual Studio:

    - Visual Studio 2013: [PTVS 2.2.2 pro Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). **File**  >  Dialogové okno**Nový projekt** v Visual Studio 2013 poskytuje zástupce pro tento proces.
    - Visual Studio 2010 a 2012: [PTVS 2.1.1 pro Visual Studio 2010 a 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Nainstalujte interpret Python podle svého výběru](installing-python-interpreters.md). Pokud již je překladač nainstalován a aplikace Visual Studio jej nerozpozná automaticky, přečtěte si téma [Ruční identifikace stávajícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Umístění instalace

Ve výchozím nastavení je podpora Pythonu nainstalovaná pro všechny uživatele v počítači.

Pro Visual Studio 2019 a Visual Studio 2017 je úloha Pythonu nainstalovaná v *% ProgramFiles (x86)% \ Microsoft Visual Studio \\<VS_version>\\<VS_edition>Common7\IDE\Extensions\Microsoft\Python* , kde &lt; VS_version &gt; 2019 nebo 2017 a &lt; VS_edition &gt; je komunita, Professional nebo Enterprise.

Pro Visual Studio 2015 a starší jsou instalační cesty následující:

- 32-bit:
  - Cesta: *% Program Files (x86)% \ Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio \\<PTVS_ver>*
  - Umístění registru cesty: **HKEY_LOCAL_MACHINE \software\microsoft\pythontools \\<VS_ver> \installdir**
- 64-bit:
  - Cesta: *% Program Files%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Python Tools for visual studio \\<PTVS_ver>*
  - Umístění registru cesty: **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\pythontools \\<VS_ver> \installdir**

kde:

- &lt;VS_ver &gt; :
  - 14,0 pro Visual Studio 2015
  - 12,0 pro Visual Studio 2013
  - 11,0 pro Visual Studio 2012
  - 10,0 pro Visual Studio 2010
- &lt;PTVS_ver &gt; je číslo verze, například 2.2.2, 2.1.1, 2,0, 1,5, 1,1 nebo 1,0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalace specifické pro uživatele (1,5 a starší)

Python Tools for Visual Studio 1,5 a starší povolená instalace pouze pro aktuálního uživatele. v takovém případě je instalační cesta *%LocalAppData%\Microsoft\VisualStudio \\<VS_ver> nástroje \Extensions\microsoft\python pro Visual Studio \\<PTVS_ver>* , kde &lt; VS_ver &gt; a &lt; PTVS_ver &gt; jsou stejné, jak je popsáno výše.
