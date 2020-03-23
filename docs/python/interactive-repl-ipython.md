---
title: IPython REPL (interaktivní okno)
description: Interaktivní okno Visual Studio v režimu IPython použijte pro uživatelsky přívětivé interaktivní vývojové prostředí s funkcemi interaktivníparalelní výpočetní techniky.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8b4510ed738fdd2b33389ab4242dbde86cffff8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957726"
---
# <a name="use-ipython-in-the-interactive-window"></a>Použití IPythonv interaktivním okně

Interaktivní **okno** Visual Studio v režimu IPython je pokročilé, ale uživatelsky přívětivé interaktivní vývojové prostředí, které má funkce interaktivní paralelní výpočetní techniky. Tento článek vás provede pomocí IPython v **interaktivní** okno Visual Studio, ve kterém jsou k dispozici také všechny běžné [interaktivní okno](python-interactive-repl-in-visual-studio.md) funkce.

Pro tento návod byste měli mít nainstalované prostředí [Anaconda,](https://www.continuum.io) které zahrnuje IPython a potřebné knihovny.

> [!Note]
> IronPython nepodporuje IPython, navzdory skutečnosti, že jej můžete vybrat ve formuláři **Interaktivní možnosti.** Další informace naleznete v [žádosti o funkci](https://github.com/Microsoft/PTVS/issues/84).

1. Otevřete Visual Studio, přepněte do okna **Prostředí Pythonu** (**Zobrazit** > **další prostředí Windows** > **Pythonu**) a vyberte prostředí Anaconda.

2. **Zkontrolujte, zda karty Balíčky (Conda)** (které se mohou zobrazit `ipython` `matplotlib` jako **pip** nebo **balíčky)** pro toto prostředí a ujistěte se, že a jsou uvedeny. Pokud ne, nainstalujte je zde. (Viz [Python Prostředí windows - balíčky kartu](python-environments-window-tab-reference.md).)

3. Vyberte kartu **Přehled** a vyberte **Použít interaktivní režim IPython**. (V Visual Studiu 2015 vyberte **Konfigurovat interaktivní možnosti,** chcete-li otevřít dialogové okno **Možnosti,** potom nastavit **interaktivní režim** na **IPython**a vybrat **OK**).

4. Vyberte **Otevřít interaktivní okno,** chcete-li vyvolat **interaktivní** okno v režimu IPython. Pokud jste právě změnili interaktivní režim, bude pravděpodobně nutné okno obnovit. Pokud se zobrazí pouze výzva >>> , může být také nutné stisknout klávesu **Enter,** aby se zobrazila výzva jako **v [2]**.

    ![Interaktivní okno v režimu IPython](media/ipython-repl-03.png)

5. Zadejte následující kód:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Po zadání posledního řádku byste měli vidět vložkový graf (který můžete v případě potřeby změnit přetažením v pravém dolním rohu).

    ![Inline graf v interaktivním okně](media/ipython-repl-04.png)

7. Místo psaní do repl, můžete místo toho psát kód v editoru, vyberte jej, pravým tlačítkem myši, a vyberte **Odeslat do interaktivní** příkaz (nebo stiskněte **klávesu Ctrl**+**Enter**). Zkuste vložit níže uvedený kód do nového souboru v editoru, vyberte jej pomocí **klávesCtrl**+**A**a potom odešlete do **interaktivního** okna. (Visual Studio odešle kód jako jednu jednotku, aby se zabránilo poskytování mezilehlé nebo částečné grafy. A pokud nemáte otevřený projekt Pythonu s vybraným jiným prostředím, Visual Studio otevře **interaktivní** okno pro jakékoli prostředí, které je vybráno jako výchozí v okně **Prostředí Pythonu.)**

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Odeslání kódu z editoru do interaktivního okna](media/ipython-repl-05.png)

8. Chcete-li zobrazit grafy mimo **interaktivní** okno, spusťte kód místo použití **příkazu Ladění** > **start bez ladění.**

IPython má mnoho dalších užitečných funkcí, jako je únik do systémového prostředí, variabilní substituce, zachytávání výstupu atd. Další informace naleznete v [dokumentaci k IPythonu.](https://ipython.org/documentation.html)

## <a name="see-also"></a>Viz také

- Pokud chcete Jupyter používat snadno a bez instalace, vyzkoušejte bezplatnou [hostovkou poznámkových bloků Azure,](https://notebooks.azure.com/) která vám umožní uchovávat a sdílet poznámkové bloky s ostatními.

- [Virtuální počítač Azure Data Science](/azure/machine-learning/data-science-virtual-machine/overview) je taky předem nakonfigurovaný pro spouštění poznámkových bloků Jupyter spolu s celou řadou dalších nástrojů pro datové vědy.
