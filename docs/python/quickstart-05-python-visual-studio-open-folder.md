---
title: Úvodní příručka – otevření složky s kódem Pythonu
description: V tomto rychlém startu otevřete a spustíte kód Pythonu ze složky bez použití projektu Visual Studio (pouze Visual Studio 2019).
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
ms.openlocfilehash: ab234d9482cf9cbab49c15167ea45aff9ac2c7e6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62431098"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Úvodní příručka: Otevření a spuštění kódu Pythonu ve složce

Po instalaci [podpory Pythonu ve Visual Studiu 2019](installing-python-support-in-visual-studio.md)je snadné spustit existující kód Pythonu ve Visual Studiu 2019 bez vytvoření projektu Visual Studia.

> [!Note]
> Visual Studio 2017 a starší vyžadují vytvoření projektu Visual Studio pro spuštění kódu Pythonu, který můžete snadno provést pomocí předdefinované šablony projektu. Viz [Úvodní příručka: Vytvoření projektu Pythonu z existujícího kódu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. Pro tento návod můžete použít libovolnou složku s kódem Pythonu, který se vám líbí. Chcete-li sledovat spolu s příkladem zde uvedené, klonovat gregmalcolm / python_koans `git clone https://github.com/gregmalcolm/python_koans` GitHub úložiště do počítače pomocí příkazu v příslušné složce.

1. Spusťte Visual Studio 2019 a ve startovním okně vyberte **Otevřít** v dolní části sloupce **Začínáme.** Případně, pokud již máte spuštěnou visual **File** > studio, vyberte místo toho příkaz**Otevřít** > **složku** souboru.

    ![Úvodní obrazovka sady Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Přejděte do složky obsahující kód Pythonu a pak **zvolte Vybrat složku**. Pokud používáte kód python_koans, nezapomeňte vybrat `python3` složku ve složce klonování.

    ![Dialogové okno Vybrat složku z příkazu Otevřít složku](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio zobrazí složku v **Průzkumníku řešení** v **takzvaném zobrazení složek**. Složky můžete rozbalit a sbalit pomocí šipek na levém okraji názvů složek:

    ![Ovládací prvky pro rozbalení a sbalení složek v Průzkumníku řešení](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Při otevírání složky Pythonu vytvoří Visual Studio několik skrytých složek pro správu nastavení souvisejících s projektem. Chcete-li zobrazit tyto složky (a další skryté soubory a složky, například složku *GIT),* vyberte tlačítko **Zobrazit všechny soubory** na panelu nástrojů:

    ![Zobrazení skrytých složek v Průzkumníku řešení](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Chcete-li spustit kód, musíte nejprve identifikovat spouštěcí nebo primární soubor programu. V příkladu uvedeném zde *contemplate-koans.py*spouštěcí soubor . Klepněte pravým tlačítkem myši na tento soubor a vyberte **příkaz Nastavit jako položku po spuštění**.

    ![Nastavení položky po spuštění v Průzkumníku řešení](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Pokud položka po spuštění není umístěna v kořenovém adresáři otevřené složky, musíte také přidat řádek do souboru JSON konfigurace spuštění, jak je popsáno v části [Nastavení pracovního adresáře](#set-a-working-directory).

1. Spusťte kód stisknutím **klávesy Ctrl**+**F5** nebo výběrem **možnosti Ladění** > **start bez ladění**. Můžete také vybrat tlačítko panelu nástrojů, které zobrazuje položku po spuštění s tlačítkem přehrávání, které spustí kód v ladicím programu sady Visual Studio. Ve všech případech Visual Studio zjistí, že vaše položka při spuštění je soubor Pythonu, takže automaticky spustí kód ve výchozím prostředí Pythonu. (Toto prostředí se zobrazí vpravo od položky po spuštění na panelu nástrojů.)

    ![Tlačítko spustit ladicí program panelu nástrojů](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Výstup programu se zobrazí v samostatném příkazovém okně:

    ![Výstupní okno pro spuštění kódu Pythonu](media/quickstart-open-folder/08-result-window.png)

1. Chcete-li spustit kód v jiném prostředí, vyberte toto prostředí z rozevíracího ovládacího prvku na panelu nástrojů a potom znovu spusťte položku po spuštění.

1. Chcete-li složku zavřít v **File** > sadě Visual Studio, vyberte příkaz nabídky**Zavřít složku** souboru.

## <a name="set-a-working-directory"></a>Nastavení pracovního adresáře

Ve výchozím nastavení visual studio spustí projekt Pythonu otevřený jako složku v kořenovém adresáři stejné složky. Kód v projektu však může předpokládat, že Python je spuštěn v podsložce. Předpokládejme například, že otevřete kořenovou složku úložiště python_koans a potom nastavíte soubor *python3/contemplate-koans.py* jako položku po spuštění. Pokud pak spustíte kód, zobrazí se chyba, že soubor *koans.txt* nebyl nalezen. K této chybě *dochází,* protože contemplate-koans.py předpokládá, že Python je spuštěn ve složce *python3* spíše než v kořenovém adresáři úložiště.

V takových případech musíte také přidat řádek do souboru JSON konfigurace spuštění a určit tak pracovní adresář:

1. Klepněte pravým tlačítkem myši na spouštěcí soubor Pythonu (*.py)* v **Průzkumníku řešení** a vyberte **Nastavení ladění a spuštění**.

    ![Příkaz Nastavení ladění a spuštění pro soubor Pythonu](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. V zobrazeném **dialogovém okně Vybrat ladicí program** vyberte **Výchozí** a pak zvolte **Vybrat**.

    ![Příkaz Nastavení ladění a spuštění pro soubor Pythonu](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Pokud nevidíte **výchozí** jako volbu, ujistěte se, že jste při výběru příkazu **Nastavení ladění a spuštění** klepněte pravým tlačítkem myši na soubor *Pythonu .py.* Visual Studio používá typ souboru k určení, zatímco ladicí možnosti pro zobrazení.

1. Visual Studio otevře soubor s názvem *launch.vs.json*, který je umístěn ve skryté složce *.vs.* Tento soubor popisuje ladicí kontext pro projekt. Chcete-li určit pracovní adresář, `"workingDirectory"`přidejte `"workingDirectory": "python3"` hodnotu pro , jako v příkladu python-koans:

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

1. Uložte soubor a znovu spusťte program, který nyní běží v zadané složce.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: Práce s Pythonem v Sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také

- [Úvodní příručka: Vytvoření projektu Pythonu z existujícího kódu](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Úvodní příručka: Vytvoření projektu Pythonu z úložiště](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Ruční identifikace existujícího interpretu Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
