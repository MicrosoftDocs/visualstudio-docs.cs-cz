---
title: Ipythonu REPL (interaktivní okno)
description: Pomocí interaktivního okna sady Visual Studio v režimu IPython pro uživatelsky přívětivé interaktivní vývojové prostředí nabízející funkce, interaktivní paralelní výpočty.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 84e93d06e294ef11cc345eb4c443845421a8f834
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067800"
---
# <a name="use-ipython-in-the-interactive-window"></a>Použití Ipythonu v interaktivním okně

Visual Studio **interaktivní** je okno v režimu IPython pokročilé ještě uživatelsky přívětivé interaktivní vývoj prostředí, které obsahuje funkce, interaktivní paralelní výpočty. Tento článek vás provede použitím IPython v sadě Visual Studio **interaktivní** okno, ve kterém jsou všechny normálního [interaktivní okno](python-interactive-repl-in-visual-studio.md) funkce jsou také k dispozici.

V tomto návodu, byste měli mít [Anaconda](https://www.continuum.io) prostředí nainstalovaná, což zahrnuje IPython a potřebné knihovny.

> [!Note]
> IronPython nepodporuje IPython, bez ohledu na skutečnost, že ji vyberete na **interaktivní možnosti** formuláře. Další informace najdete v článku [žádost o funkci](https://github.com/Microsoft/PTVS/issues/84).

1. Otevřít Visual Studio, přejděte **prostředí Pythonu** okno (**zobrazení** > **ostatní Windows** > **prostředí Pythonu** ) a vyberte prostředí Anaconda.

2. Zkontrolujte **balíčky (Conda)** kartu (což se může zobrazit **pip** nebo **balíčky**) pro toto prostředí, abyste měli jistotu, že `ipython` a `matplotlib` jsou uvedeny. V opačném případě je nainstalovat zde. (Viz [prostředí Pythonu windows – karta balíčky](python-environments-window-tab-reference.md).)

3. Vyberte **přehled** kartě a vyberte **interaktivní režim IPython použití**. (V sadě Visual Studio 2015, vyberte **konfigurovat interaktivní možnosti** otevřít **možnosti** dialogové okno, nastavte **interaktivním režimu** k **IPython**a vyberte **OK**).

4. Vyberte **otevřít interaktivní okno** zobrazíte **interaktivní** okno v režimu IPython. Možná budete muset obnovit v okně, pokud jste právě změnili interaktivním režimu; Možná budete také muset stiskněte **Enter** Pokud pouze >>> výzva zobrazí, tak, aby se zobrazí příkazový řádek jako **v [2]**.

    ![Interaktivní okno v režim IPython](media/ipython-repl-03.png)

5. Zadejte následující kód:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np
  
   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Po zadání na posledním řádku, měli byste vidět vložené grafu, (to můžete změnit velikost přetažením v pravém dolním rohu v případě potřeby).

    ![Vložené grafu v interaktivním okně](media/ipython-repl-04.png)

7. Místo zadání v REPL, místo toho můžete napsat kód v editoru, vyberte ho, klikněte pravým tlačítkem a vyberte **zaslat do Interactive** příkazu (nebo stiskněte klávesu **Ctrl**+**Enter**). Zkuste vložíte následující kód do nového souboru v editoru, vyberte ho s **Ctrl**+**A**, potom odešlete do **interaktivní** okna. (Visual Studio odešle kód jako jedna jednotka na Vyhněte se poskytování zprostředkující nebo částečné grafu. A pokud nemáte Python projekt otevřít v různém prostředí vybrali, Visual Studio otevře **interaktivní** libovolné prostředí je zvolen jako výchozí v okně **prostředí Pythonu**okna.)

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

8. Chcete-li zobrazit grafy mimo **interaktivní** okna spuštění kódu namísto použití **ladění** > **spustit bez ladění** příkazu.

IPython má mnoho dalších užitečných funkcí jako je například uvození prostředí systému a nahrazení proměnné zachytávání výstupu, např. Odkazovat [IPython dokumentaci](https://ipython.org/documentation.html) Další informace.

## <a name="see-also"></a>Viz také:

- Chcete-li použít Jupyter snadno a bez instalace, zkuste bezplatnou [poznámkových bloků Azure hostovaná služba](https://notebooks.azure.com/) , který umožňuje zachovat a sdílení vašich poznámkových bloků s ostatními.

- [Virtuální počítač Azure datové vědy](/azure/machine-learning/data-science-virtual-machine/overview) také předem nakonfigurované na spouštění poznámkových bloků Jupyter spolu s širokou řadu dalších nástrojů pro datové vědy.
