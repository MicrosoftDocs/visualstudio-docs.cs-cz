---
title: Symboly pro ladění ve smíšeném režimu Python/C++
description: Jak Visual Studio poskytuje možnost načíst symboly pro kompletní ladění v kombinovaném režimu C++ a Python.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 52eb7535430248f519654c09924541a6900336cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933086"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Nainstalovat symboly ladění pro překladače Pythonu

Aby bylo možné zajistit úplné ladění, potřebuje [ladicí program Pythonu ve smíšeném režimu](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) v aplikaci Visual Studio symboly ladění pro interpret Pythonu, který se používá k analýze mnoha vnitřních datových struktur. Pro *python27.dll* například odpovídající soubor symbolů je *python27. pdb*; pro *python36.dll* je soubor symbolů *python36. pdb*. Každá verze překladače také poskytuje soubory symbolů pro nejrůznější moduly.

V rámci sady Visual Studio 2017 nebo novější překladače Python 3 a Anaconda 3 automaticky instalují příslušné symboly a aplikace Visual Studio tyto symboly vyhledá automaticky. Pro Visual Studio 2015 a starší nebo při použití jiných překladačů je potřeba stáhnout symboly samostatně a pak na ně Ukázat Visual Studio pomocí   >  dialogového okna **Možnosti** nástrojů na   >  kartě **symboly** ladění. Tyto kroky jsou podrobně popsané v následujících částech.

Visual Studio vás může vyzvat, když potřebuje symboly, obvykle při spuštění relace ladění ve smíšeném režimu. V takovém případě se zobrazí dialogové okno se dvěma možnostmi:

- **Otevření dialogového okna nastavení symbolů** otevře dialogové okno **Možnosti** na   >  kartě **symboly** ladění.
- **Stáhnout symboly pro interpreta** otevře tuto současnou stránku dokumentace. v takovém případě vyberte   >  **Možnosti** nástrojů a přejděte na kartu   >  **symboly** ladění a pokračujte.

    ![Výzva k zobrazení symbolů ladicího programu ve smíšeném režimu](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Stáhnout symboly

- Python 3,5 a novější: Získejte symboly ladění prostřednictvím instalačního programu Pythonu. Vyberte možnost **vlastní instalace**, pro získání **pokročilých možností** vyberte **Další** a potom zaškrtněte políčka **stáhnout symboly ladění** a **stáhnout binární soubory ladění**:

    ![Instalační program Python 3. x včetně symbolů ladění](media/mixed-mode-debugging-symbols-installer35.png)

    Soubory symbolů (*PDB*) se pak nacházejí v kořenové instalační složce (soubory symbolů pro jednotlivé moduly jsou také ve složce *DLL* ). Z tohoto důvodu je Visual Studio automaticky vyhledává a nejsou potřeba žádné další kroky.

- Python 3.4. x a starší: symboly jsou k dispozici jako soubory ke stažení s *příponou. zip* z [oficiálních distribucí](#official-distributions) nebo [Enthought zápoje](#enthought-canopy). Po stažení souborů rozbalte soubory do místní složky, aby bylo možné pokračovat, jako je například složka *symbolů* ve složce Python.

    > [!Important]
    > Symboly se liší mezi vedlejšími sestaveními Pythonu a mezi 32 a 64 sestaveními, takže chcete přesně odpovídat verzi. Chcete-li zjistit, který překladač se používá, rozbalte *uzel* **prostředí Pythonu** pod projektem v **Průzkumník řešení** a poznamenejte si název prostředí. Pak přepněte do okna **prostředí Pythonu**  a poznamenejte si umístění instalace. Pak otevřete příkazové okno v tomto umístění a spusťte *python.exe*, které zobrazuje přesnou verzi a zda je 32 nebo 64-bit.

- Pro všechny ostatní distribuce Pythonu třetích stran, jako je ActiveState Python: kontaktujte autory této distribuce a požádejte je, aby vám poskytli symboly. WinPython v rámci své součásti zahrnuje standardní interpret Pythonu beze změn, takže pro odpovídající číslo verze použijte symboly z oficiální distribuce.

## <a name="point-visual-studio-to-the-symbols"></a>Ukázat aplikaci Visual Studio na symboly

Pokud jste stáhli symboly samostatně, postupujte podle následujících kroků, abyste je měli v programu Visual Studio. Pokud jste nainstalovali symboly prostřednictvím instalačního programu Python 3,5 nebo novějšího, Visual Studio je automaticky najde.

1. Vyberte nabídku   >  **Možnosti** nástrojů a přejděte na symboly **ladění**  >  .

1. Na panelu nástrojů vyberte tlačítko **Přidat** (viz níže), zadejte složku, do které jste rozšířili stažené symboly (kde se nachází soubor *Python. pdb* , například *c:\python34\Symbols*, viz níže), a vyberte **OK**.

    ![Možnosti ladění symbolů ladicího programu ve smíšeném režimu](media/mixed-mode-debugging-symbols.png)

1. Během relace ladění může Visual Studio také vyzvat k umístění zdrojového souboru pro interpret Pythonu. Pokud jste stáhli zdrojové soubory (například z [Python.org/downloads/](https://www.python.org/downloads/)), můžete samozřejmě nasměrovat i na ně.

> [!Note]
> Funkce ukládání symbolů do mezipaměti zobrazené v dialogovém okně slouží k vytvoření místní mezipaměti symbolů získaných z online zdroje. Tyto funkce nejsou nutné se symboly překladače Pythonu, protože symboly jsou již přítomny lokálně. V každém případě se podrobnosti zobrazí v [ladicím programu sady Visual Studio pro zadání symbolů a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .

## <a name="official-distributions"></a>Oficiální distribuce

| Python version (Verze Pythonu) | Soubory ke stažení |
| --- | --- |
| 3,5 a novější | Nainstalujte symboly prostřednictvím instalačního programu Pythonu. |
| 3.4.4 | [32 – bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 – bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 – bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 – bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 – bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 – bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 – bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| body | [32 – bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 – bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 – bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 – bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32 – bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32 – bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32 – bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32 – bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32 – bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 – bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 – bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 – bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 – bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 – bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 – bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 – bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 – bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 – bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 – bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip)  -  [64 – bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought zápoje

Enthought zápoje poskytuje symboly pro své binární soubory od verze 1,2. Automaticky se instalují spolu s distribucí, ale stále musíte ručně přidat složku, která je obsahuje, do cesty k symbolu, jak je popsáno výše. Pro typickou instalaci zápoje pro jednotlivé uživatele se symboly nacházejí v *%USERPROFILE%\AppData\Local\Enthought\Canopy\User\Scripts* pro 64 verze a *%USERPROFILE%\AppData\Local\Enthought\Canopy32\User\Scripts* pro 32 verzi.

Enthought zápoje 1,1 a starší, stejně jako Enthought pro distribuci Pythonu (EPD), neposkytují symboly překladače a nejsou proto kompatibilní s laděním ve smíšeném režimu.
