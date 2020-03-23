---
title: Python v kurzu Visual Studia krok 5, instalace balíčků
titleSuffix: ''
description: Krok 5 základního návodu možností Pythonu v sadě Visual Studio, který demonstruje funkce Visual Studia pro správu balíčků v prostředí Pythonu.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372906"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Krok 5: Instalace balíčků v prostředí Pythonu

**Předchozí krok: [Spuštění kódu v ladicím programu](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Komunita vývojářů Pythonu vytvořila tisíce užitečných balíčků, které můžete začlenit do vlastních projektů. Visual Studio poskytuje ui pro správu balíčků v prostředí Pythonu.

## <a name="view-environments"></a>Zobrazení prostředí

1. Vyberte příkaz **Zobrazit** > **další** > prostředí Windows**Pythonu.** Okno **Prostředí Pythonu** se otevře jako partner **Průzkumníka řešení** a zobrazí různá prostředí, která máte k dispozici. Seznam zobrazuje obě prostředí, která jste nainstalovali pomocí instalačního programu sady Visual Studio, i prostředí, která jste nainstalovali samostatně. To zahrnuje globální, virtuální a conda prostředí. Prostředí tučně je výchozí prostředí, které se používá pro nové projekty. Další informace o práci s prostředími najdete v tématu [Jak vytvořit a spravovat prostředí Pythonu v prostředích Sady Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Okno Prostředí Pythonu](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Okno Prostředí Pythonu můžete otevřít také kliknutím na okno Průzkumník řešení a pomocí klávesové zkratky Ctrl+K, Ctrl+'. Pokud zástupce nefunguje a nemůžete najít okno Prostředí Pythonu v nabídce, je možné, že jste nenainstalovali zatížení Pythonu. Pokyny k instalaci Pythonu najdete v tématu [Jak nainstalovat podporu Pythonu ve Visual Studiu.](installing-python-support-in-visual-studio.md)

2. Karta **Přehled** prostředí poskytuje rychlý přístup k **interaktivnímu** oknu pro toto prostředí spolu s instalační složkou prostředí a interprety. Vyberte například **otevřít interaktivní okno** a **interaktivní** okno pro dané konkrétní prostředí se zobrazí v sadě Visual Studio.

3. Nyní vytvořte nový projekt s **file** > **new** > **project**a vyberte šablonu aplikace **Pythonu.** V souboru kódu, který se zobrazí, vložte následující kód, který vytvoří kosinusovou vlnu jako předchozí kroky kurzu, pouze tentokrát vykreslen graficky. Případně můžete použít projekt, který jste dříve vytvořili, a nahradit kód. 

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

4. S otevřeným projektem Pythonu můžete také otevřít okno Prostředí Pythonu z Průzkumníka řešení kliknutím pravým tlačítkem myši na prostředí Pythonu a výběrem **možnosti Zobrazit všechna prostředí Pythonu**

   ![Prostředí](media/environments/environments-view-all-2019.png)

5. Při pohledu na okno editoru si všimnete, `numpy` `matplotlib` že pokud najedete na příkazy importu a importu, které nejsou vyřešeny. Je to proto, že balíčky nebyly nainstalovány do výchozího globálního prostředí.

   ![Nevyřešený import balíčku](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Instalace balíčků pomocí okna Prostředí Pythonu

1. V okně Prostředí Pythonu klikněte na výchozí prostředí pro nové projekty Pythonu a vyberte kartu **Balíčky.** Zobrazí se seznam balíčků, které jsou aktuálně nainstalovány v prostředí.

   ![Balíčky instalované v prostředí](media/environments/environments-installed-packages-2019.png)

2. Nainstalujte `matplotlib` zadáním jeho názvu do vyhledávacího pole a výběrem **příkazu Spustit: pip install matplotlib.** To bude `matplotlib`instalovat , stejně jako všechny balíčky, `numpy`na kterých závisí (v tomto případě, který zahrnuje ).

   ![Instalace matplotlib v prostředí](media/environments/environments-add-matplotlib-2019.png)

5. Souhlas s nadezíním, pokud k tomu budete vyzváni.

6. Po instalaci balíčku se zobrazí v okně **Prostředí Pythonu.** **X** napravé straně balíčku odinstaluje.

   ![Dokončení instalace matplotlib v prostředí](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Pod prostředím se může zobrazit malý indikátor průběhu, který označuje, že visual studio vytváří svou databázi IntelliSense pro nově nainstalovaný balíček. Karta **IntelliSense** také zobrazuje podrobnější informace. Uvědomte si, že dokud nebude tato databáze dokončena, funkce Technologie IntelliSense, jako je automatické dokončování a kontrola syntaxe, nebudou v editoru pro tento balíček aktivní.
   > 
   > Visual Studio 2017 verze 15.6 a novější používá jinou a rychlejší metodu pro práci s IntelliSense a zobrazí zprávu s tímto účinkem na kartě **IntelliSense.**

## <a name="run-the-program"></a>Spuštění programu

1. Nyní, když je nainstalován [matplotlib,](https://matplotlib.org/) spusťte program s (**F5**) nebo bez ladicího programu (**Ctrl**+**F5**) pro zobrazení výstupu:

   ![Výstup příkladu matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Práce s Gitem](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Prostředí Pythonu](managing-python-environments-in-visual-studio.md)
- [Jak používat Django v sadě Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Jak používat Flask v sadě Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
