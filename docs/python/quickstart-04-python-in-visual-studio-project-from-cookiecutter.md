---
title: Úvodní příručka - Vytvoření projektu Pythonu pomocí cookiecutteru
description: V tomto rychlém startu vytvoříte projekt sady Visual Studio pro Python pomocí šablony Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f3e7f56f4a36a7958cba9bd7092f38d735123d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62954488"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Úvodní příručka: Vytvoření projektu ze šablony Cookiecutter

Po instalaci [podpory Pythonu ve Visual Studiu](installing-python-support-in-visual-studio.md)je snadné vytvořit nový projekt ze šablony Cookiecutter, včetně mnoha publikovaných na GitHubu. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) poskytuje grafické uživatelské rozhraní pro objevování šablon, možnosti vstupních šablon a vytváření projektů a souborů. Je součástí Sady Visual Studio 2017 a novější a lze ji nainstalovat samostatně v dřívějších verzích sady Visual Studio.

1. Pro tento rychlý start nejprve nainstalujte distribuci Anaconda3 Python, která obsahuje potřebné balíčky Pythonu pro šablonu Cookiecutter, která je zde zobrazena. Spusťte instalační program Sady Visual Studio, vyberte **Změnit**, rozbalte možnosti **pro vývoj Pythonu** na pravé straně a vyberte **Anaconda3** (32bitový nebo 64bitový). Všimněte si, že instalace může nějakou dobu trvat v závislosti na rychlosti internetu, ale toto je nejjednodušší způsob instalace potřebných balíčků.

1. Spusťte Visual Studio.

1. Vyberte **možnost Nový** > **New** > soubor**z cookiecutteru**. Tento příkaz otevře okno v sadě Visual Studio, kde můžete procházet šablony.

    ![Nový projekt z Cookiecutter šablony](media/projects-from-cookiecutter1.png)

1. Byla vybrána šablona **Microsoft/python-sklearn-classifier-cookiecutter** a pak vyberte **další**. (Proces může trvat několik minut při prvním použití určité šablony, protože Visual Studio nainstaluje požadované balíčky Pythonu.)

1. V dalším kroku nastavte umístění nového projektu v poli **Vytvořit do** a pak vyberte Vytvořit a **otevřít projekt**.

    ![Druhý krok pomocí Cookiecutter, nastavení vlastností projektu](media/projects-from-cookiecutter2.png)

1. Po dokončení procesu se zobrazí zpráva **Úspěšně vytvořené soubory pomocí šablony...**. Projekt se otevře v Průzkumníku řešení automaticky.

1. Stisknutím **klávesy Ctrl**+**F5** nebo stisknutím **možnosti Ladění** > **start bez ladění** program spusťte.

    ![Výstup projektu šablony python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: Práce s Pythonem v Sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také

- [Použití rozšíření Cookiecutter](using-python-cookiecutter-templates.md)
- [Ruční identifikace existujícího interpretu Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalace podpory Pythonu ve Visual Studiu 2015 a starších](installing-python-support-in-visual-studio.md)
- [Instalace umístění](installing-python-support-in-visual-studio.md#install-locations)
