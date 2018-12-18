---
title: Rychlý start – klonování úložiště kódu v Pythonu
description: V tomto rychlém startu vytvoříte projekt Python v sadě Visual Studio naklonováním úložiště koans Python pomocí Visual Studio Team Explorer.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 871a5f620cc90db5064562461336fdeac38ba757
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068390"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Rychlý start: Klonování úložiště kódu v Pythonu v sadě Visual Studio

Jakmile [nainstalována podpora Pythonu v sadě Visual Studio 2017](installing-python-support-in-visual-studio.md), můžete přidat rozšíření GitHub pro Visual Studio. Rozšíření vám umožní snadno naklonujte úložiště kódu v Pythonu a vytvoření projektu z něj z integrovaného vývojového prostředí. Můžete vždy klonovat úložiště na příkazovém řádku a potom s nimi pracovat v sadě Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Instalace rozšíření GitHub pro Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Práce s Githubem v sadě Visual Studio

1. Spusťte sadu Visual Studio.

1. Vyberte **zobrazení** > **Team Exploreru** otevřít **Team Exploreru** okno, ve kterém můžete připojit ke Githubu nebo úložiště Azure nebo klonování úložiště. (Pokud se nezobrazí **připojit** stránky zobrazené níže, vyberte ikonu moduly na horním panelu nástrojů, které vás přesměruje na tuto stránku.)

    ![Team explorer okno zobrazující úložišť Azure, Githubu a klonování úložiště](media/team-explorer.png)

1. V části **místní úložiště Git**, vyberte **klonování** příkazu, a pak zadejte `https://github.com/gregmalcolm/python_koans` do pole Adresa URL zadejte složky pro klonované soubory a vyberte **klonování** tlačítko.

    > [!Tip]
    > Vámi zadané v složky **Team Exploreru** je přesně složka pro příjem klonované soubory. Na rozdíl od `git clone` příkaz vytvoření klonu v **Team Exploreru** neprovádí automatické vytváření podsložku s názvem úložiště.

1. Po dokončení klonování se zobrazí název úložiště v **místní úložiště Git** seznamu. Dvakrát klikněte na tento název se přejděte do řídicího panelu úložiště v **Team Exploreru**.

1. V části **řešení**vyberte **nový**.

    ![Okno Průzkumníka týmu, vytvoření nového projektu z klonu](media/team-explorer-new-project.png)

1. V **nový projekt** dialogové okno, které se zobrazí, přejděte **Python** jazyk (nebo vyhledávání "Python"), vyberte **z existujícího kódu Pythonu**, zadejte název projektu, Nastavte **umístění** do stejné složky jako úložiště a vyberte **OK**. V průvodci, který se zobrazí, vyberte **Dokončit**.

1. Vyberte **zobrazení** > **Průzkumníka řešení** z nabídky.

1. V **Průzkumníka řešení**, rozbalte **pythonu3** uzel, klikněte pravým tlačítkem na **contemplate_koans.py**a vyberte **nastavit jako spouštěcí soubor**. Tento krok informuje soubor, který by měl použít při spuštění projektu sady Visual Studio.

1. Vyberte **projektu** > **Koans vlastnosti** nabídce, vyberte **Obecné** kartu a nastavte **pracovní adresář** na " pythonu3 ". Tento krok je nezbytný, protože ve výchozím nastavení sady Visual Studio nastaví pracovní adresář na kořen projektu namísto umístění spouštěcího souboru (*python3\contemplate_koans.py*, který se zobrazí ve vlastnostech projektu). Kód program vyhledá soubor *koans.txt* v pracovní složce tak beze změny tato hodnota se zobrazí chyba za běhu.

    ![Nastavení pracovní adresář pro projekt v Pythonu](media/projects-set-working-directory.png)

1. Stisknutím klávesy **Ctrl**+**F5** nebo vyberte **ladění** > **spustit bez ladění** ke spuštění programu. Pokud se zobrazí **FileNotFoundError** pro *koans.txt*, zkontrolujte pracovní adresář, nastavení, jak je popsáno v předchozím kroku.

1. Když se program spustí úspěšně, zobrazí chybu kontrolní výraz na řádku 17 *python3/koans/about_asserts.py*. Je to záměr: program navrženy tak, aby Python tím, že můžete opravit všechny úmyslné chyby. (Další podrobnosti se nachází na [Ruby Koans](https://rubykoans.com/), který která vychází z Pythonu Koans.)

    ![První výstup z programu koans Pythonu](media/koans-output.png)

1. Otevřít *python3/koans/about_asserts.py* tak, že přejdete na ni v **Průzkumníka řešení** a poklepáním na soubor. Všimněte si, že čísla řádků v editoru ve výchozím nastavení nezobrazí. Chcete-li toto nastavení změnit, vyberte **nástroje** > **možnosti**vyberte **zobrazit všechna nastavení** v dolní části dialogového okna, přejděte na **textový Editor**   >  **Python** > **Obecné** a vyberte **čísla řádků**:

    ![Zapnutí číslo řádku pro soubory Pythonu](media/options-general-line-numbers.png)

1. Opravte tuto chybu tak, že změníte `False` argument na řádek 17 `True`. Přečtěte si řádku takto:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Spusťte program znovu. Pokud aplikace Visual Studio vás varuje, o chybách, odpovědět **Ano** pokračoval kód. Pak uvidíte, že první proběhne a program se zastaví na další koan. Pokračovat v opravě chyby a program znovu, jak chcete.

> [!Important]
> V tomto rychlém startu jste vytvořili klon s přímým přístupem *python_koans* úložišti na Githubu. Taková úložiště je chráněn jeho autor z přímé změny, takže pokus o potvrzení změn do úložiště selže. V praxi vývojáři místo toho vytvořit fork úložiště do účtu Githubu, ujistěte se, že změny a vytvořte žádosti o přijetí změn k odeslání změn do původní úložiště. Až budete mít vlastní rozvětvení, použijte její adresu URL namísto původní adresu URL úložiště použili dříve.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: Práce s využitím Pythonu v sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také:

- [Ručně identifikovat existující interpret Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalace podpory Pythonu v sadě Visual Studio 2015 a starší](installing-python-support-in-visual-studio.md)
- [Umístění instalace](installing-python-support-in-visual-studio.md#install-locations)
