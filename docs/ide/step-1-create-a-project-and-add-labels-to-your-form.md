---
title: 'Krok 1: Vytvoření projektu a přidání štítků do formuláře'
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bf904fca84fba88e81306ff91add6c2156b4544
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579444"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1: Vytvoření projektu a přidání štítků do formuláře

Jako první kroky při vývoji tohoto kvízu vytvoříte projekt a do formuláře přidáte popisky, tlačítko a další ovládací prvky. Můžete také nastavit vlastnosti pro každý ovládací prvek, který přidáte. Projekt bude obsahovat formulář, ovládací prvky a (později v kurzu) kód. Tlačítko spustí kvíz, popisky zobrazí problémy s kvízem a ostatní ovládací prvky zobrazí odpovědi kvízu a čas, který zbývá do konce kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-project-for-a-form"></a>Vytvoření projektu pro formulář

::: moniker range="vs-2017"

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. Na levé straně dialogového okna **Nový projekt** zvolte **visual c#** nebo **visual basic** a pak zvolte **Plochu systému Windows**.

1. V seznamu šablon zvolte šablonu **aplikace Windows Forms App (.NET Framework),** pojmenujte ji *MathQuiz*a pak zvolte tlačítko **OK.**

    V závislosti na vybraném programovacím jazyce se zobrazí formulář s názvem *Form1.cs* nebo *Form1.vb.*

   > [!NOTE]
   > Pokud šablonu aplikace **Windows Forms App (.NET Framework)** nevidíte, nainstalujte pracovní vytížení **pro vývoj plochy .NET** pomocí Instalační služby visual studia.<br/><br/>![Úloha vývoje plochy rozhraní .NET v Instalační službě sady Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Další informace najdete na stránce [Instalace sady Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

1. V počátečním okně zvolte **Vytvořit nový projekt**.

   ![Zobrazit okno Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte windows *forms* do vyhledávacího pole. Dále zvolte **Plocha** ze seznamu **typ projektu.**

   Po použití filtru **typu projektu** zvolte šablonu aplikace Windows Forms **App (.NET Framework)** pro c# nebo visual basic a pak zvolte **Další**.

   ![Zvolte šablonu jazyka C# nebo Visual Basic pro aplikaci Windows Forms App (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Pokud šablonu **Aplikace Windows Forms (.NET Framework)** nevidíte, můžete ji nainstalovat z okna Vytvořit nový **projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?**
   >
   > ![Odkaz "Nainstalovat další nástroje a funkce" ze zprávy "Nenajít to, co hledáte" v okně "Vytvořit nový projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Dále v Instalační službě sady Visual Studio zvolte zvolte **úlohu vývoje plochy .NET.**
   >
   > ![Úloha jádra .NET v Instalační službě sady Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Poté zvolte tlačítko **Změnit** v Instalační službě sady Visual Studio. Můžete být vyzváni k uložení práce. pokud ano, uvažte tak. Dále zvolte **Pokračovat** k instalaci úlohy.

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MathQuiz* do pole **Název projektu.** Potom zvolte **Vytvořit**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Nastavení vlastností formuláře

1. V sadě Visual Studio zvolte formulář *(buď Form1.cs* nebo *Form1.vb*, v závislosti na programovacím jazyce) a změňte jeho vlastnost **Text** na **Matematický kvíz**.

     Okno **Vlastnosti** obsahuje vlastnosti formuláře.

1. Změňte velikost formuláře na 500 pixelů na šířku o 400 pixelů.

     Velikost formuláře můžete změnit přetažením jeho okrajů, dokud se v levém dolním rohu integrovaného vývojového prostředí (IDE) nezobrazí správná velikost. Jako alternativu můžete změnit hodnoty **Size** vlastnost.

1. Změňte hodnotu vlastnosti **FormBorderStyle** na **Fixed3D**a nastavte vlastnost **MaximizeBox** na **Hodnotu False**.

     Tyto hodnoty brání příjemcům kvízu v tom, aby formulář měnili.

## <a name="to-create-the-time-remaining-box"></a>Vytvoření zbývajícího časového pole

1. Přidejte <xref:System.Windows.Forms.Label> ovládací prvek z **panelu nástrojů**a nastavte hodnotu jeho vlastnosti **(Name)** na **timeLabel**.

     Tento štítek se stane rámečkem v pravém horním rohu, který zobrazuje počet sekund, které zůstávají v kvízu.

2. Změňte vlastnost **AutoSize** na **Hodnotu Nepravda,** abyste mohli změnit velikost pole.

3. Změňte **BorderStyle** vlastnost **FixedSingle** nakreslit čáru kolem pole.

4. Nastavte **Vlastnost Size** na **200, 30**.

5. Přesuňte popisek do pravého horního rohu formuláře, kde se zobrazí modré čáry mezery.

     Tyto řádky pomáhají zarovnat ovládací prvky ve formuláři.

6. V okně **Vlastnosti** zvolte vlastnost **Text** a pak zvolte klávesu **Backspace,** chcete-li vymazat její hodnotu.

7. Zvolte znaménko plus**+**( ) vedle Vlastnost **Font** a pak změňte hodnotu Size vlastnost **15.75**. **Size**

     Můžete změnit několik vlastností písma, jak ukazuje následující snímek obrazovky.

     ![Okno Vlastnosti zobrazující velikost písma](../ide/media/express_setfontsize.png)

8. Přidejte další ovládací prvek Popisek z **panelu nástrojů**a nastavte jeho velikost písma na **15,75**.

9. Nastavte vlastnost **Text** na **možnost Čas vlevo**.

10. Přesuňte popisek tak, aby zařazuje pouze nalevo od popisku **timeLabel.**

### <a name="to-add-controls-for-the-addition-problems"></a>Přidání ovládacích prvků pro problémy s přidáním

1. Přidejte ovládací prvek Popisek z **panelu nástrojů**a nastavte jeho vlastnost **Text** na **?** (otazník).

2. Nastavte vlastnost **AutoSize** na **hodnotu False**.

3. Nastavte **Vlastnost Size** na **60, 50**.

4. Nastavte velikost písma na **18**.

5. Nastavte vlastnost **TextAlign** na **MiddleCenter**.

6. Nastavte **Vlastnost Location** na **50, 75** pro umístění ovládacího prvku ve formuláři.

7. Nastavte vlastnost **(Name)** na **plusLeftLabel**.

8. Zvolte popisek **plusLeftLabel** a pak zvolte buď klávesy **Ctrl**+**C,** nebo **Kopírovat** v nabídce **Úpravy.**

9. Vložte popisek třikrát tak, že vyberete klávesy **Ctrl**+**V** nebo **V nabídce** **Úpravy.**

10. Uspořádejte tři nové popisky tak, aby byly v řádku vpravo od popisku **plusLeftLabel.**

     Můžete použít distanční čáry k jejich rozmístit a line-line je.

11. Nastavte hodnotu vlastnosti **Text** druhého **+** popisku na (znaménko plus).

12. Nastavte hodnotu vlastnosti třetí popisek **(Název)** na **hodnotu plusRightLabel**.

13. Nastavte hodnotu vlastnosti **Text** čtvrtého **=** popisku na hodnotu (znaménko rovná se).

14. Přidejte <xref:System.Windows.Forms.NumericUpDown> ovládací prvek z **panelu nástrojů**, nastavte jeho velikost písma na **18**a nastavte jeho šířku na **100**.

     Více informací o tomto druhu kontroly se dozvíte později.

15. Zařazujete ovládací prvek NumericUpDown pomocí ovládacích prvků Label pro problém s přidáním.

16. Změňte hodnotu vlastnosti **(Name)** pro ovládací prvek NumericUpDown na **součet**.

     Vytvořili jste první řádek, jak je znázorněno na následujícím obrázku.

     ![První řádek matematického kvízu](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Přidání ovládacích prvků pro problémy s odčítáním, násobením a dělením

1. Zkopírujte všech pět ovládacích prvků pro problém přidání (čtyři label ovládací prvky a NumericUpDown ovládací prvek) a vložte je.

     Formulář obsahuje pět nových ovládacích prvků, které jsou stále vybrány.

2. Přesuňte všechny ovládací prvky na místo tak, aby se zařazují pod ovládací prvky sčítání.

     Můžete použít distanční čáry, abyste mezi oběma řádky poskytli dostatečnou vzdálenost.

3. Změňte hodnotu vlastnosti **Text** pro **-** druhý popisek na (znaménko mínus).

4. Pojmenujte první popisek otazníku **minusLeftLabel**.

5. Pojmenujte druhý popisek otazníku **minusRightLabel**.

6. Pojmenujte **rozdíl**ovládacího prvku NumericUpDown .

7. Vložte pět ovládacích prvků ještě dvakrát.

8. Pro třetí řádek pojmenujte první label **timesLeftLabel**, změňte vlastnost **Text** druhého popisku na **×** (znak násobení), pojmenujte třetí popisek **timesRightLabel**a pojmenujte **ovládací produkt**NumericUpDown .

9. Pro čtvrtý řádek pojmenujte první popisek **dividedLeftLabel**, změňte vlastnost **Text** druhého popisku na **÷** (znaménko dělení), pojmenujte třetí popisek **dividedRightLabel**a pojmenujte **kvocient ovládacího prvku**NumericUpDown .

    > [!NOTE]
    > Můžete zkopírovat znak násobení × a znak dělení ÷ z tohoto kurzu a vložit je do formuláře.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Přidání tlačítka Start a nastavení pořadí indexů karet

1. Přidejte <xref:System.Windows.Forms.Button> ovládací prvek z **panelu nástrojů**a nastavte jeho vlastnost **(Název)** na **startButton**.

2. Nastavte vlastnost **Text** tak, aby **spustila kvíz**.

3. Nastavte velikost písma na **14**.

4. Nastavte vlastnost **AutoSize** na **hodnotu True**, což způsobí, že se velikost tlačítka automaticky změní tak, aby odpovídala textu.

5. Vystředěte tlačítko v dolní části formuláře.

6. Nastavte hodnotu vlastnosti **TabIndex** pro ovládací prvek **startButton** na **hodnotu 1**.

    > [!NOTE]
    > Vlastnost **TabIndex** nastaví pořadí ovládacích prvků, když příjemce kvízu zvolí klávesu **Tab.** Chcete-li zjistit, jak to funguje, otevřete libovolné dialogové okno (například na řádku nabídek zvolte**Otevřít** **soubor** > ) a pak několikrát zvolte klávesu **Tabulátor.** Sledujte, jak se kurzor pohybuje od ovládacího prvku k ovládacímu prvku pokaždé, když zvolíte klávesu **Tabulátor.** Programátor rozhodl pořadí při vytváření tohoto formuláře.

7. Nastavte hodnotu vlastnosti **TabIndex** pro ovládací prvek součet NumericUpDown na **hodnotu 2**, pro ovládací prvek rozdíl na **3**, pro ovládací prvek produktu na **4**a pro ovládací prvek kvocientu na **5**.

     Formulář by měl vypadat podobně jako na následujícím snímku obrazovky.

     ![Počáteční formulář matematického kvízu](../ide/media/express_formlaidout.png)

8. Chcete-li ověřit, zda **tabindex** vlastnost funguje podle očekávání, uložte a spusťte program výběrem **klávesy F5** nebo výběrem **ladění** > **start ladění** na řádku nabídek a pak zvolte **klávesu Tab** několikrát.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Chcete-li přejít k dalšímu kroku kurzu, **[přečtěte si krok 2: Vytvoření problému s náhodným přidáním](../ide/step-2-create-a-random-addition-problem.md)**.

- Chcete-li se vrátit k tématu [přehledu, přečtěte si téma 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).
