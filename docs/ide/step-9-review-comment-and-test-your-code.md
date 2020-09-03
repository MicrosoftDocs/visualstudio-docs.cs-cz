---
title: 'Krok 9: Kontrola, okomentování a otestování kódu'
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b31532bf6c26512e471ee787dc7219620e6db62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579744"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Krok 9: Kontrola, okomentování a otestování kódu

Dál přidáte komentář k vašemu kódu. Komentář je Poznámka, která nemění způsob, jakým se aplikace chová. Usnadňuje někomu, kdo čte váš kód, abychom pochopili, co dělá. Přidání komentářů do kódu je dobrým příznakem, který se má dostat do.

V jazyce C# dvě lomítka (//) označí řádek jako komentář. V Visual Basic se k označení řádku jako komentáře používá jednoduchá uvozovka ('). Po přidání komentáře otestujete aplikaci. Dobrým zvykem je spouštět a testovat kód často při práci na projektech, takže můžete zachytit a opravit případné problémy dříve, než bude kód složitější. Toto se nazývá *iterativní testování*.

Právě jste vytvořili něco, co funguje, a i když ještě není hotové, může už načíst obrázek. Než přidáte komentář do kódu a otestujete jej, vezměte v úvahu čas ke kontrole konceptů kódu, protože tyto koncepty budete používat často:

- Po dvojitém kliknutí na tlačítko **Zobrazit obrázek** v **Návrhář formulářů**rozhraní IDE automaticky přidalo do kódu programu *metodu* .

- Metody slouží k uspořádání kódu: Jedná se o způsob seskupení kódu dohromady.

- Ve většině případů metoda dělá malý počet věcí v určitém pořadí, například jak vaše `showButton_Click()` metoda (nebo `ShowButton_Click()` ) zobrazuje dialogové okno a následně načítá obrázek.

- Metoda je tvořena *příkazy*kódu nebo řádky kódu. Metodu můžete představit jako způsob, jak seskupit příkazy kódu dohromady.

- Když je metoda spuštěna nebo *volána*, příkazy v metodě jsou spouštěny v pořadí, jeden po druhém, počínaje první.

   Následuje příklad příkazu.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Příkazy jsou to, co dělají vaše programy. V jazyce C# příkaz vždy končí středníkem. V Visual Basic konec řádku je konec příkazu. (V Visual Basic není potřeba žádný středník.) Předchozí příkaz oznamuje vašemu <xref:System.Windows.Forms.PictureBox> ovládacímu prvku, aby načetl soubor, který uživatel vybral pomocí komponenty **OpenFileDialog** .

## <a name="to-add-comments"></a>Přidání komentářů

1. Přidejte následující komentář do kódu.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    **showButton** <xref:System.Windows.Forms.Control.Click> Obslužná rutina události tlačítka showButton je teď dokončená a funguje. Začali jste psát kód, počínaje `if` příkazem. `if`Příkaz je způsob, jakým vaše aplikace poznáte, "Podívejte se na tuto jednu věc a pokud ano, udělejte tyto akce." V tomto případě určíte, aby aplikace otevřela dialogové okno **otevřít soubor** , a pokud uživatel vybere soubor a klikne na tlačítko **OK** , načte tento soubor do **ovládacího prvku PictureBox**.

    > [!TIP]
    > Rozhraní IDE je sestaveno tak, aby bylo snadné psát kód a *fragmenty kódu* jsou jedním ze způsobů, jak to provést. Fragment kódu je zástupce, který se rozšíří na malý blok kódu.
    >
    >  Můžete zobrazit všechny dostupné fragmenty kódu. Na řádku nabídek klikněte na **nástroje**  >  **Správce fragmentů kódu**. V jazyce C# `if` je fragment kódu v jazyce **Visual C#** . Pro Visual Basic `if` jsou fragmenty **kódu**v  >  **podmíněných vzorcích a smyčkách**. Pomocí tohoto správce můžete procházet existující fragmenty nebo přidávat vlastní fragmenty kódu.
    >
    >  Chcete-li aktivovat fragment při psaní kódu, zadejte jej a vyberte klávesu **TAB** . Mnoho fragmentů kódu se zobrazí v okně **technologie IntelliSense** , což je důvod, proč si vyberete klávesu **TAB** dvakrát: nejprve vyberte fragment kódu z okna **technologie IntelliSense** a potom pro určení rozhraní IDE, aby používal fragment. (Technologie IntelliSense podporuje `if` fragment, ale ne `ifelse` fragment.)

1. Před spuštěním aplikace uložte aplikaci tak, že kliknete na tlačítko **Uložit vše** na panelu nástrojů, které by mělo vypadat podobně jako na následujícím snímku obrazovky.

     ![Tlačítko Uložit vše na panelu nástrojů](../ide/media/express_iconsaveall.png)<br>
*Tlačítko* ***Uložit vše***

     Pokud chcete aplikaci uložit, zvolte **soubor**  >  **Uložit vše** z panelu nabídek (nebo stiskněte klávesy **CTRL** + **SHIFT** + **S**). Osvědčeným postupem je ukládat včas a často.

     Když je spuštěný, váš program by měl vypadat jako na následujícím obrázku.

     ![Prohlížeč obrázků](../ide/media/express_pictureviewerdonerun.png)<br>***Prohlížeč obrázků***

## <a name="to-test-your-app"></a>Testování aplikace

1. Klikněte na klávesu **F5** nebo vyberte tlačítko **Spustit ladění** na panelu nástrojů.

1. Kliknutím na tlačítko **Zobrazit obrázek** spusťte kód, který jste právě napsali. Nejprve aplikace otevře dialogové okno **otevřít soubor** . Ověřte, že se filtry zobrazí v rozevíracím seznamu **soubory typu** v dolní části dialogového okna. Pak přejděte na obrázek a otevřete ho. Ukázkové obrázky, které se dodávají s operačním systémem Windows, můžete obvykle najít ve složce *dokumenty* ve složce *Moje Pictures\Sample obrázky* .

    > [!TIP]
    > Pokud se v dialogovém okně **Vybrat soubor s obrázkem** nezobrazí žádné obrázky, ujistěte se, že je v rozevíracím seznamu v pravé dolní části dialogového okna vybrán filtr **všechny soubory (*. \* )** .

1. Načtěte obrázek, který se zobrazí v ovládacím prvku PictureBox. Pak zkuste změnit velikost formuláře přetažením jeho ohraničení. Vzhledem k tomu, že máte ovládací prvek PictureBox ukotven uvnitř kontejneru TableLayoutPanel, který je umístěn uvnitř formuláře, změní se vaše oblast obrázku tak, aby byla stejná jako forma formuláře, a vyplní horní 90 procent formuláře. To je důvod, proč jste <xref:System.Windows.Forms.TableLayoutPanel> použili <xref:System.Windows.Forms.FlowLayoutPanel> kontejnery a: při změně velikosti uživatele udržují vaši formu správnou velikost.

     Nyní větší obrázky přecházejí nad hranicemi prohlížeče obrázků. V dalším kroku přidáte kód, který zajistí přizpůsobení obrázků v okně.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si téma **[Krok 10: zápis kódu pro další tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si [Krok 8: napište kód pro zobrazení obslužné rutiny události tlačítka Zobrazit obrázek](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
