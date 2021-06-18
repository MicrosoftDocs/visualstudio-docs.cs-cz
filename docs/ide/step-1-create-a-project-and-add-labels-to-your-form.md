---
title: 'Krok 1: Vytvoření projektu a přidání popisků do formuláře'
description: Zjistěte, jak vytvořit projekt, přidat popisky, tlačítko a další ovládací prvky do formuláře a nastavit vlastnosti pro každý ovládací prvek, který přidáte.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0400c29e53c45ad9a98e7edca78fd2cf9741fcf0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307749"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Krok 1: Vytvoření projektu a přidání popisků do formuláře

Jako první kroky při vývoji tohoto kvízu vytvoříte projekt a do formuláře přidáte popisky, tlačítko a další ovládací prvky. Můžete také nastavit vlastnosti pro každý ovládací prvek, který přidáte. Projekt bude obsahovat formulář, ovládací prvky a (dále v tomto kurzu). Tlačítko spustí kvíz, popisky zobrazí problémy kvízu a ostatní ovládací prvky ukazují odpovědi kvízu a čas, který zbývá na dokončení kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu Kurz 2: Vytvoření matematického kvízu [s časovým limitem.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-create-a-project-for-a-form"></a>Vytvoření projektu pro formulář

::: moniker range="vs-2017"

1. Na řádku nabídek zvolte File New Project **(Soubor** > **nový** > **projekt).**

1. Zvolte **Visual C#** **nebo Visual Basic** na levé  straně dialogového okna Nový projekt a pak zvolte **Windows Desktop.**

1. V seznamu šablon zvolte šablonu **model Windows Forms App (.NET Framework),** pojmete ji *MathQuiz* a pak zvolte **tlačítko OK.**

    V závislosti na programovacím jazyce, který jste zvolili, se zobrazí formulář s názvem *Form1.cs* nebo *Form1.vb.*

   > [!NOTE]
   > Pokud šablonu model Windows Forms **App (.NET Framework)** nevidíte, použijte Instalační program pro Visual Studio k instalaci úlohy vývoje desktopových aplikací **.NET.**<br/><br/>![Úloha vývoj desktopových aplikací .NET v Instalační program pro Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Další informace najdete na stránce [Instalace Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

1. V úvodním okně zvolte **Vytvořit nový projekt.**

   ![Zobrazení okna Vytvořit nový projekt](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. V **okně Vytvořit nový** projekt zadejte nebo zadejte *model Windows Forms* do vyhledávacího pole. Potom v **seznamu Typ** projektu zvolte **Desktop.**

   Po použití filtru **Typ projektu** zvolte šablonu model Windows Forms **App (.NET Framework)** pro jazyk C# nebo Visual Basic a pak zvolte **Další.**

   ![Zvolte šablonu C# nebo Visual Basic pro aplikaci model Windows Forms (.NET Framework).](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Pokud se šablona **model Windows Forms App (.NET Framework),** můžete ji nainstalovat z okna Vytvořit **nový** projekt. Ve zprávě **Nehledá se, co hledáte?** zvolte odkaz Instalovat **další** nástroje a funkce.
   >
   > ![Odkaz Install more tools and features (Nainstalovat další nástroje a funkce) ze zprávy Not finding what you're looking for (Najít, co hledáte) v okně Create new project (Vytvořit nový projekt)](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > V dalším kroku Instalační program pro Visual Studio zvolte úlohu Zvolte vývoj desktopových aplikací **pro .NET.**
   >
   > ![Úloha .NET Core v Instalační program pro Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Potom zvolte tlačítko **Upravit** v Instalační program pro Visual Studio. Může se zobrazit výzva k uložení práce. Pokud ano, proveďte to. Potom zvolte **Pokračovat a** nainstalujte úlohu.

1. V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo zadejte *MathQuiz* **do pole Project name (Název** projektu). Pak zvolte **Vytvořit.**

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Nastavení vlastností formuláře

1. V Visual Studio zvolte formulář *(Form1.cs* nebo *Form1.vb* v závislosti na programovacím jazyce) a pak změňte jeho vlastnost **Text** na **Math Quiz**.

     Okno **Vlastnosti** obsahuje vlastnosti formuláře.

1. Změňte velikost formuláře na šířku 500 pixelů a výšku 400 pixelů.

     Velikost formuláře můžete změnit přetažením jeho okrajů, dokud se v levém dolním rohu integrovaného vývojového prostředí (IDE) nezobrazí správná velikost. Jako alternativu můžete změnit hodnoty vlastnosti **Size.**

1. Změňte hodnotu vlastnosti **FormBorderStyle** na **Fixed3D** a nastavte vlastnost **MaximizeBox** na **False**.

     Tyto hodnoty znemožňují uživatelům kvízu změnu velikosti formuláře.

## <a name="to-create-the-time-remaining-box"></a>Vytvoření zbývajícího časového pole

1. Přidejte ovládací prvek z panelu nástrojů a pak nastavte hodnotu jeho <xref:System.Windows.Forms.Label> vlastnosti **(Name)** na **timeLabel**. 

     Tento popisek se stane polem v pravém horním rohu, které zobrazuje počet sekund zbývajících v kvízu.

2. Změňte **vlastnost AutoSize** na **False,** abyste mohli změnit velikost pole.

3. Změňte **vlastnost BorderStyle** na **FixedSingle** a nakreslete kolem rámečku čáru.

4. Vlastnost **Size nastavte** na **200, 30.**

5. Přesuňte popisek do pravého horního rohu formuláře, kde se zobrazí modré čárky mezerníku.

     Tyto čáry vám pomůžou zarovnat ovládací prvky ve formuláři.

6. V **okně Vlastnosti** zvolte vlastnost **Text** a pak výběrem klávesy **Backspace** vymažte její hodnotu.

7. Zvolte znaménko plus ( ) vedle vlastnosti Font a pak změňte hodnotu vlastnosti **+** **Size** na **15,75**. 

     Můžete změnit několik vlastností písma, jak je vidět na následujícím snímku obrazovky.

     ![okno Vlastnosti velikost písma](../ide/media/express_setfontsize.png)

8. Přidejte další ovládací prvek Popisek ze **sady nástrojů** a pak nastavte jeho velikost písma na **15,75.**

9. Vlastnost **Text nastavte** na **Time Left**.

10. Přesuňte popisek tak, aby se začaril nalevo od **popisku timeLabel.**

### <a name="to-add-controls-for-the-addition-problems"></a>Přidání ovládacích prvků pro problémy s přidáváním

1. Přidejte ovládací prvek Popisek z **panelu nástrojů** a jeho vlastnost **Text nastavte** na **?** (otazník).

2. Nastavte **vlastnost AutoSize** na **False**.

3. Vlastnost **Size nastavte** **na 60, 50.**

4. Nastavte velikost písma na **18.**

5. Vlastnost **TextAlign nastavte** na **MiddleCenter**.

6. Vlastnost **Location (Umístění)** **nastavte na 50, 75,** aby se ovládací prvek na formuláři umiste.

7. Nastavte **vlastnost (Name)** na **plusLeftLabel**.

8. Zvolte **popisek plusLeftLabel** a pak zvolte **klávesy Ctrl** C nebo +  **Kopírovat** v **nabídce Úpravy.**

9. Vložte popisek třikrát tak, že v nabídce Upravit zvolíte **klávesy Ctrl** V nebo +  **Vložit.** 

10. Uspořádejte tři nové popisky tak, aby byly na řádku napravo od **popisku plusLeftLabel.**

     Mezery můžete použít k jejich rozteč a jejich sesesování.

11. Nastavte hodnotu vlastnosti **Text** druhého popisku na **+** (znaménko plus).

12. Nastavte hodnotu vlastnosti **(Name)** třetího popisku na **plusRightLabel**.

13. Nastavte hodnotu vlastnosti **Text** čtvrtého popisku **=** na (znaménko rovná se).

14. Přidejte ovládací prvek ze sady nástrojů, nastavte jeho velikost písma na 18 a nastavte jeho <xref:System.Windows.Forms.NumericUpDown> šířku na **100.**  

     O tomto druhu kontroly se dozvíte více později.

15. Sestavte ovládací prvek NumericUpDown pomocí ovládacích prvků Popisek pro problém sčítání.

16. Změňte hodnotu vlastnosti **(Name)** ovládacího prvku NumericUpDown na **součet**.

     Vytvořili jste první řádek, jak je znázorněno na následujícím obrázku.

     ![První řádek matematického kvízu](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Přidání ovládacích prvků pro problémy odčítání, násobení a dělení

1. Zkopírujte všech pět ovládacích prvků pro problém sčítání (čtyři ovládací prvky Popisek a ovládací prvek NumericUpDown) a vložte je.

     Formulář obsahuje pět nových ovládacích prvků, které jsou stále vybrané.

2. Přesuňte všechny ovládací prvky na místo, aby byly zasunuly pod ovládací prvky sčítání.

     Pomocí čárek mezerníku můžete mezi těmito dvěma řádky dát dostatečně vzdálenost.

3. Změňte hodnotu vlastnosti **Text** druhého popisku na **-** (znaménko minus).

4. První popisek otazník **pojmete minusLeftLabel**.

5. Druhý popisek otazník **pojmete minusRightLabel**.

6. Jako název ovládacího prvku NumericUpDown **zadejte .**

7. Vložte pět ovládacích prvků ještě dvakrát.

8. Pro třetí řádek pojmete první popisek **timesLeftLabel,** změňte vlastnost **Text** druhého popisku na **×** (znaménko násobení), třetí popisek **timesRightLabel** a název ovládacího prvku NumericUpDown s názvem **.**

9. Pro čtvrtý řádek pojmete první popisek **dividedLeftLabel,** změňte vlastnost **Text** druhého popisku na **÷** (znak dělení), třetí popisek **pojmete dividedRightLabel** a pojmete ovládací prvek NumericUpDown **quotient**.

    > [!NOTE]
    > Můžete zkopírovat znaménko násobení × a znak dělení ÷ z tohoto kurzu a vložit je do formuláře.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Přidání tlačítka Start a nastavení pořadí indexování karet

1. Přidejte ovládací prvek z panelu nástrojů a <xref:System.Windows.Forms.Button> jeho **vlastnost (Name)** nastavte **na startButton**. 

2. Nastavte **vlastnost Text** na Start the quiz **(Spustit kvíz).**

3. Nastavte velikost písma na **14.**

4. Nastavte **vlastnost AutoSize** na **True,** což způsobí, že se velikost tlačítka automaticky přizpůsobí textu.

5. Na střed tlačítka v dolní části formuláře.

6. Nastavte hodnotu vlastnosti **TabIndex** ovládacího **prvku startButton** na **1.**

    > [!NOTE]
    > Vlastnost **TabIndex** nastaví pořadí ovládacích prvků, když kvíz zvolí klávesu **Tab.** Pokud chcete vidět, jak to funguje, otevřete libovolné dialogové okno (například na řádku nabídek zvolte Otevřít soubor ) a potom několikrát stiskněte  >  klávesu Tab.  Sledujte, jak se kurzor posouvá z ovládacího prvku a řídí se při každém výběru **klávesy Tab.** Programátor se při vytváření tohoto formuláře rozhodl o pořadí.

7. Nastavte hodnotu vlastnosti **TabIndex** ovládacího prvku součet NumericUpDown na **2**, pro ovládací prvek rozdílu na **3**, pro ovládací prvek produktu na **4** a pro ovládací prvek podíl na **5**.

     Formulář by měl vypadat podobně jako na následujícím snímku obrazovky.

     ![Formulář počátečního matematického kvízu](../ide/media/express_formlaidout.png)

8. Pokud chcete ověřit, jestli vlastnost **TabIndex** funguje podle očekávání, uložte a spusťte program zvolením klávesy **F5** nebo zvolením možnosti Ladit spustit ladění na řádku nabídek a potom několikrát stiskněte klávesu  >   **Tabulátor.**

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kroku kurzu, podívejte se na **[krok 2: Vytvoření problému s náhodným sčítáním](../ide/step-2-create-a-random-addition-problem.md)**.

- Pokud se chcete vrátit k tématu přehledu, projděte si [Kurz 2: Vytvoření matematického](../ide/tutorial-2-create-a-timed-math-quiz.md)kvízu s časovým limitem.
