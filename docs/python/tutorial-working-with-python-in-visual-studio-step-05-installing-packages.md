---
title: Python v aplikaci Visual Studio – Krok 5, instalace balíčků
titleSuffix: ''
description: Krok 5 základního návodu k funkcím Pythonu v aplikaci Visual Studio, které demonstrují funkce sady Visual Studio pro správu balíčků v prostředí Pythonu.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 32e85f39c4acf9466def24bcfea59bbfd6807a1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801656"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Krok 5: Instalace balíčků do prostředí Pythonu

**Předchozí krok: [spuštění kódu v ladicím programu](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Komunita vývojářů v Pythonu vytvořila tisíce užitečných balíčků, které můžete začlenit do svých vlastních projektů. Visual Studio poskytuje uživatelské rozhraní pro správu balíčků v prostředích Pythonu.

## <a name="view-environments"></a>Zobrazení prostředí

1. Vyberte příkaz nabídky **Zobrazit**  >  **Další**  >  **prostředí Windows Python** . Okno **prostředí Pythonu** se otevře jako partnerský uzel pro **Průzkumník řešení** a zobrazí různá prostředí, která máte k dispozici. V seznamu se zobrazují obě prostředí, která jste nainstalovali pomocí instalačního programu sady Visual Studio, a ty, které jste nainstalovali samostatně. Který zahrnuje globální, virtuální a conda prostředí. Prostředí je tučným písmem výchozí prostředí, které se používá pro nové projekty. Další informace o práci s prostředími najdete v tématu [jak vytvářet a spravovat prostředí Pythonu v prostředích sady Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Okno prostředí Pythonu](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Okno prostředí Pythonu můžete otevřít také tak, že vyberete okno Průzkumník řešení a použijete klávesovou zkratku **CTRL + K, CTRL +** . Pokud zástupce nefunguje a v nabídce nemůžete najít okno prostředí Pythonu, je možné, že jste nenainstalovali úlohu Pythonu. Pokyny k instalaci Pythonu najdete [v tématu Jak nainstalovat podporu Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md) .

2. Karta **Přehled** prostředí poskytuje rychlý přístup k **interaktivnímu** oknu pro toto prostředí spolu s instalační složkou a Překladači prostředí. Můžete například vybrat **otevřít interaktivní okno** a **interaktivní** okno pro toto konkrétní prostředí se zobrazí v aplikaci Visual Studio.

3. Nyní vytvořte nový projekt se **souborem**  >  **Nový**  >  **projekt**a vyberte šablonu **aplikace Python** . V souboru kódu, který se zobrazí, vložte následující kód, který vytvoří kosinus Wave jako v předchozích krocích kurzu, tentokrát se graficky vykresluje. Alternativně můžete použít projekt, který jste dříve vytvořili, a nahradit kód.

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

4. V otevřeném projektu Python můžete také otevřít okno prostředí Pythonu z Průzkumník řešení kliknutím pravým tlačítkem na **prostředí Pythonu** a výběrem **Zobrazit všechna prostředí Pythonu.**

   ![Prostředí](media/environments/environments-view-all-2019.png)

5. V okně editoru si všimněte, že pokud najedete myší na `numpy` `matplotlib` příkazy a, které nejsou vyřešeny. To je proto, že balíčky nebyly nainstalovány do výchozího globálního prostředí.

   ![Import nevyřešeného balíčku](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Instalace balíčků pomocí okna prostředí Pythonu

1. V okně prostředí Pythonu vyberte výchozí prostředí pro nové projekty v Pythonu a zvolte kartu **balíčky** . Zobrazí se seznam balíčků, které jsou aktuálně nainstalovány v prostředí.

   ![Balíčky nainstalované v prostředí](media/environments/environments-installed-packages-2019.png)

2. Nainstalujte `matplotlib` zadáním jeho názvu do vyhledávacího pole a pak vyberte možnost **Spustit příkaz: PIP Install matplotlib** . Tím se nainstaluje `matplotlib` i všechny balíčky, na kterých závisí (v tomto případě zahrnuje `numpy` ).

   ![Instalace matplotlib v prostředí](media/environments/environments-add-matplotlib-2019.png)

5. Pokud k tomu budete vyzváni, je nutné vyjádřit souhlas s zvýšením oprávnění.

6. Po instalaci balíčku se zobrazí v okně **prostředí Pythonu** . Znak **X** napravo od balíčku ho odinstaluje.

   ![Dokončení instalace matplotlib v prostředí](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > V prostředí se může zobrazit malý indikátor průběhu, který indikuje, že sada Visual Studio sestavuje svou databázi IntelliSense pro nově nainstalovaný balíček. Na kartě **technologie IntelliSense** se zobrazí také podrobnější informace. Mějte na paměti, že dokud se databáze nedokončí, funkce IntelliSense, jako je automatické dokončování a kontrola syntaxe, nebudou v editoru pro daný balíček aktivní.
   >
   > Visual Studio 2017 verze 15,6 a novější používá pro práci s technologií IntelliSense jinou metodu a rychlejší a na kartě **IntelliSense** zobrazí zprávu s tímto efektem.

## <a name="run-the-program"></a>Spuštění programu

1. Teď, když je nainstalovaný [matplotlib](https://matplotlib.org/) , spusťte program s (**F5**) nebo bez ladicího programu (**CTRL** + **F5**) a zobrazte výstup:

   ![Výstup příkladu matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Další krok

> [!div class="nextstepaction"]
> [Práce s Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Prostředí Pythonu](managing-python-environments-in-visual-studio.md)
- [Jak používat Django v sadě Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Jak používat Flask v sadě Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
