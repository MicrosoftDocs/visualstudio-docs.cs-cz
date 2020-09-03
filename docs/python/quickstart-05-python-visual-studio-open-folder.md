---
title: Rychlý Start – otevření složky kódu Pythonu
description: V tomto rychlém startu otevřete a spustíte kód Pythonu ze složky bez použití projektu sady Visual Studio (pouze Visual Studio 2019).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: a7bf174191a6a2fb013aa3d25880b01bc2e7f070
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801669"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Rychlý Start: otevření a spuštění kódu Pythonu ve složce

Po [instalaci podpory Pythonu v aplikaci Visual studio 2019](installing-python-support-in-visual-studio.md)je snadné spustit existující kód Pythonu v aplikaci visual Studio 2019 bez vytvoření projektu sady Visual Studio.

> [!Note]
> Visual Studio 2017 a starší vyžaduje vytvoření projektu sady Visual Studio pro spuštění kódu Pythonu, který můžete snadno použít integrovanou šablonu projektu. Viz [rychlý Start: vytvoření projektu v Pythonu z existujícího kódu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. Pro tento návod můžete použít libovolnou složku s kódem Pythonu, který chcete. Pokud chcete postupovat podle uvedeného příkladu, naklonujte úložiště GitHub gregmalcolm/python_koans do počítače pomocí příkazu `git clone https://github.com/gregmalcolm/python_koans` v příslušné složce.

1. Spusťte sadu Visual Studio 2019 a v okně Start vyberte **otevřít** ve spodní části sloupce **Začínáme** . Případně, pokud již máte spuštěnou aplikaci Visual Studio, vyberte **File**  >  **Open**  >  místo toho příkaz Otevřít**složku** pro otevření souboru.

    ![Úvodní obrazovka sady Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Přejděte do složky, která obsahuje kód Pythonu, a pak zvolte **Vybrat složku**. Pokud používáte python_koans kód, ujistěte se, že jste vybrali `python3` složku ve složce klonování.

    ![Dialogové okno vybrat složku z příkazu otevřít složku](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio zobrazí složku v **Průzkumník řešení** v zobrazení s názvem **složky**. Složky můžete rozbalit a sbalit pomocí šipek na levém okraji názvů složek:

    ![Ovládací prvky pro rozbalení a sbalení složek v Průzkumník řešení](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Při otevírání složky Python vytvoří Visual Studio několik skrytých složek pro správu nastavení souvisejících s projektem. Chcete-li zobrazit tyto složky (a všechny ostatní skryté soubory a složky, jako je například složka *. Git* ), vyberte tlačítko **Zobrazit všechny soubory** na panelu nástrojů:

    ![Zobrazení skrytých složek v Průzkumník řešení](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Chcete-li spustit kód, musíte nejprve určit spouštěcí nebo primární soubor programu. V následujícím příkladu se zobrazí spouštěcí soubor *contemplate-koans.py*. Klikněte pravým tlačítkem na tento soubor a vyberte **nastavit jako položku při spuštění**.

    ![Nastavení položky po spuštění v Průzkumník řešení](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Pokud se položka po spuštění nenachází v kořenu složky, kterou jste otevřeli, musíte do souboru JSON konfigurace spuštění přidat řádek, jak je popsáno v části, [Nastavení pracovního adresáře](#set-a-working-directory).

1. Spusťte kód stisknutím **klávesy CTRL** + **F5** nebo výběrem možnosti **ladit**  >  **Spustit bez ladění**. Můžete také vybrat tlačítko panelu nástrojů, které zobrazuje položku po spuštění, pomocí tlačítka Přehrát, které spouští kód v ladicím programu sady Visual Studio. Ve všech případech Visual Studio zjistí, že položka po spuštění je soubor Pythonu, takže automaticky spustí kód ve výchozím prostředí Pythonu. (Toto prostředí se zobrazuje napravo od položky po spuštění na panelu nástrojů.)

    ![Spustit ladicí program – tlačítko panelu nástrojů](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Výstup programu se zobrazí v samostatném příkazovém okně:

    ![Okno výstup pro spuštění kódu Pythonu](media/quickstart-open-folder/08-result-window.png)

1. Chcete-li spustit kód v jiném prostředí, vyberte toto prostředí z rozevíracího seznamu na panelu nástrojů a pak znovu spusťte položku po spuštění.

1. Chcete-li složku Zavřít v aplikaci Visual Studio, **File**vyberte  >  příkaz nabídky**Zavřít složku** souboru.

## <a name="set-a-working-directory"></a>Nastavení pracovního adresáře

Ve výchozím nastavení Visual Studio spustí projekt Pythonu, který se otevřel jako složka v kořenovém adresáři stejné složky. Kód ve vašem projektu ale může předpokládat, že se Python spouští v podsložce. Předpokládejme například, že otevřete kořenovou složku úložiště python_koans a potom nastavíte soubor *python3/koans. py* jako položku po spuštění. Pokud potom kód spustíte, zobrazí se chyba, že soubor *koans.txt* nebyl nalezen. K této chybě dochází, protože *contemplate-koans.py* předpokládá, že se Python spouští ve složce *python3* a ne v kořenovém adresáři úložiště.

V takových případech musíte přidat řádek do konfiguračního souboru JSON ke spuštění a zadat pracovní adresář:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na spouštěcí soubor Pythonu (*. py*) a vyberte **nastavení ladění a spouštění**.

    ![Příkaz Nastavení ladění a spuštění pro soubor Pythonu](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. V zobrazeném dialogovém okně **Vybrat ladicí program** vyberte **výchozí** a pak zvolte **Vybrat**.

    ![Příkaz Nastavení ladění a spuštění pro soubor Pythonu](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Pokud se možnost **výchozí** nezobrazuje jako volba, ujistěte se, že při výběru příkazu **ladit a spustit nastavení** jste zvolili soubor Python *. py* . Visual Studio používá typ souboru k určení možností ladicího programu, které se mají zobrazit.

1. Sada Visual Studio otevře soubor s názvem *launch.vs.jsna*, který je umístěn ve skryté složce *. vs* . Tento soubor popisuje kontext ladění pro projekt. Pokud chcete zadat pracovní adresář, přidejte hodnotu pro `"workingDirectory"` , jako v  `"workingDirectory": "python3"` pro Python – koans příklad:

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Uložte soubor a znovu spusťte program, který se teď spustí v zadané složce.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: práce s Pythonem v aplikaci Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také

- [Rychlý Start: vytvoření projektu v Pythonu z existujícího kódu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Rychlý Start: vytvoření projektu v Pythonu z úložiště](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Ručně identifikovat existující interpret Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
