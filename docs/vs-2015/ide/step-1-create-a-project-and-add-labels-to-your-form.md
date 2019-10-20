---
title: 'Krok 1: Vytvořte projekt a přidejte do svého formuláře popisky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a13d96d8932a3a9e4628f2d0e67a28869252c95
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667365"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1: Vytvořte projekt a přidejte do svého formuláře popisky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jako první kroky při vývoji tohoto kvízu vytvoříte projekt a přidáte popisky, tlačítko a další ovládací prvky do formuláře. Nastavili jste také vlastnosti pro každý ovládací prvek, který přidáte. Projekt bude obsahovat formulář, ovládací prvky a (dále v tomto kurzu) kódu. Tlačítko spustí kvíz, jmenovky zobrazí problémy kvízu a ostatní ovládací prvky zobrazí odpovědi kvízu a čas, který zbývá k dokončení kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-create-a-project-and-set-properties-for-a-form"></a>Vytvoření projektu a nastavení vlastností pro formulář

1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

2. V seznamu **Nainstalované šablony** vyberte možnost **C#** nebo **Visual Basic**.

3. V seznamu šablon vyberte šablonu **aplikace model Windows Forms** , pojmenujte ji **Math kvíz**a pak klikněte na tlačítko **OK** .

     Zobrazí se formulář s názvem **Form1.cs** nebo **Form1. vb** v závislosti na zvoleném programovacím jazyce.

4. Zvolte formulář a změňte jeho vlastnost **text** na **Matematický kvíz**.

     Okno **vlastnosti** obsahuje vlastnosti pro formulář.

5. Změňte velikost formuláře na 500 pixelů na šířku až 400 pixelů na výšku.

     Velikost formuláře můžete změnit přetažením jeho okrajů, dokud se nezobrazí správná velikost v levém dolním rohu integrovaného vývojového prostředí (IDE). Alternativně můžete změnit hodnoty vlastnosti **Size** .

6. Změňte hodnotu vlastnosti **FormBorderStyle** na **Fixed3D**a vlastnost **MaximizeBox** nastavte na **false**.

     Tyto hodnoty zabrání v uživatelé vyplňujícíi kvízu změnit velikost formuláře.

### <a name="to-create-the-time-remaining-box"></a>Vytvoření pole pro zbývající čas

1. Přidejte ovládací prvek **popisek** z panelu nástrojů a potom nastavte hodnotu vlastnosti **(název)** na `timeLabel`.

     Tento popisek se stane polem v pravém horním rohu, které zobrazuje počet sekund, které zůstanou v kvízu.

2. Změňte vlastnost **AutoSize** na **hodnotu false** , abyste mohli měnit velikost pole.

3. Změňte vlastnost **BorderStyle** na **FixedSingle** , aby se kolem pole nakreslila čára.

4. Nastavte vlastnost **Size** na **200, 30**.

5. Přesuňte popisek do pravého horního rohu formuláře, kde se objeví modré oddělovací čáry.

     Tyto čáry vám pomůžou Zarovnat ovládací prvky ve formuláři.

6. V okně **vlastnosti** zvolte vlastnost **text** a potom stiskněte klávesu Backspace a vymažte její hodnotu.

7. Zvolte znaménko plus (+) vedle vlastnosti **Font** a pak změňte hodnotu vlastnosti **Size** na **15,75**.

     Můžete změnit několik vlastností písma, jak je znázorněno na následujícím obrázku.

     ![Okno Vlastnosti zobrazení velikosti písma](../ide/media/express-setfontsize.png "Express_setFontSize") okno Vlastnosti zobrazení velikosti písma

8. Přidejte další ovládací prvek **popisek** z panelu nástrojů a nastavte jeho velikost písma na **15,75**.

9. Nastavte vlastnost **text** na hodnotu **zbývající čas**.

10. Přesuňte popisek tak, aby byl zarovnán přesně vlevo od popisku **timeLabel** .

### <a name="to-add-controls-for-the-addition-problems"></a>Přidání ovládacích prvků pro úlohy sčítání

1. Přidejte ovládací prvek **popisek** z panelu nástrojů a potom nastavte jeho vlastnost **text** na **?** (otazník).

2. Nastavte vlastnost **AutoSize** na **hodnotu false**.

3. Nastavte vlastnost **Size** na **60, 50**.

4. Nastavte velikost písma na **18**.

5. Nastavte vlastnost **TextAlign** na **hodnotu MiddleCenter**.

6. Nastavte vlastnost **umístění** na **50, 75** pro umístění ovládacího prvku ve formuláři.

7. Nastavte vlastnost **(Name)** na **plusLeftLabel**.

8. Zvolte popisek **plusLeftLabel** a pak zvolte buď klávesy CTRL + C nebo příkaz **Kopírovat** v nabídce **Upravit** .

9. Vložte popisek třikrát kliknutím na klávesovou zkratku CTRL + V nebo **Vložit** v nabídce **Upravit** .

