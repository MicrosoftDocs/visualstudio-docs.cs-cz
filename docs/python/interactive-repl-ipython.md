---
title: IPython REPL (interaktivní okno)
description: Interaktivní okno Visual Studio v režimu IPython použijte pro uživatelsky přívětivé interaktivní vývojové prostředí s funkcemi interaktivního paralelního zpracování.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e53ef96ad8fab8b26f04ccd5f7f0488d1f0d6985
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974079"
---
# <a name="use-ipython-in-the-interactive-window"></a>Použití IPython v interaktivním okně

**Interaktivní** okno Visual Studio v režimu IPython je pokročilé a uživatelsky přívětivé interaktivní vývojové prostředí, které má funkce interaktivního paralelního zpracování. Tento článek vás provede použitím IPython v **interaktivním** okně sady Visual Studio, ve kterém jsou k dispozici také všechny běžné [interaktivní funkce okna](python-interactive-repl-in-visual-studio.md) .

V tomto návodu byste měli mít nainstalované prostředí [Anaconda](https://www.continuum.io) , které zahrnuje IPython a potřebné knihovny.

> [!Note]
> Ironpythonu nepodporuje IPython, navzdory tomu, že ho můžete vybrat ve formuláři **interaktivní možnosti** . Další informace najdete v [žádosti o funkce](https://github.com/Microsoft/PTVS/issues/84).

1. Otevřete Visual Studio, přepněte do okna **prostředí Pythonu** (**Zobrazit**  >  **Další**  >  **prostředí Windows Python**) a vyberte prostředí Anaconda.

2. Zkontrolujte kartu **balíčky (conda)** (která se může zobrazit jako **PIP** nebo **balíčky**) pro toto prostředí, aby se zajistilo, že `ipython` a `matplotlib` jsou uvedené. Pokud ne, nainstalujte je sem. (Viz [prostředí Python Windows – karta balíčky](python-environments-window-tab-reference.md).)

3. Vyberte kartu **Přehled** a vyberte **použít interaktivní režim IPython**. (V sadě Visual Studio 2015 vyberte **Konfigurovat interaktivní možnosti** pro otevření dialogového okna **Možnosti** , pak nastavte **interaktivní režim** na **IPython** a vyberte **OK**).

4. Vyberte **otevřít interaktivní okno** a zobrazte **interaktivní** okno v režimu IPython. Pokud jste právě změnili interaktivní režim, možná budete muset resetovat okno. Pokud se zobrazí jenom >>> výzvy, budete muset stisknout **ENTER** , takže se zobrazí výzva jako **v [2]**.

    ![Interaktivní okno v režimu IPython](media/ipython-repl-03.png)

5. Zadejte následující kód:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Po zadání posledního řádku byste měli vidět vložený graf (jehož velikost můžete změnit přetažením v pravém dolním rohu, pokud je potřeba).

    ![Vložený graf v interaktivním okně](media/ipython-repl-04.png)

7. Namísto psaní do REPL můžete místo toho napsat kód v editoru, vybrat ho, kliknout pravým tlačítkem a vybrat možnost **Odeslat do interaktivního** příkazu (nebo stisknout klávesu **CTRL** + **ENTER**). Zkuste vložit kód uvedený níže do nového souboru v editoru, vybrat ho pomocí **kombinace kláves CTRL** + **a** a odeslat do **interaktivního** okna. (Visual Studio pošle kód jako jednu jednotku, abyste se vyhnuli poskytování mezilehlých nebo částečných grafů. A pokud nemáte otevřený projekt v Pythonu s vybraným jiným prostředím, Visual Studio otevře **interaktivní** okno pro jakékoli prostředí, které je v okně **prostředí Pythonu** vybrané jako výchozí.)

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

8. Chcete-li zobrazit grafy mimo **interaktivní** okno, spusťte kód místo toho pomocí příkazu **ladit**  >  **Spustit bez ladění** .

IPython má mnoho dalších užitečných funkcí, jako je například uvozovací znaky pro systémové prostředí, nahrazování proměnných, zachycení výstupu atd. Další informace najdete v [dokumentaci k IPython](https://ipython.org/documentation.html) .

## <a name="see-also"></a>Viz také

- [Azure Data Science Virtual Machine](/azure/machine-learning/data-science-virtual-machine/overview) je předem nakonfigurovaný tak, aby spouštěl poznámkové bloky Jupyter spolu s řadou dalších nástrojů pro datové vědy.
