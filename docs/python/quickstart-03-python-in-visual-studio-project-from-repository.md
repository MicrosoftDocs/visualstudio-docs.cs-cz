---
title: Úvodní příručka – klonování úložiště kódu Pythonu
description: V tomto rychlém startu vytvoříte projekt Pythonu v sadě Visual Studio klonováním úložiště Python koans pomocí Průzkumníka týmu Visual Studio.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5d0363626748588b6f4058e197f0d6796ece51ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "64543139"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Úvodní příručka: Klonování úložiště kódu Pythonu v sadě Visual Studio

Po instalaci [podpory Pythonu ve Visual Studiu](installing-python-support-in-visual-studio.md)můžete přidat rozšíření GitHub pro Visual Studio. Rozšíření umožňuje snadno klonovat úložiště kódu Pythonu a vytvořit z něj projekt z ide. Úložiště můžete vždy klonovat také na příkazovém řádku a pak s nimi pracovat v sadě Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Instalace rozšíření GitHub pro Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Práce s GitHubem ve Visual Studiu

1. Spusťte Visual Studio.

1. Vyberte **Zobrazit** > **Průzkumníka týmu,** chcete-li otevřít okno **Průzkumníka týmu,** ve kterém se můžete připojit k GitHubu nebo Azure Repos, nebo naklonovat úložiště. (Pokud níže zobrazenou stránku **Připojit** nevidíte, vyberte ikonu plug na horním panelu nástrojů, která vás přenese na tuto stránku.)

    ![Okno průzkumníka týmu zobrazující Azure Repos, GitHub a klonování úložiště](media/team-explorer.png)

1. V **části Local Git Repositories**vyberte příkaz **Klonování,** zadejte do `https://github.com/gregmalcolm/python_koans` pole URL, zadejte složku pro klonované soubory a vyberte tlačítko **Klonování.**

    > [!Tip]
    > Složka zadaná v **Průzkumníkovi týmu** je přesná složka pro příjem klonovaných souborů. Na `git clone` rozdíl od příkazu vytvoření klonu v **Průzkumníkovi týmu** automaticky nevytvoří podsložku s názvem úložiště.

1. Po dokončení klonování se název úložiště zobrazí v seznamu **Místní úložiště Git.** Poklepáním na tento název přejděte na řídicí panel úložiště v **Průzkumníkovi týmu**.

1. V části **Řešení**vyberte **Nový**.

    ![Okno průzkumníka týmu, vytvoření nového projektu z klonu](media/team-explorer-new-project.png)

1. V dialogovém okně **Nový projekt,** které se zobrazí, přejděte do jazyka **Pythonu** (nebo hledat v "Pythonu"), vyberte **Z existujícího kódu Pythonu**, zadejte název projektu, nastavte **umístění** do stejné složky jako úložiště a vyberte **OK**. V průvodci, který se zobrazí, vyberte **dokončit**.

1. V nabídce vyberte **Zobrazit** > **Průzkumníka řešení.**

1. V **Průzkumníku řešení**rozbalte uzel **python3,** klepněte pravým tlačítkem myši na **soubor contemplate_koans.py**a vyberte **nastavit jako spouštěcí soubor**. Tento krok informuje visual studio, který soubor by měl použít při spuštění projektu.

1. V yberte **Vlastnosti projektu** > **Koans** v nabídce, vyberte kartu **Obecné** a nastavte **pracovní adresář** na "python3". Tento krok je nezbytný, protože ve výchozím nastavení sada Visual Studio nastaví pracovní adresář do kořenového adresáře projektu, nikoli na umístění spouštěcího souboru (*python3\contemplate_koans.py*, který můžete vidět také ve vlastnostech projektu). Kód programu hledá soubor *koans.txt* v pracovní složce, takže bezzměny této hodnoty se zobrazí chyba za běhu.

    ![Nastavení pracovního adresáře pro projekt Pythonu](media/projects-set-working-directory.png)

1. Stisknutím **klávesy Ctrl**+**F5** nebo stisknutím **možnosti Ladění** > **start bez ladění** program spusťte. Pokud se u souboru **FileNotFoundError** zobrazí *soubor koans.txt*, zkontrolujte nastavení pracovního adresáře, jak je popsáno v předchozím kroku.

1. Po úspěšném spuštění programu se na řádku 17 *python3/koans/about_asserts.py*zobrazí chyba kontrolního výrazu. To je úmyslné: program je navržen tak, aby učil Python tím, že vás opravit všechny úmyslné chyby. (Další podrobnosti naleznete na [Ruby Koans](https://rubykoans.com/), která inspirovala Python Koans.)

    ![První výstup z programu Python koans](media/koans-output.png)

1. Otevřete *python3/koans/about_asserts.py* tak, že na něj přejdete v **Průzkumníku řešení** a poklikáte na soubor. Všimněte si, že čísla řádků se ve výchozím nastavení v editoru nezobrazují. Chcete-li to změnit, vyberte**Možnosti** **nástrojů** > , vyberte **Zobrazit všechna nastavení** v dolní části dialogového okna, přejděte do **obecného editoru** > **textu pythonu** > **General** a vyberte **čísla řádků**:

    ![Zapnutí čísla řádku pro soubory Pythonu](media/options-general-line-numbers.png)

1. Opravte chybu změnou argumentu `False` na `True`řádku 17 na . Řádek by měl znít takto:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Spusťte program znovu. Pokud visual studio vás upozorní na chyby, odpovězte **ano,** chcete-li pokračovat ve spuštění kódu. Pak uvidíte, že první kontrola projde a program se zastaví na další koan. Pokračujte v opravách chyb a programu znovu, jak chcete.

> [!Important]
> V tomto rychlém startu jste vytvořili přímý klon *úložiště python_koans* na GitHubu. Takové úložiště je chráněno svým autorem před přímými změnami, takže pokus o potvrzení změn v úložišti se nezdaří. V praxi vývojáři místo toho rozvinout takové úložiště na svůj vlastní účet GitHub, provést změny tam a potom vytvořit žádosti o přijetí změn k odeslání těchto změn do původního úložiště. Pokud máte vlastní rozvinku, použijte její adresu URL namísto původní adresy URL úložiště, která byla použita dříve.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: Práce s Pythonem v Sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také

- [Ruční identifikace existujícího interpretu Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Jak nainstalovat podporu Pythonu v Sadě Visual Studio ve Windows](installing-python-support-in-visual-studio.md)
- [Instalace umístění](installing-python-support-in-visual-studio.md#install-locations)
