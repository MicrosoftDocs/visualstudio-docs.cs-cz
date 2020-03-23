---
title: Úvodní příručka – Vytvoření projektu Pythonu pomocí šablony
description: V tomto rychlém startu vytvoříte projekt Sady Visual Studio pro Python pomocí předdefinované šablony pro základní aplikaci Flask.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 089be3e6f28a939979f6bd97097ea7558824b493
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62429750"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Úvodní příručka: Vytvoření projektu Pythonu ze šablony v Sadě Visual Studio

Po instalaci [podpory Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md)je snadné vytvořit nový projekt Pythonu pomocí různých šablon. V tomto rychlém startu vytvoříte jednoduchou aplikaci Flask pomocí šablony. Výsledný projekt je podobný projektu, který vytvoříte ručně pomocí [rychlého startu - Vytvoření webové aplikace s Flask](../ide/quickstart-python.md).

1. Spusťte Visual Studio.

1. V horním řádku nabídek zvolte **Soubor** > **nový** > **projekt**, pak v dialogovém okně Nový **projekt** vyhledejte "prázdnou baňku", vyberte šablonu **webového projektu Prázdná flask** ve středním seznamu, pojmenujte projekt a vyberte **OK**:

    ![Vytvoření nového projektu pomocí šablony webového projektu Blank Flask](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio zobrazí výzvu pomocí dialogového okna, které říká, že **tento projekt vyžaduje externí balíčky.** Toto dialogové okno se zobrazí, protože šablona obsahuje soubor *requirements.txt,* který určuje závislost na Flask. Visual Studio můžete nainstalovat balíčky automaticky a poskytuje možnost nainstalovat do *virtuálního prostředí*. Použití virtuálního prostředí se doporučuje přes instalaci do globálního prostředí, takže vyberte **Nainstalovat do virtuálního prostředí** pokračovat.

    ![Instalace baňky do virtuálního prostředí](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio zobrazí dialogové okno **Přidat virtuální prostředí.** Přijměte výchozí nastavení a vyberte **Vytvořit**a pak souhlaste s požadavky na zvýšení oprávnění.

    > [!Tip]
    > Když začnete projekt, důrazně doporučujeme vytvořit virtuální prostředí hned, jako většina šablon Sady Visual Studio vás pozvat k tomu. Virtuální prostředí udržovat přesné požadavky projektu v průběhu času při přidávání a odebírá knihovny. Potom můžete snadno vygenerovat soubor *requirements.txt,* který použijete k přeinstalaci těchto závislostí v jiných vývojových počítačích (jako při použití správy zdrojového kódu) a při nasazování projektu na produkční server. Další informace o virtuálních prostředích a jejich výhodách naleznete v [tématu Použití virtuálních prostředí](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) a [Správa požadovaných balíčků pomocí souboru requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Poté, co Visual Studio vytvoří toto prostředí, podívejte se do **Průzkumníka řešení** a zjistěte, zda máte *app.py* soubor spolu s *souborem requirements.txt*. Otevřete *app.py* a uvidíte, že šablona poskytla takový kód v [rychlém startu - Vytvořte webovou aplikaci s Flask](../ide/quickstart-python.md), s několika přidanými sekcemi. Celý níže uvedený kód je vytvořen šablonou, takže nemusíte vkládat do *app.py* sami.

    Kód začíná potřebnými importy:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Dále je následující řádek, který může být užitečný při nasazování aplikace do webového hostitele:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Pak přichází trasa decorator na jednoduchou funkci, která definuje zobrazení:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Nakonec níže uvedený spouštěcí kód umožňuje nastavit hostitele a port prostřednictvím proměnných prostředí, nikoli je pevně kódovat. Takový kód umožňuje snadno ovládat konfiguraci na vývoji i ve výrobních strojích bez změny kódu:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Chcete-li **aplikaci** > spustit a otevřít prohlížeč do `localhost:5555`aplikace , vyberte možnost Začít bez**ladění.**

**Otázka: Jaké další šablony Pythonu Visual Studio nabízí?**

**Odpověď**: S nainstalovanou úlohou Pythonu poskytuje Visual Studio celou řadu šablon projektů, včetně šablon pro [webové rámce Flask, Bottle a Django](../python/python-web-application-project-templates.md), cloudové služby Azure, různé scénáře strojového učení a dokonce i šablonu pro vytvoření projektu z existující struktury složek obsahující aplikaci Python. K nim se dostanete prostřednictvím dialogového okna Nový**New** > **projekt** **souboru** > výběrem jazykového uzlu **Pythonu** a jeho podřízených uzlů.

Visual Studio také poskytuje různé šablony souborů nebo položek pro rychlé vytvoření *třídy* Pythonu, balíčku Pythonu, testu částí Pythonu, souborů *web.config* a dalších. Když máte otevřený projekt Pythonu, získáte přístup k šablonám položek prostřednictvím příkazu nabídky Přidat**novou položku** **projektu.** >  Viz odkaz na [šablony položek.](python-item-templates.md)

Použití šablon vám může ušetřit značný čas při spuštění projektu nebo vytvoření souboru a jsou také skvělým způsobem, jak se dozvědět o různých typech aplikací a strukturách kódu. Je užitečné trvat několik minut k vytvoření projektů a položek z různých šablon, abyste se seznámili s tím, co nabízejí.

**Otázka: Mohu také použít Cookiecutter šablony?**

**Odpověď**: Ano! Ve skutečnosti Visual Studio poskytuje přímou integraci s Cookiecutter, které se můžete dozvědět o prostřednictvím [rychlého startu: Vytvoření projektu ze šablony Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: Práce s Pythonem v Sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také

- [Ruční identifikace existujícího interpretu Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalace podpory Pythonu ve Visual Studiu 2015 a starších](installing-python-support-in-visual-studio.md)
- [Instalace umístění](installing-python-support-in-visual-studio.md#install-locations)