10. Uspořádejte tři nové popisky tak, aby byly v řádku napravo od popisku **plusLeftLabel** .

     Pomocí oddělovacích čar můžete Vymístit jejich prostor a založit je.

11. Nastavte hodnotu vlastnosti **text** druhé jmenovky na **+** (znaménko plus).

12. Nastavte hodnotu vlastnosti třetího popisku **(Name)** na **plusRightLabel**.

13. Nastavte hodnotu vlastnosti **text** čtvrtého popisku na **=** (symbol rovná se).

14. Přidejte ovládací prvek **NumericUpDown** ze sady nástrojů, nastavte jeho velikost písma na **18**a nastavte jeho šířku na **100**.

     O tomto druhu řízení se dozvíte později.

15. Zapište ovládací prvek **NumericUpDown** pomocí ovládacího prvku popisek pro problém sčítání.

16. Změňte hodnotu vlastnosti **(Name)** ovládacího prvku **NumericUpDown** na **součet**.

     Vytvořili jste první řádek, jak ukazuje následující obrázek.

     ![První řádek matematického kvízu](../ide/media/express-firstrow.png "Express_firstRow") První řádek matematického kvízu

### <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Přidání ovládacích prvků pro problémy odčítání, násobení a dělení

1. Zkopírujte všechny pět ovládacích prvků pro problém sčítání (čtyři ovládací prvky popisek a ovládací prvek NumericUpDown) a pak je vložte.

     Formulář obsahuje pět nových ovládacích prvků, které jsou stále vybrány.

2. Přesuňte všechny ovládací prvky na místo, aby byly v souladu s ovládacími prvky sčítání.

     Oddělovací čáry můžete použít k poskytnutí dostatečné vzdálenosti mezi dvěma řádky.

3. Změňte hodnotu vlastnosti **text** pro druhý popisek na **–** (znaménko minus).

4. Pojmenujte první popisek otazníku **minusLeftLabel**.

5. Pojmenujte druhou jmenovku otazníku **minusRightLabel**.

6. Pojmenujte **rozdíl**ovládacího prvku **NumericUpDown** .

7. Vložte pět ovládacích prvků dvakrát.

8. Pro třetí řádek pojmenujte první jmenovku **timesLeftLabel**, změňte vlastnost **text** druhé jmenovky na hodnotu **×** (znaménko násobení), pojmenujte třetí popisek **timesRightLabel**a pojmenujte ho na řídicí **produkt**NumericUpDown.

9. U čtvrtého řádku pojmenujte první popisek **dividedLeftLabel**, změňte vlastnost **text** druhé jmenovky na **÷** (znaménko dělení), pojmenujte třetí popisek **dividedRightLabel**a pojmenujte **podíl**ovládacího prvku NumericUpDown.

    > [!NOTE]
    > V tomto kurzu můžete zkopírovat znaménko násobení × a znaménko dělení ÷ a vložit je do formuláře.

### <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Přidání tlačítka Start a nastavení pořadí indexů karet

1. Přidejte ovládací prvek **tlačítko** z panelu nástrojů a potom nastavte jeho vlastnost **(Name)** na **startButton**.

2. Nastavte vlastnost **text** na hodnotu **spustit kvíz**.

3. Nastavte velikost písma na **14**.

4. Nastavte vlastnost **AutoSize** na **hodnotu true**, což způsobí, že tlačítko automaticky změní velikost tak, aby odpovídala textu.

5. Vycentruje tlačítko v dolní části formuláře.

6. Nastavte hodnotu vlastnosti **TabIndex** ovládacího prvku **startButton** na hodnotu **1**.

    > [!NOTE]
    > Vlastnost **TabIndex** nastaví pořadí ovládacích prvků, když si autor kvízu zvolí klávesu TAB. Chcete-li zjistit, jak to funguje, otevřete libovolné dialogové okno (například na panelu nabídek zvolte **soubor**, **otevřít**) a pak několikrát zvolte klávesu TAB. Sledujte, jak se kurzor pohybuje od ovládacího prvku a řídí se pokaždé, když vyberete klávesu TAB. Programátor určil pořadí při vytváření tohoto formuláře.

7. Nastavte hodnotu vlastnosti **TabIndex** pro ovládací prvek NumericUpDown suma na **2**, pro ovládací prvek rozdíl na **3**, pro řízení produktu na **4**a pro řízení podílu na **5**.

     Formulář by měl vypadat jako na následujícím obrázku.

     ![Počáteční formulář matematického kvízu](../ide/media/express-formlaidout.png "Express_FormLaidOut") Počáteční formulář matematického kvízu

8. Chcete-li ověřit, zda vlastnost **TabIndex** funguje podle očekávání, uložte a spusťte program tak, že vyberete klávesu F5 nebo kliknete na položku **ladit**, **Spustit ladění** na řádku nabídek a několikrát vyberte klávesu TAB.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek krok 2: vytvoření náhodného problému s přidáním](../ide/step-2-create-a-random-addition-problem.md).

- Pokud se chcete vrátit k tématu Přehled, přečtěte si článek [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).
