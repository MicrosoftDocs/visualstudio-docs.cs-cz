---
title: Rychlý start – vytvoření projektu Pythonu pomocí Cookiecutter
description: V tomto rychlém startu vytvoříte projekt sady Visual Studio pro Python s pomocí šablon Cookiecutter.
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
ms.openlocfilehash: b8ad6d53a337e6a2a0d879ff9637156fb3d6d791
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062700"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Rychlý start: Vytvoření projektu ze šablony Cookiecutter

Jakmile [nainstalována podpora Pythonu v sadě Visual Studio 2017](installing-python-support-in-visual-studio.md), je snadné vytvořit nový projekt ze šablony Cookiecutter, včetně množství, které se publikují do Githubu. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) poskytuje grafické uživatelské rozhraní pro zjišťování šablony, zadejte možnosti šablony a vytváření projektů a souborů. Je součástí sady Visual Studio 2017 a je možné nainstalovat odděleně v dřívějších verzích sady Visual Studio.

1. Pro účely tohoto rychlého startu nejprve nainstalujte distribuční Anaconda3 Python, který obsahuje potřebné balíčky Pythonu pro šablony Cookiecutter je vidět tady. Spusťte instalační program sady Visual Studio, vyberte **změnit**, rozbalte možnosti pro **vývoj v jazyce Python** na pravé straně a vyberte **Anaconda3** (32bitová nebo 64bitová verze). Všimněte si, že instalace může trvat delší dobu v závislosti na rychlosti Internetu, ale toto je nejjednodušší způsob, jak nainstalovat potřebné balíčky.

1. Spusťte sadu Visual Studio.

1. Vyberte **souboru** > **nové** > **z Cookiecutter**. Tento příkaz otevře okno v sadě Visual Studio, kde můžou Procházet šablony. 

    ![Nový projekt ze šablony Cookiecutter](media/projects-from-cookiecutter1.png)

1. Vybrané **Microsoft/python-skriptu sklearn třídění cookiecutter** šablony, pak vyberte **Další**. (Procesu může trvat několik minut, než poprvé použijete Cookiecutter.)

1. V dalším kroku, nastavit umístění nového projektu v **vytvořit do** pole a pak vyberte **vytvořit**.

    ![Druhý krok pomocí Cookiecutter, nastavení vlastností projektu](media/projects-from-cookiecutter2.png)

1. Po dokončení procesu se zobrazí zpráva **soubory se úspěšně vytvořil.** Vyberte příkaz **v Průzkumníku řešení otevřete** pro otevření projektu.

1. Stisknutím klávesy **Ctrl**+**F5** nebo vyberte **ladění** > **spustit bez ladění** ke spuštění programu. 

    ![Výstup projektu šablony python skriptu sklearn třídění cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: Práce s využitím Pythonu v sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také:

- [Použití rozšíření Cookiecutter](using-python-cookiecutter-templates.md)
- [Ručně identifikovat existující interpret Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalace podpory Pythonu v sadě Visual Studio 2015 a starší](installing-python-support-in-visual-studio.md)
- [Umístění instalace](installing-python-support-in-visual-studio.md#install-locations)
