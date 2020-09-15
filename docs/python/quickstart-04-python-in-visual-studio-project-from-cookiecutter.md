---
title: Rychlý Start – vytváření projektů v Pythonu pomocí Cookiecutter
description: V tomto rychlém startu vytvoříte projekt sady Visual Studio pro Python pomocí šablony Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 6868b4c581674c8015d30bf81f64f2ab24ea2ee0
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100732"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Rychlý Start: vytvoření projektu ze šablony Cookiecutter

Po [instalaci podpory Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md)je snadné vytvořit nový projekt ze šablony Cookiecutter, včetně mnoha publikovaných na GitHubu. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) poskytuje grafické uživatelské rozhraní pro zjišťování šablon, možností vstupní šablony a vytváření projektů a souborů. Je součástí sady Visual Studio 2017 nebo novější a lze ji nainstalovat samostatně v dřívějších verzích sady Visual Studio.

1. V tomto rychlém startu nejprve nainstalujte distribuci Pythonu Anaconda3, která obsahuje potřebné balíčky Python pro šablonu Cookiecutter, která se tady zobrazuje. Spusťte instalační program sady Visual Studio, vyberte **Upravit**, rozbalte možnosti pro **vývoj v Pythonu** na pravé straně a vyberte **Anaconda3** (buď 32 bitů, nebo 64 bitů). Všimněte si, že instalace může v závislosti na rychlosti Internetu trvat delší dobu, ale toto je nejjednodušší způsob, jak nainstalovat potřebné balíčky.

1. Spusťte Visual Studio.

1. Vyberte **soubor**  >  **Nový**  >  **z Cookiecutter**. Tento příkaz otevře okno v aplikaci Visual Studio, kde můžete procházet šablony.

    ![Nový projekt ze šablony Cookiecutter](media/projects-from-cookiecutter1.png)

1. Vyberte šablonu **Microsoft/Python-skriptu sklearn-klasifikátor-cookiecutter** a pak vyberte **Další**. (Proces může trvat několik minut při prvním použití konkrétní šablony, protože Visual Studio nainstaluje požadované balíčky Pythonu.)

1. V dalším kroku nastavte umístění pro nový projekt v poli **vytvořit do** a pak vyberte **vytvořit a otevřít projekt**.

    ![Druhý krok s použitím Cookiecutter, nastavení vlastností projektu](media/projects-from-cookiecutter2.png)

1. Po dokončení procesu se zobrazí zpráva, že se **úspěšně vytvořily soubory pomocí šablony...**. Projekt je otevřen v Průzkumník řešení automaticky.

1. Stiskněte klávesu **CTRL** + **F5** nebo vyberte **ladit**  >  **Spustit bez ladění** pro spuštění programu.

    ![Výstup projektu Python-skriptu sklearn-klasifikátor-cookiecutter šablony](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: práce s Pythonem v aplikaci Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také

- [Použití rozšíření Cookiecutter](using-python-cookiecutter-templates.md)
- [Ručně identifikovat existující interpret Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalace podpory Pythonu do sady Visual Studio 2015 a starší](installing-python-support-in-visual-studio.md)
- [Umístění instalace](installing-python-support-in-visual-studio.md#install-locations)
