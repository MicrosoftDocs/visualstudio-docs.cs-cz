---
title: Symboly pro ladění pythonu/C++ ve smíšeném režimu
description: Jak Visual Studio poskytuje možnost načíst symboly pro úplné ladění c++ a pythonu v kombinovaném režimu.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 77dc73b0be050e5108f73d38dfbbaa763d236995
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957596"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Instalace ladicích symbolů pro překladače Pythonu

Chcete-li poskytnout úplné ladění prostředí, [ladicí program Pythonu ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) v sadě Visual Studio potřebuje ladicí symboly pro překladač Pythonu se používá k analýzě mnoha interních datových struktur. Pro *python27.dll*, například odpovídající soubor symbolů je *python27.pdb*; pro *python36.dll*je soubor symbolů *python36.pdb*. Každá verze interpreta také dodává soubory symbolů pro různé moduly.

S Visual Studio 2017 a novější, Python 3 a Anaconda 3 interpreti automaticky nainstalovat své příslušné symboly a Visual Studio najde tyto symboly automaticky. Pro Visual Studio 2015 a starší nebo při použití jiných interpretů, je třeba stáhnout **Tools** > symboly samostatně a pak bod Visual Studio na ně prostřednictvím nástroje**možnosti** dialogového okna na **kartě ladění** > **symboly.** Tyto kroky jsou podrobně popsány v následujících částech.

Visual Studio vás může vyzvat, když potřebuje symboly, obvykle při spuštění relace ladění ve smíšeném režimu. V tomto případě se zobrazí dialogové okno se dvěma možnostmi:

- **Otevře tesá dialogové okno Nastavení symbolu** a otevře dialogové okno **Volby** na kartě **Ladění** > **symbolů.**
- **Stáhnout symboly pro můj interpret** otevře tuto stránku dokumentace, v takovém případě vyberte **Možnosti nástrojů** > **Options** a přejděte na kartu **Ladění** > **symbolů** pokračovat.

    ![Výzva k zadání symbolů ladicího programu ve smíšeném režimu](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Stáhnout symboly

- Python 3.5 a novější: získejte ladicí symboly prostřednictvím instalačního programu Pythonu. Vyberte **Vlastní instalace**, vyberte **Další,** abyste se dostali k **rozšířeným možnostem**, pak vyberte políčka pro **stažení ladicích symbolů** a **Stažení ladicích binárních souborů**:

    ![Instalační program Pythonu 3.x včetně ladicích symbolů](media/mixed-mode-debugging-symbols-installer35.png)

    Soubory symbolů (*.pdb*) se pak nacházejí v kořenové instalační složce (soubory symbolů pro jednotlivé moduly jsou také ve složce *DLL).* Z tohoto důvodu Visual Studio vyhledá automaticky a žádné další kroky jsou potřeba.

- Python 3.4.x a starší: symboly jsou k dispozici ke stažení *.zip* soubory z [oficiálních distribucí](#official-distributions) nebo [Enthought Canopy](#enthought-canopy). Po stažení extrahujte soubory do místní složky, abyste *pokračovali,* například složku Symboly ve složce Python.

    > [!Important]
    > Symboly se liší mezi menšími sestaveními Pythonu a mezi 32bitovými a 64bitovými sestaveními, takže chcete přesně odpovídat verzím. Chcete-li zkontrolovat používaný interpret, rozbalte *uzel* **Prostředí Pythonu** pod projektem v **Průzkumníku řešení** a poznamenejte si název prostředí. Pak přepněte do *okna* **Prostředí Pythonu** a poznamenejte si umístění instalace. Potom otevřete příkazové okno v tomto umístění a *spusťte python.exe*, který zobrazí přesnou verzi a zda je 32bitový nebo 64bitový.

- Pro jakoukoli jinou distribuci Pythonu jiných výrobců, jako je ActiveState Python: obraťte se na autory této distribuce a požádejte je, aby vám poskytli symboly. WinPython, pro jeho část, zahrnuje standardní interpret Pythonu beze změn, takže použijte symboly z oficiální distribuce pro odpovídající číslo verze.

## <a name="point-visual-studio-to-the-symbols"></a>Nasměrovat Visual Studio na symboly

Pokud jste si stáhli symboly samostatně, postupujte podle následujících kroků, aby visual studio vědomi těchto. Pokud jste nainstalovali symboly prostřednictvím instalačního programu Pythonu 3.5 nebo novějšího, Visual Studio je najde automaticky.

1. Vyberte nabídku**Možnosti** **nástrojů** > a přejděte na **Možnostladění** > **symbolů**.

1. Vyberte tlačítko **Přidat** na panelu nástrojů (naobrázku níže), zadejte složku, do které jste rozbalili stažené symboly (což je místo, kde se nachází *python.pdb,* například *c:\python34\Symbols*, zobrazeno níže), a vyberte **OK**.

    ![Volby symbolů ladicího programu ve smíšeném režimu](media/mixed-mode-debugging-symbols.png)

1. Během relace ladění visual studio může také vyzvat k zadání umístění zdrojového souboru pro interpret pythonu. Pokud jste si stáhli zdrojové soubory (například z [python.org/downloads/),](https://www.python.org/downloads/)pak na ně samozřejmě můžete také poukázat.

> [!Note]
> Funkce ukládání symbolů do mezipaměti zobrazené v dialogovém okně se používají k vytvoření místní mezipaměti symbolů získaných z online zdroje. Tyto funkce nejsou potřeba se symboly překladače Pythonu, protože symboly jsou již k dispozici místně. V každém případě, odkazovat [na určení symbolů a zdrojových souborů v ladicím programu Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) podrobnosti.

## <a name="official-distributions"></a>Úřední distribuce

| Verze Pythonu | Soubory ke stažení |
| --- | --- |
| 3.5 a novější | Nainstalujte symboly prostřednictvím instalačního programu Pythonu. |
| 3.4.4 | [32bitový](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32bitový](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32bitový](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32bitový](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32bitový](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32bitový](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32bitový](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32bitový](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32bitový](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32bitový](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32bitový](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64bitový](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32bitový](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32bitový](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32bitový](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32bitový](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32bitový](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32bitový](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32bitový](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32bitový](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32bitový](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32bitový](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32bitový](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32bitový](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32bitový](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32bitový](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32bitový](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64bitový](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Baldachýn

Enthought Canopy poskytuje symboly pro své binární soubory od verze 1.2. Jsou automaticky nainstalovány společně s distribucí, ale stále je třeba ručně přidat složku, která je obsahuje, do cesty symbolů, jak je popsáno výše. Pro typickou instalaci canopy pro jednotlivé uživatele jsou symboly umístěny v *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* pro 64bitovou verzi a *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts* pro 32bitovou verzi.

Enthought Canopy 1.1 a starší, stejně jako Enthought Python Distribution (EPD), neposkytují symboly interpretu a proto nejsou kompatibilní s laděním ve smíšeném režimu.
