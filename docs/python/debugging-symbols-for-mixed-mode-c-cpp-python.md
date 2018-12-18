---
title: Symboly pro ladění ve smíšeném režimu Python/C++
description: Jak Visual Studio poskytuje možnost načíst symboly pro dokončení C++ ve smíšeném režimu a ladění pro Python.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 62e3727b36e6ba3231ee12388e1be5bde40d080a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062687"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Instalace interpretů Pythonu symboly pro ladění

Zajištění úplného ladicího prostředí [ladicí program Pythonu ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) v sadě Visual Studio potřebuje ladění symbolů pro interpret Pythonu se použije k parsování mnoha interních datových struktur. Pro *python27.dll*, je třeba odpovídající souboru symbolů *python27.pdb*; pro *python36.dll*, je soubor symbolů *python36.pdb*. Každou verzi interpreta také poskytuje soubory symbolů pro celou řadu modulů.

Pomocí sady Visual Studio 2017 interpretů Pythonu 3 a 3 programu Anaconda automaticky instalovat jejich odpovídajících symbolů a sady Visual Studio automaticky vyhledá tyto symboly. Pro Visual Studio 2015 a starší nebo při použití jiných interprety, budete muset stáhnout symboly samostatně a pak k nim prostřednictvím sady Visual Studio **nástroje** > **možnosti** dialogového okna v **ladění** > **symboly** kartu. Tyto kroky jsou podrobně popsané v následujících částech.

Visual Studio může výzvu, když je nutné symboly, obvykle při spuštění relace ladění ve smíšeném režimu. V takovém případě se zobrazí dialogové okno s dvě možnosti:

- **Dialogové okno nastavení symbolů otevřít** otevře **možnosti** dialogové okno **ladění** > **symboly** kartu.
- **Stáhnout symboly pro interpret** otevře tato k dispozici dokumentace stránky, v takovém případě vyberte **nástroje** > **možnosti** a přejděte **ladění**   >  **Symboly** kartu, abyste mohli pokračovat.

    ![Řádku symboly ladění ve smíšeném režimu](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Stáhnout symboly

- Python 3.5 a novější: získání symboly ladění přes instalační program Pythonu. Vyberte **vlastní instalace**vyberte **Další** zobrazíte **rozšířené možnosti**, potom zaškrtněte políčka pro **stáhnout symboly ladění** a **ladicí binární soubory ke stažení**:

    ![Instalační program Pythonu 3.x včetně symboly ladění](media/mixed-mode-debugging-symbols-installer35.png)

    Soubory symbolů (*PDB*) pak najdete v kořenové složce instalace (jsou soubory symbolů pro jednotlivé moduly v *knihovny DLL* také složky). Z tohoto důvodu sady Visual Studio vyhledá je automaticky a nejsou potřeba žádné další kroky.

- Python 3.4.x a dříve: symboly jsou k dispozici ke stažení *ZIP* souborů z doručené pošty [oficiální distribuce](#official-distributions) nebo [Enthought zápoje](#enthought-canopy). Po stažení, rozbalte soubory do místní složky, abyste mohli pokračovat, například *symboly* složku ve složce Python.

    > [!Important]
    > Symboly se liší mezi menší sestaveními jazyka Python a mezi 32bitové a 64bitové sestavení, takže chcete přesně shodovat s verzemi. Chcete-li zkontrolovat překladač používá, rozbalte **prostředí Pythonu** *uzel* v rámci vašeho projektu v **Průzkumníku řešení** a poznamenejte si název prostředí. Potom přejděte **prostředí Pythonu** *okno* a poznamenejte si umístění instalace. Pak otevřete okno příkazového řádku v tomto umístění a spusťte *python.exe*, který zobrazuje přesnou verzi a zda je 32bitová nebo 64bitová verze.

- Pro všechny ostatní třetích stran distribuci jazyka Python jako je ActiveState Python: Obraťte se autoři příslušné distribuci a požádejte je, kde přinášejí symboly. WinPython, jeho části, zahrnuje standardní interpret Pythonu beze změn, tak použijte symboly z oficiální distribuce pro příslušné číslo verze.

## <a name="point-visual-studio-to-the-symbols"></a>Visual Studio přejděte na symboly

Pokud jste si stáhli samostatně symboly, podle následujících pokynů sada Visual Studio vědomi. Pokud jste nainstalovali symboly prostřednictvím Python 3.5 nebo novější instalačního programu, sada Visual Studio najde je automaticky.

1. Vyberte **nástroje** > **možnosti** nabídky a přejděte do **ladění** > **symboly**.

1. Vyberte **přidat** tlačítko na panelu nástrojů (popsaných níže), zadejte složku, kam jste rozbalili stažené symboly (což je tam, kde *python.pdb* nachází, jako například *c:\python34\Symbols* , jak je znázorněno níže) a vyberte **OK**. 

    ![Možnosti symbolů ladění ve smíšeném režimu](media/mixed-mode-debugging-symbols.png)

1. Během relace ladění Visual Studio mohou také vyžadovat zadání umístění zdrojového souboru pro interpret Pythonu. Pokud jste stáhli zdrojové soubory (z [python.org/downloads](https://www.python.org/downloads), například), pak samozřejmě pak můžete jim také.

> [!Note]
> Funkce ukládání do mezipaměti symbolů zobrazené v dialogovém okně umožňují vytvořit místní mezipaměť symbolů získaných z online zdroje. Tyto funkce nejsou potřeba se symboly interpret Pythonu, protože symboly jsou už k dispozici místně. V každém případě najdete [zadejte symboly a zdrojové soubory v ladicím programu sady Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) podrobnosti.

## <a name="official-distributions"></a>Oficiální distribuce

| Verze Pythonu | Soubory ke stažení | 
| --- | --- | 
| 3.5 a novější | Nainstalujte symboly přes instalační program Pythonu. | 
| 3.4.4 | [32-bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32-bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32-bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32-bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32-bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32-bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32-bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32-bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32-bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32-bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32-bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32-bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32-bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32-bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32-bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32-bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32-bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32-bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32-bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32-bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32-bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32-bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32-bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32-bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32-bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32-bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought zápoje

Enthought zápoje poskytuje symboly pro její binární soubory od verze 1.2. Jsou automaticky nainstalovány spolu s distribucí, ale je stále potřeba ručně přidat složku obsahující do cesty k symbolu jak je popsáno výše. Pro instalaci zápoje typické na uživatele, jsou symboly umístěné v *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* pro 64bitovou verzi a *%UserProfile%\AppData\Local\Enthought\ Canopy32\User\Scripts* pro 32bitovou verzi.

Enthought zápoje 1.1 a starší, jakož i Enthought Python distribuce (EPD), se neposkytuje symboly překladače a proto nejsou kompatibilní s ladění ve smíšeném režimu.
