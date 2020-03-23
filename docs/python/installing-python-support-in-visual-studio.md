---
title: Podpora pro Install Python
description: Jak nainstalovat nástroje Pythonu pro Visual Studio (PTVS) ve Visual Studiu 2017, 2015, 2013, 2012 a 2010, včetně možností a umístění instalace.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 15869119ea867e41d3b91a1f046d1ffb995cd4e4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75398425"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Jak nainstalovat podporu Pythonu v Sadě Visual Studio ve Windows

Chcete-li nainstalovat podporu Pythonu pro Visual Studio (označované také jako Nástroje Pythonu pro Visual Studio nebo PTVS), postupujte podle pokynů v části, která odpovídá vaší verzi Sady Visual Studio:

- [Visual Studio 2017 a Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 a starší](#visual-studio-2013-and-earlier)

Chcete-li rychle otestovat podporu Pythonu po provedení kroků instalace, `2+2`otevřete interaktivní okno **Pythonu** stisknutím **klávesy Alt**+**I** a zadáním klávesy . Pokud nevidíte výstup , `4`zkontrolujte kroky.

> [!Tip]
> Úloha Pythonu zahrnuje užitečné rozšíření Cookiecutter, které poskytuje grafické uživatelské rozhraní pro zjišťování šablon, možnosti vstupníšablony a vytváření projektů a souborů. Podrobnosti naleznete v [tématu Použití cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Podpora Pythonu není v současné době k dispozici ve Visual Studiu pro Mac, ale je k dispozici na Maca a Linuxu prostřednictvím visual studia Code. Viz [otázky a odpovědi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 a Visual Studio 2017

1. Stáhněte a spusťte nejnovější instalační program sady Visual Studio. Pokud už máte nainstalovaný Visual Studio, spusťte Instalační službu sady Visual Studio, vyberte možnost **Změnit** (viz [Úprava sady Visual Studio)](../install/modify-visual-studio.md)a přejděte ke kroku 2.

    > [!div class="nextstepaction"]
    > [Instalace komunity Visual Studia 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Komunitní vydání je určen pro jednotlivé vývojáře, výuku ve třídě, akademický výzkum a vývoj s otevřeným zdrojovým kódem. Pro další použití nainstalujte [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) nebo Visual Studio [2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Instalační program vám zobrazí seznam úloh, což jsou skupiny souvisejících možností pro konkrétní oblasti vývoje. Pro Python vyberte vývojové zatížení **Pythonu.**

    ![Úloha vývoje Pythonu v instalačním programu Visual Studia](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Volitelné: Pokud pracujete s datovou vědou, zvažte také zatížení **datové vědy a analytických aplikací.** Toto zatížení zahrnuje podporu pro jazyky Python, R a F#. Další informace naleznete v [tématu Zpracování dat a analytické aplikace zatížení](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Úlohy Pythonu a datové vědy jsou dostupné jenom s Visual Studio 2017 verze 15.2 a novější.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Volitelné: Pokud pracujete s datovou vědou, zvažte také zatížení **datové vědy a analytických aplikací.** Toto zatížení zahrnuje podporu pro jazyky Python a F#. Další informace naleznete v [tématu Zpracování dat a analytické aplikace zatížení](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Na pravé straně instalátoru, v případě potřeby zvolte další možnosti. Přeskočenítohoto kroku přijměte výchozí možnosti.

    ::: moniker range="vs-2017"
    ![Možnosti vývoje Pythonu v instalačním programu Sady Visual Studio](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Možnosti vývoje Pythonu v instalačním programu Visual Studia 2019](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Možnost | Popis |
    | --- | --- |
    | Distribuce Pythonu | Vyberte libovolnou kombinaci dostupných možností, například 32bitové a 64bitové varianty distribucí Pythonu 2, Python3, Miniconda, Anaconda2 a Anaconda3, se kterými plánujete pracovat. Každý obsahuje interpret distribuce, runtime a knihovny. Anaconda je platforma pro otevřenou datovou vědu, která zahrnuje širokou škálu předinstalovaných balíčků. (Můžete se kdykoli vrátit k instalačnímu programu sady Visual Studio a přidat nebo odebrat distribuce.)  **Poznámka:** Pokud jste nainstalovali distribuci mimo instalační program sady Visual Studio, není nutné zde kontrolovat ekvivalentní možnost. Visual Studio automaticky detekuje existující instalace Pythonu. Viz [okno Prostředí Pythonu](managing-python-environments-in-visual-studio.md#the-python-environments-window). Také pokud je k dispozici novější verze Pythonu, než co je uvedeno v instalačním programu, můžete nainstalovat tuto verzi samostatně a Visual Studio ji detekuje. |
    | **Podpora pro Cookiecutter template** | Nainstaluje uživatelské okno Cookiecutter grafické hodování, aby zjišťovat šablony, vstupní šablony možnosti a vytvářet projekty a soubory. Viz [Použití rozšíření Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Webová podpora pythonu** | Nainstaluje nástroje pro vývoj webu, včetně podpory úprav HTML, CSS a JavaScriptu, spolu se šablonami pro projekty používající architektury Bottle, Flask a Django. Viz [Šablony webových projektů pythonu](python-web-application-project-templates.md). |
    | **Podpora pro Python IoT** | Podporuje vývoj Windows IoT Core pomocí Pythonu. |
    | **Nativní vývojové nástroje Pythonu** | Nainstaluje kompilátor Jazyka C++ a další nezbytné součásti pro vývoj nativních rozšíření pro Python. Viz [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md). Také nainstalujte vývoj plochy s úlohou **C++** pro plnou podporu C++. |
    | **Základní nástroje Cloudových služeb Azure** | Poskytuje další podporu pro vývojáře Cloud Services Azure v Pythonu. Viz [Projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Možnost | Popis |
    | --- | --- |
    | Distribuce Pythonu | Vyberte libovolnou kombinaci dostupných možností, například 32bitové a 64bitové varianty distribucí Pythonu 2, Python3, Miniconda, Anaconda2 a Anaconda3, se kterými plánujete pracovat. Každý obsahuje interpret distribuce, runtime a knihovny. Anaconda je platforma pro otevřenou datovou vědu, která zahrnuje širokou škálu předinstalovaných balíčků. (Můžete se kdykoli vrátit k instalačnímu programu sady Visual Studio a přidat nebo odebrat distribuce.)  **Poznámka:** Pokud jste nainstalovali distribuci mimo instalační program sady Visual Studio, není nutné zde kontrolovat ekvivalentní možnost. Visual Studio automaticky detekuje existující instalace Pythonu. Viz [okno Prostředí Pythonu](managing-python-environments-in-visual-studio.md#the-python-environments-window). Také pokud je k dispozici novější verze Pythonu, než co je uvedeno v instalačním programu, můžete nainstalovat tuto verzi samostatně a Visual Studio ji detekuje. |
    | **Podpora pro Cookiecutter template** | Nainstaluje uživatelské okno Cookiecutter grafické hodování, aby zjišťovat šablony, vstupní šablony možnosti a vytvářet projekty a soubory. Viz [Použití rozšíření Cookiecutter](using-python-cookiecutter-templates.md). |
    | **Webová podpora pythonu** | Nainstaluje nástroje pro vývoj webu, včetně podpory úprav HTML, CSS a JavaScriptu, spolu se šablonami pro projekty používající architektury Bottle, Flask a Django. Viz [Šablony webových projektů pythonu](python-web-application-project-templates.md). |
    | **Nativní vývojové nástroje Pythonu** | Nainstaluje kompilátor Jazyka C++ a další nezbytné součásti pro vývoj nativních rozšíření pro Python. Viz [Vytvoření rozšíření C++ pro Python](working-with-c-cpp-python-in-visual-studio.md). Také nainstalujte vývoj plochy s úlohou **C++** pro plnou podporu C++. |
    | **Základní nástroje Cloudových služeb Azure** | Poskytuje další podporu pro vývojáře Cloud Services Azure v Pythonu. Viz [Projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

1. Po instalaci poskytuje instalační program možnosti úpravy, spuštění, opravy nebo odinstalace sady Visual Studio. Tlačítko **Změnit** se změní na **Aktualizovat,** pokud jsou k dispozici aktualizace sady Visual Studio pro všechny nainstalované součásti. (Možnost **Změnit** je pak k dispozici v rozevírací nabídce.) Visual Studio a instalační program můžete spustit také z nabídky **Start** systému Windows vyhledáním v "Visual Studio".

    ![Spuštění, úprava, úprava nebo odinstalace sady Visual Studio z instalačního programu](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Řešení potíží

Pokud narazíte na problémy s instalací nebo spuštěním Pythonu v sadě Visual Studio, vyzkoušejte následující postup:

- Zjistěte, zda dojde ke stejné chybě pomocí rozhraní PŘÍKAZOVÉHO ŘÁDKU pythonu, tedy spuštění *python.exe* z příkazového řádku.
- Použijte možnost [**Opravit**](../install/repair-visual-studio.md) v instalačním programu sady Visual Studio.
- Oprava nebo přeinstalace Pythonu prostřednictvím **aplikací nastavení** > **& funkce** v systému Windows.

**Příklad chyby**: Nepodařilo se spustit interaktivní proces: System.ComponentModel.Win32Exception (0x80004005): Neznámá chyba (0xc0000135) na adrese Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Spusťte instalační program sady Visual Studio pomocí **Ovládacích panelů > programy a funkce**, vyberte **položku Microsoft Visual Studio 2015** a **potom možnost Změnit**.

1. V instalačním programu vyberte **Změnit**.

1. Vyberte **nástroje Pythonu pro programovací jazyky** > **pro Visual Studio** a potom **další**:

    ![Možnost PTVS v instalačním programu Sady Visual Studio 2015](media/installation-vs2015.png)

1. Po dokončení instalace sady Visual Studio [nainstalujte interpreta Pythonu podle vašeho výběru](installing-python-interpreters.md). Visual Studio 2015 podporuje jenom Python 3.5 a starší; novější verze generovat zprávu, jako **je nepodporovaný Python verze 3.6**). Pokud už máte nainstalovaný interpret a Visual Studio ho nerozpozná automaticky, přečtěte si informace [o ruční identifikaci existujícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 a starší

1. Nainstalujte příslušnou verzi Pythontools pro Visual Studio pro vaši verzi Sady Visual Studio:

    - Visual Studio 2013: [PTVS 2.2.2 pro Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). Dialogové okno**Nový projekt** **souboru** > v Sadě Visual Studio 2013 poskytuje zástupce pro tento proces.
    - Visual Studio 2010 a 2012: [PTVS 2.1.1 pro Visual Studio 2010 a 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Nainstalujte si interpreta Pythonu podle vašeho výběru](installing-python-interpreters.md). Pokud už máte nainstalovaný interpret a Visual Studio ho nerozpozná automaticky, přečtěte si informace [o ruční identifikaci existujícího prostředí](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Instalace umístění

Ve výchozím nastavení je podpora Pythonu nainstalována pro všechny uživatele v počítači.

Pro Visual Studio 2019 a Visual Studio 2017 je úloha Pythonu nainstalovaná v *%ProgramFiles(x86)\Microsoft Visual\\ Studio<VS_version>VS_version \\<VS_edition>Common7\IDE\Extensions\Microsoft\Python,* kde &lt;je VS_version&gt; 2019 nebo 2017 a &lt;VS_edition&gt; je Community, Professional nebo Enterprise.

Pro Visual Studio 2015 a starší jsou instalační cesty následující:

- 32bitové:
  - Cesta: *%Program Files(x86)%\Microsoft \<Visual Studio VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*
  - Umístění cesty v registru: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64bitové:
  - Cesta: *%Program Files%\Microsoft \<Visual Studio VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*
  - Umístění cesty v registru: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

kde:

- &lt;VS_ver&gt; je:
  - 14.0 pro Visual Studio 2015
  - 12.0 pro Visual Studio 2013
  - 11.0 pro Visual Studio 2012
  - 10.0 pro Visual Studio 2010
- &lt;PTVS_ver&gt; je číslo verze, například 2.2.2, 2.1.1, 2.0, 1.5, 1.1 nebo 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalace specifické pro uživatele (1.5 a starší)

Nástroje Pythonu pro visual studio 1.5 a dřívější povolená instalace pouze pro aktuálního uživatele, v takovém případě je instalační cesta *\\ %LocalAppData%\Microsoft\VisualStudio<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>,* kde &lt;jsou VS_ver&gt; a &lt;PTVS_ver&gt; stejné, jak je popsáno výše.
