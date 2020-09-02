---
title: Rychlý Start – vytvoření projektu v Pythonu pomocí šablony
description: V tomto rychlém startu vytvoříte projekt sady Visual Studio pro Python pomocí předdefinované šablony pro aplikaci základní baňky.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429750"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Rychlý Start: vytvoření projektu v Pythonu ze šablony v aplikaci Visual Studio

Po [instalaci podpory Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md)je snadné vytvořit nový projekt v jazyce Python pomocí nejrůznějších šablon. V tomto rychlém startu vytvoříte jednoduchou aplikaci v baňce pomocí šablony. Výsledný projekt je podobný projektu, který vytvoříte ručně pomocí rychlého startu [– Vytvoření webové aplikace s použitím baňky](../ide/quickstart-python.md).

1. Spusťte Visual Studio.

1. V horním panelu nabídek zvolte **soubor**  >  **Nový**  >  **projekt**a potom v dialogovém okně **Nový projekt** vyhledejte "prázdná baňka", vyberte šablonu **webového projektu prázdné baňky** v prostředním seznamu, zadejte název projektu a vyberte **OK**:

    ![Vytvoření nového projektu pomocí šablony webového projektu prázdné baňky](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio vás vyzve k zadání dialogu, který říká, že **Tento projekt vyžaduje externí balíčky.** Toto dialogové okno se zobrazí, protože šablona obsahuje soubor *requirements.txt* určující závislost na baňce. Visual Studio může instalovat balíčky automaticky a poskytuje možnost jejich instalace do *virtuálního prostředí*. Při instalaci do globálního prostředí se doporučuje použít virtuální prostředí, takže pokračujte výběrem **nainstalovat do virtuálního prostředí** .

    ![Instalace baňky do virtuálního prostředí](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio zobrazí dialogové okno **Přidat virtuální prostředí** . Přijměte výchozí nastavení a vyberte **vytvořit**a pak vyjádřete souhlas s případnými žádostmi o zvýšení oprávnění.

    > [!Tip]
    > Když zahájíte projekt, důrazně doporučujeme vytvořit virtuální prostředí hned, protože se vám dá dělat většina šablon sady Visual Studio. Virtuální prostředí udržují přesné požadavky vašeho projektu v průběhu času při přidávání a odebírání knihoven. Pak můžete snadno vygenerovat *requirements.txt* soubor, který použijete k přeinstalaci těchto závislostí na jiné vývojové počítače (jako při použití správy zdrojového kódu) a při nasazení projektu na provozní server. Další informace o virtuálních prostředích a jejich výhodách najdete v tématu [použití virtuálních prostředí](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) a [Správa požadovaných balíčků pomocí requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Jakmile aplikace Visual Studio vytvoří toto prostředí, vyhledejte **Průzkumník řešení** a podívejte se, že máte soubor *app.py* spolu s *requirements.txt*. Otevřete *App.py* , abyste viděli, že šablona poskytovala kód jako v [rychlém startu – vytvořte webovou aplikaci s použitím baňky](../ide/quickstart-python.md)s několika přidanými oddíly. Všechny níže uvedené kódy jsou vytvořeny šablonou, takže je nemusíte vkládat do *App.py* sami.

    Kód začíná nezbytnými importy:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Dalším je následující řádek, který může být užitečný při nasazování aplikace na webového hostitele:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Pak je dekoratér směrování na jednoduchou funkci, která definuje zobrazení:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Nakonec vám spouštěcí kód umožňuje nastavit hostitele a port přes proměnné prostředí, a ne je pevně zakódovat. Takový kód vám umožňuje snadno řídit konfiguraci na vývojových i produkčních počítačích beze změny kódu:

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

1. Vyberte **ladit**  >  **Spustit bez ladění** , aby se spustila aplikace, a otevřete v prohlížeči prohlížeč `localhost:5555` .

**Otázka: Jaké další šablony Pythonu nabízí Visual Studio?**

**Odpověď**: s nainstalovanou úlohou Pythonu nabízí Visual Studio celou řadu šablon projektů, včetně těch, které se týkají [láhve, Django webových architektur](../python/python-web-application-project-templates.md), Azure Cloud Services, různých scénářů strojového učení a dokonce i šablony pro vytvoření projektu z existující struktury složek obsahující aplikaci v Pythonu. Přístup k nim provedete pomocí dialogového okna **soubor**  >  **Nový**  >  **projekt** výběrem uzlu jazyk **Pythonu** a jeho podřízených uzlů.

Sada Visual Studio také poskytuje celou řadu šablon souborů nebo *položek* k rychlému vytvoření třídy Pythonu, balíčku Pythonu, testu jednotek Pythonu, *web.config* souborů a dalších. Pokud máte otevřený projekt v jazyce Python, získáte přístup k šablonám položek **Project**pomocí  >  příkazu nabídky**Přidat novou položku** v projektu. Viz Referenční dokumentace k [šablonám položek](python-item-templates.md) .

Použití šablon vám může ušetřit značný čas při spuštění projektu nebo při vytváření souboru a je to skvělý způsob, jak se dozvědět o různých typech aplikací a struktur kódu. Vytváření projektů a položek z různých šablon je užitečné, pokud si chcete seznámit s tím, co nabízejí.

**Otázka: můžu také použít šablony Cookiecutter?**

**Odpověď**: Ano! Ve skutečnosti nabízí Visual Studio přímou integraci s Cookiecutter, na kterou si můžete přečíst v kurzu [rychlý Start: vytvoření projektu ze šablony Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurz: práce s Pythonem v aplikaci Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Viz také

- [Ručně identifikovat existující interpret Pythonu](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalace podpory Pythonu do sady Visual Studio 2015 a starší](installing-python-support-in-visual-studio.md)
- [Umístění instalace](installing-python-support-in-visual-studio.md#install-locations)
