---
title: Rychlý start – vytvoření projektu Pythonu pomocí šablony
description: V tomto rychlém startu vytvoříte projekt sady Visual Studio pro Python s pomocí integrovanou šablonu pro základní aplikaci Flask.
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
ms.openlocfilehash: c36fc6e10b196c3da4ba58ff047adab62345fa6f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066022"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Rychlý start: Vytvoření projektu Pythonu z šablony v sadě Visual Studio

Jakmile [nainstalována podpora Pythonu v sadě Visual Studio 2017](installing-python-support-in-visual-studio.md), je snadné vytvoření nového projektu Pythonu pomocí různých šablon. V tomto rychlém startu vytvoříte jednoduchou aplikaci Flask pomocí šablony. Výsledný projekt je podobný projekt můžete vytvořit ručně pomocí [rychlý start – vytvoření webové aplikace pomocí Flask](../ide/quickstart-python.md).

1. Spusťte Visual Studio 2017.

1. V horní nabídce zvolte **souboru** > **nový** > **projektu**, pak v **nový projekt** dialogové okno hledání "prázdná flask", vyberte **prázdný webový projekt Flask** šablony v seznamu v prostředním pojmenujte projekt a vyberte **OK**:

    ![Vytvoření nového projektu pomocí šablony prázdný webový projekt Flask](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio vás vyzve k se dialogové okno s upozorněním **tento projekt vyžaduje externí balíčky.** Tento dialog se zobrazuje, protože obsahuje šablony *souboru requirements.txt* souboru určení závislost na Flask. Visual Studio může automaticky nainstalovat balíčky a dá vám možnost nainstalovat je do *virtuální prostředí*. Použití virtuální prostředí se doporučuje instalací do globálního prostředí, takže vyberte **nainstalovat do virtuálního prostředí** pokračujte.

    ![Instalace Flask do virtuálního prostředí](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio zobrazí **přidat virtuální prostředí** dialogového okna. Přijměte výchozí nastavení a vyberte **vytvořit**, pak všechny požadavky na zvýšení oprávnění vyjádřit souhlas.

    > [!Tip]
    > Při zahájení projektu vysoce doporučuje se vytvořit virtuální prostředí hned, jak pozvat většina šablony sady Visual Studio, můžete s nimi dělat. Virtuální prostředí Údržba přesné požadavky na váš projekt v průběhu času, jak přidávat a odebírat knihovny. Potom můžete snadno generovat *souboru requirements.txt* soubor, který použijete k přeinstalaci těchto závislostí na jiných počítačích vývoje (jako při použití správy zdrojového kódu) a při nasazení projektu do provozního serveru. Další informace o virtuálních prostředí a jejich výhody, naleznete v tématu [použít virtuální prostředí](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) a [spravovat vyžadované balíčky pomocí souboru requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Poté, co Visual Studio vytvoří toto prostředí, podívejte se **Průzkumníka řešení** chcete zjistit, že máte *app.py* souboru spolu s *souboru requirements.txt*. Otevřít *app.py* zobrazíte, že šablona poskytuje kód, jako je například v [rychlý start – vytvoření webové aplikace pomocí Flask](../ide/quickstart-python.md), s několika přidání oddíly. Veškerý kód níže je vytvořený pomocí šablony, takže není nutné vložit některé do *app.py* sami.

    Kód začíná nezbytných importů:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Dále je následující řádek, který může být užitečné při nasazování aplikace na webového hostitele:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Potom pochází dekoratér trasy na jednoduchou funkci, která definuje zobrazení:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Nakonec spouštěcí kód uvedený níže můžete nastavit hostitele a port prostřednictvím proměnných prostředí nezadávejte napevno-je. Takový kód umožňuje snadno ovládat konfiguraci na počítačích pro vývoj i produkci beze změny kódu:

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

1. Vyberte **ladění** > **spustit bez ladění** ke spuštění aplikace a otevřete prohlížeč na `localhost:5555`.

**Otázka: Jaké další Python šablony sady Visual Studio nabízí?**

**Odpověď**: S úlohou Pythonu nainstalován, Visual Studio poskytuje celou řadu šablon projektů, včetně těch, které jsou pro [webové architektury Flask, Bottle a Django](../python/python-web-application-project-templates.md), cloudových služeb Azure, jiné strojové učení scénáře a dokonce i šablonu pro vytvoření projektu z existující strukturu složky obsahující aplikace v Pythonu. Přístup k těmto prostřednictvím **souboru** > **nový** > **projektu** dialogové okno tak, že vyberete **Python** uzel jazyka a jeho podřízených uzlů.

Visual Studio také poskytuje širokou škálu souboru nebo *šablon položek* k rychlému vytvoření třída Pythonu, balíček Pythonu, test jednotky Pythonu, *web.config* souborů a dalších. Pokud máte otevřen projekt Python, můžete přístup k šablony položek prostřednictvím **projektu** > **přidat novou položku** příkazu nabídky. Zobrazit [šablon položek](python-item-templates.md) odkaz.

Pomocí šablon můžete ušetřit významný čas, kdy spuštění projektu nebo vytvoření souboru a nabízeny jsou také skvělou možnost pro další informace o různých typů aplikací a kódu struktury. Je vhodné trvat několik minut, než vytváření projektů a položek z různých šablon se seznámit s co nabízejí.

**Otázka: Mohu také použít šablony Cookiecutter?**

**Odpověď**: Ano! Ve skutečnosti, Visual Studio poskytuje přímou integraci se Cookiecutter, které se dozvíte prostřednictvím [rychlý start: vytvoření projektu ze šablony Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: Práce s využitím Pythonu v sadě Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také:

- [Ručně identifikovat existující interpret Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalace podpory Pythonu v sadě Visual Studio 2015 a starší](installing-python-support-in-visual-studio.md)
- [Umístění instalace](installing-python-support-in-visual-studio.md#install-locations)
