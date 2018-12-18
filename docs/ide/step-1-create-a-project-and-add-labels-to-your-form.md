---
title: 'Krok 1: Vytvořte projekt a přidejte do svého formuláře popisky'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb29a985a39344c5bffad59e63a9d540311ec648
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925113"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1: Vytvořte projekt a přidejte do svého formuláře popisky

Jako první kroky ve vývoji tohoto kvízu vytvoříte projekt a přidat popisky, tlačítka a další ovládací prvky do formuláře. Můžete také nastavit vlastnosti pro každý ovládací prvek, který přidáte. Projekt bude obsahovat formulář, ovládací prvky a (později v tomto návodu) kód. Tlačítko spustí kvíz, popisky zobrazí problémy kvízu a další ovládací prvky zobrazí odpovědi kvízu a čas, který zbývá do dokončení kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních principech kódování. Přehled kurzu, naleznete v tématu [kurz 2: vytvoření matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-project-and-set-properties-for-a-form"></a>Chcete-li vytvořit projekt a nastavit vlastnosti pro formulář

1.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

2.  V **nainstalované šablony** , zvolte buď **jazyka C#** nebo **jazyka Visual Basic**.

3.  V seznamu šablon vyberte **formulářová aplikace Windows** šablony, pojmenujte ho **matematický kvíz**a klikněte na tlačítko **OK** tlačítko.

     Formulář, který je pojmenován *Form1.cs* nebo *Form1.vb* v závislosti na programovacím jazyce, který jste zvolili.

4.  Vyberte formulář a změňte jeho **Text** vlastnost **matematický kvíz**.

     **Vlastnosti** okno obsahuje vlastnosti pro formulář.

5.  Změňte velikost formuláře na 500 pixelů na šířku a výšku 400 pixelů.

     Změnit velikost formuláře přetažením jeho okrajů, dokud se nezobrazí správná velikost v levém dolním rohu integrovaného vývojového prostředí (IDE). Jako alternativu můžete změnit hodnoty **velikost** vlastnost.

6.  Změňte hodnotu **FormBorderStyle** vlastnost **Fixed3D**a nastavte **MaximizeBox** vlastnost **False**.

     Tyto hodnoty zabraňují uživatelům vyplňujícím kvíz ve změně velikosti formuláře.

## <a name="to-create-the-time-remaining-box"></a>Chcete-li vytvořit pole Zbývající čas

1.  Přidat <xref:System.Windows.Forms.Label> ovládacího prvku **nástrojů**a pak nastavte hodnotu jeho **(název)** vlastnost **timeLabel**.

     Tento popisek se stane polem v pravém horním rohu, který zobrazuje počet sekund do ukončení kvízu.

2.  Změnit **AutoSize** vlastnost **False** tak, že můžete změnit velikost pole.

3.  Změnit **BorderStyle** vlastnost **FixedSingle** nakreslení čáry kolem pole.

4.  Nastavte **velikost** vlastnost **200, 30**.

5.  Přetáhněte jmenovku do pravého horního rohu formuláře, ve kterém se zobrazí modré oddělovací čáry.

     Tyto řádky vám pomohou Zarovnat ovládací prvky ve formuláři.

6.  V **vlastnosti** okna, vyberte **Text** vlastnost a klikněte na tlačítko **Backspace** klíč pro vymazání jeho hodnoty.

7.  Vyberte znaménko plus (**+**) vedle položky **písmo** vlastnost a potom změňte hodnotu **velikost** vlastnost **15,75**.

     Můžete změnit několik vlastností písma, jak ukazuje následující obrázek.

     ![Okno Vlastnosti zobrazující velikost písma](../ide/media/express_setfontsize.png)

8.  Přidejte další ovládací prvek popisek z **nástrojů**a potom změňte jeho velikost písma na **15,75**.

9. Nastavte **Text** vlastnost **zbývající čas**.

10. Přesuňte popisek tak, aby byl zarovnán pouze na levé straně **timeLabel** popisek.

### <a name="to-add-controls-for-the-addition-problems"></a>Chcete-li přidat ovládací prvky pro úlohy sčítání

1.  Přidejte ovládací prvek popisek z **nástrojů**a pak nastavte jeho **Text** vlastnost **?** (otazník).

2.  Nastavte **AutoSize** vlastnost **False**.

3.  Nastavte **velikost** vlastnost **60, 50**.

4.  Nastavte velikost písma **18**.

5.  Nastavte **TextAlign** vlastnost **MiddleCenter**.

6.  Nastavte **umístění** vlastnost **50, 75** pro umístění ovládacího prvku na formuláři.

7.  Nastavte **(název)** vlastnost **plusLeftLabel**.

8.  Zvolte **plusLeftLabel** popisek a zvolte buď **Ctrl**+**C** klíče nebo **kopírování** na  **Upravit** nabídky.

9. Vložit popisek třikrát výběrem buď **Ctrl**+**V** klíče nebo **vložit** na **upravit** nabídky.

10. Uspořádejte tři nové popisky tak, aby byly v řádku napravo od **plusLeftLabel** popisek.

     Můžete použít oddělovací čáry a místo řádek nahoru.

11. Nastavte hodnotu druhého popisku **Text** vlastnost **+** (znaménko plus).

12. Nastavte hodnotu třetího popisku **(název)** vlastnost **plusRightLabel**.

13. Nastavte hodnotu čtvrté jmenovky **Text** vlastnost **=** (rovná se).

14. Přidat <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku **nástrojů**, změňte jeho velikost písma na **18**a nastavte jeho šířku na **100**.

     Zobrazí další informace o tomto druhu ovládacího prvku později.

15. Zarovnejte ovládací prvek NumericUpDown s popisky ovládacích prvků pro úlohu sčítání.

16. Změňte hodnotu **(název)** vlastnost pro ovládací prvek NumericUpDown **součet**.

     Vytvořili jste první řádek, jak ukazuje následující obrázek.

     ![První řádek matematického kvízu](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Přidání ovládacích prvků pro problémy odčítání, násobení a dělení

1.  Zkopírujte všech pět ovládacích prvků pro úlohu sčítání (čtyři ovládací prvky Label a ovládací prvek NumericUpDown) a pak je vložte.

     Formulář obsahuje pět nových ovládacích prvků, které jsou stále vybrané.

2.  Přesuňte všechny ovládací prvky na místo tak, aby byly vyrovnány pod dalšími ovládacími prvky.

     Můžete použít oddělovací čáry pro poskytnutí dostatku vzdálenosti mezi dvěma řádky.

3.  Změňte hodnotu **Text** vlastnosti pro druhý popisek na **-** (znaménko minus).

4.  Pojmenujte první jmenovku otazníku **minusLeftLabel**.

5.  Pojmenujte druhou jmenovku otazníku **minusRightLabel**.

6.  Ovládací prvek NumericUpDown **rozdíl**.

7.  Vložte pět ovládacích prvků ještě dvakrát.

8.  Třetí řádek pojmenujte první jmenovku **timesLeftLabel**, změňte druhý popisek **Text** vlastnost **×** (znaménko násobení), pojmenujte třetí jmenovku **timesRightLabel**a ovládací prvek NumericUpDown **produktu**.

9. Čtvrtý řádek pojmenujte první jmenovku **dividedLeftLabel**, změňte druhý popisek **Text** vlastnost **÷** (děleno), pojmenujte třetí jmenovku  **dividedRightLabel**a ovládací prvek NumericUpDown **podíl**.

    > [!NOTE]
    > Můžete zkopírovat × znaménko násobení a dělení přihlašování ÷ z tohoto kurzu a vložte je do formuláře.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Přidání tlačítka start a nastavení pořadí indexů karty

1.  Přidat <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů**a pak nastavte jeho **(název)** vlastnost **startButton**.

2.  Nastavte **Text** vlastnost **spusťte kvíz**.

3.  Nastavte velikost písma **14**.

4.  Nastavte **AutoSize** vlastnost **True**, což způsobí, že tlačítko automaticky změní velikost podle textu.

5.  Prostřední tlačítko v dolní části formuláře.

6.  Nastavte hodnotu **TabIndex** vlastnost **startButton** mít pod kontrolou **1**.

    > [!NOTE]
    > **TabIndex** vlastnost nastavuje pořadí ovládacích prvků při kvízu vybere **kartu** klíč. Pokud chcete zobrazit, jak to funguje, otevřete dialogové okno všechny (například v panelu nabídek zvolte **souboru** > **otevřete**) a klikněte na tlačítko **kartu** klíč několikrát. Podívejte se, jak se váš kurzor přesouvá z ovládacího prvku na ovládací prvek pokaždé, když, abyste zvolili **kartu** klíč. Programátor pořadí při vytváření formuláře.

7.  Nastavte hodnotu **TabIndex** vlastnost pro součtový ovládací prvek NumericUpDown na **2**, pro ovládací prvek rozdílu na **3**, ovládací prvek produktu **4**a pro ovládací prvek podílu na **5**.

     Formulář by měl vypadat jako na následujícím obrázku.

     ![Počáteční formulář matematického kvízu](../ide/media/express_formlaidout.png)

8.  Chcete-li ověřit, jestli **TabIndex** vlastnost funguje podle očekávání, uložte a spusťte váš program výběrem **F5** klíče, nebo podle výběru **ladění**  >  **Spustit ladění** v nabídce a potom vyberte **kartu** klíč několikrát.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 2: Vytvořte náhodný problém s přidáním](../ide/step-2-create-a-random-addition-problem.md).

-   K návratu na téma přehledu přejděte [kurz 2: vytvoření matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).
