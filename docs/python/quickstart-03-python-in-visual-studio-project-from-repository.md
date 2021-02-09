---
title: Rychlý Start – klonování úložiště kódu Pythonu
description: V tomto rychlém startu vytvoříte projekt Pythonu v aplikaci Visual Studio tak, že naklonujte úložiště Python koans pomocí sady Visual Studio Team Explorer.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 55db74b2b2882aac12ac1587c4e972e31f7dfe10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902398"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Rychlý Start: klonování úložiště kódu Pythonu v aplikaci Visual Studio

Po [instalaci podpory Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md)můžete přidat rozšíření GitHub pro Visual Studio. Rozšíření umožňuje snadno klonovat úložiště kódu Pythonu a vytvořit z něj projekt z integrovaného vývojového prostředí (IDE). Můžete vždycky klonovat úložiště na příkazovém řádku a pak s nimi pracovat v aplikaci Visual Studio.

## <a name="install-the-github-extension-for-visual-studio"></a>Instalace rozšíření GitHub pro Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Práce s GitHubem v aplikaci Visual Studio

1. Spusťte Visual Studio.

1. Výběrem **Zobrazit**  >  **Team Explorer** otevřete okno **Team Explorer** , ve kterém se můžete připojit k GitHubu nebo Azure Repos nebo klonovat úložiště. (Pokud se nezobrazí stránka **připojit** uvedená níže, vyberte ikonu plug-in na horním panelu nástrojů, která vás přesměruje na tuto stránku.)

    ![Okno Průzkumníka týmových oken zobrazující Azure Repos, GitHub a klonování úložiště](media/team-explorer.png)

1. V části **místní úložiště Git** vyberte příkaz **Clone** a potom `https://github.com/gregmalcolm/python_koans` do pole Adresa URL zadejte složku klonovaných souborů a vyberte tlačítko **klonování** .

    > [!Tip]
    > Složka, kterou zadáte v **Team Explorer** , je přesná složka pro příjem klonovaných souborů. Na rozdíl od `git clone` příkazu vytvoření klonu v **Team Explorer** nevytvoří automaticky podsložku s názvem úložiště.

1. Po dokončení klonování se název úložiště zobrazí v seznamu **místní úložiště Git** . Dvojím kliknutím na tento název přejdete na řídicí panel úložiště v **Team Explorer**.

1. V části **řešení** vyberte **Nový**.

    ![Okno Průzkumník týmových projektů, vytvoření nového projektu z klonu](media/team-explorer-new-project.png)

1. V dialogu **Nový projekt** , který se zobrazí, přejděte na **jazyk Pythonu** (nebo vyhledejte "Python"), vyberte **z existujícího kódu Pythonu**, zadejte název projektu, nastavte **umístění** na stejnou složku jako úložiště a vyberte **OK**. V průvodci, který se zobrazí, vyberte **Dokončit**.

1. V nabídce vyberte **Zobrazit**  >  **Průzkumník řešení** .

1. V **Průzkumník řešení** rozbalte uzel **python3** , klikněte pravým tlačítkem na **Contemplate_koans. py** a vyberte **nastavit jako spouštěcí soubor**. Tento krok informuje Visual Studio, který soubor má použít při spuštění projektu.

1. V nabídce vyberte vlastnosti **projektu**  >  **koans** , vyberte kartu **Obecné** a nastavte **pracovní adresář** na "python3". Tento krok je nezbytný, protože ve výchozím nastavení sada Visual Studio nastaví pracovní adresář na kořenový adresář projektu místo umístění spouštěcího souboru (*python3 \ contemplate_koans. py*, který můžete zobrazit také ve vlastnostech projektu). Programový kód vyhledá soubor *koans.txt* v pracovní složce, takže beze změny této hodnoty se zobrazí chyba za běhu.

    ![Nastavení pracovního adresáře pro projekt v Pythonu](media/projects-set-working-directory.png)

1. Stiskněte klávesu **CTRL** + **F5** nebo vyberte **ladit**  >  **Spustit bez ladění** pro spuštění programu. Pokud se zobrazí **FileNotFoundError** pro *koans.txt*, zkontrolujte nastavení pracovní adresář, jak je popsáno v předchozím kroku.

1. Po úspěšném spuštění programu se zobrazí chyba kontrolního výrazu na řádku 17 *python3/koans/about_asserts. py*. To je úmyslné: program je navržený tak, aby se v jazyce Python učí, že opravuje všechny úmyslné chyby. (V [Ruby koans](https://rubykoans.com/)najdete další podrobnosti, které nechte inspirovat Python koans.)

    ![První výstup z programu Python koans](media/koans-output.png)

1. Otevřete *python3/koans/about_asserts. py* tak, že na ni přejdete v **Průzkumník řešení** a dvakrát kliknete na soubor. Všimněte si, že ve výchozím nastavení se v editoru nezobrazí čísla řádků. Pokud to chcete změnit, vyberte  >  **Možnosti** nástroje, v dolní části dialogového okna vyberte **Zobrazit všechna nastavení** , přejděte na **text editoru**  >  **Python**  >  **Obecné** a vyberte **čísla řádků**:

    ![Zapnutí čísla řádku pro soubory Pythonu](media/options-general-line-numbers.png)

1. Opravte chybu tak, že změníte `False` argument na řádku 17 na `True` . Řádek by měl číst takto:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Spusťte program znovu. Pokud aplikace Visual Studio upozorňuje na chyby, odpovězte pomocí **Ano** a pokračujte v běhu kódu. Pak vidíte, že první ověření proběhlo úspěšně, a program se zastaví na dalším Koan. Pokračujte v opravování chyb a program tak, jak chcete.

> [!Important]
> V tomto rychlém startu jste vytvořili přímý klon *python_koans* úložiště na GitHubu. Takové úložiště je chráněno jeho autorem z přímých změn, takže pokus o potvrzení změn v úložišti se nezdaří. V praxi vývojáři místo toho roztáhnou takové úložiště na vlastní účet GitHubu, provedou změny a pak vytvoří žádosti o přijetí změn, které tyto změny odešlou do původního úložiště. Pokud máte vlastní rozvětvení, použijte místo původní adresy URL, kterou jste použili dříve, místo adresy URL původního úložiště.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: práce s Pythonem v aplikaci Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také

- [Ručně identifikovat existující interpret Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Jak nainstalovat podporu Pythonu v aplikaci Visual Studio ve Windows](installing-python-support-in-visual-studio.md)
- [Umístění instalace](installing-python-support-in-visual-studio.md#install-locations)
