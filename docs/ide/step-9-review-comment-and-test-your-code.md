---
title: 'Krok 9: kontrola, komentář a testování kódu'
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39be6feffb70dd43823af2af0fce719daafc6f78
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572483"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Krok 9: kontrola, komentář a testování kódu

Dál přidáte komentář k vašemu kódu. Komentář je Poznámka, která nemění způsob, jakým se aplikace chová. Usnadňuje někomu, kdo čte váš kód, abychom pochopili, co dělá. Přidání komentářů do kódu je dobrým příznakem, který se má dostat do.

V C#, dvě lomítka (//) označí řádek jako komentář. V Visual Basic se k označení řádku jako komentáře používá jednoduchá uvozovka ('). Po přidání komentáře otestujete aplikaci. Dobrým zvykem je spouštět a testovat kód často při práci na projektech, takže můžete zachytit a opravit případné problémy dříve, než bude kód složitější. Toto se nazývá *iterativní testování*.

Právě jste vytvořili něco, co funguje, a i když ještě není hotové, může už načíst obrázek. Než přidáte komentář do kódu a otestujete jej, vezměte v úvahu čas ke kontrole konceptů kódu, protože tyto koncepty budete používat často:

- Po dvojitém kliknutí na tlačítko **Zobrazit obrázek** v **Návrhář formulářů**rozhraní IDE automaticky přidalo do kódu programu *metodu* .

- Metody slouží k uspořádání kódu: Jedná se o způsob seskupení kódu dohromady.

- Ve většině případů metoda dělá malý počet věcí v určitém pořadí, například způsob, jakým metoda `showButton_Click()` (nebo `ShowButton_Click()`) zobrazuje dialogové okno a následně načte obrázek.

- Metoda je tvořena *příkazy*kódu nebo řádky kódu. Metodu můžete představit jako způsob, jak seskupit příkazy kódu dohromady.

- Když je metoda spuštěna nebo *volána*, příkazy v metodě jsou spouštěny v pořadí, jeden po druhém, počínaje první.

   Následuje příklad příkazu.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Příkazy jsou to, co dělají vaše programy. V C#příkazu, příkaz vždy končí středníkem. V Visual Basic konec řádku je konec příkazu. (V Visual Basic není potřeba žádný středník.) Předchozí příkaz oznamuje vašemu ovládacímu prvku <xref:System.Windows.Forms.PictureBox>, aby načetl soubor, který uživatel vybral pomocí komponenty **OpenFileDialog** .

## <a name="to-add-comments"></a>Přidání komentářů

1. Přidejte následující komentář do kódu.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    Obslužná rutina události <xref:System.Windows.Forms.Control.Click> tlačítka pro **showButton** je teď dokončená a funguje. Začali jste psát kód, počínaje příkazem `if`. Příkaz `if` je způsob, jakým aplikaci poznáte, "Podívejte se na tuto jednu věc a pokud je to pravda, udělejte tyto akce." V tomto případě určíte, aby aplikace otevřela dialogové okno **otevřít soubor** , a pokud uživatel vybere soubor a klikne na tlačítko **OK** , načte tento soubor do **ovládacího prvku PictureBox**.

    > [!TIP]
    > Rozhraní IDE je sestaveno tak, aby bylo snadné psát kód a *fragmenty kódu* jsou jedním ze způsobů, jak to provést. Fragment kódu je zástupce, který se rozšíří na malý blok kódu.
    >
    >  Můžete zobrazit všechny dostupné fragmenty kódu. Na panelu nabídek vyberte **nástroje**  > **Správce fragmentů kódů**. Pro C#je fragment kódu `if` v **jazyce Visual C#**  . Pro Visual Basic jsou fragmenty `if` ve **vzorech kódu**  > **podmíněny a smyčky**. Pomocí tohoto správce můžete procházet existující fragmenty nebo přidávat vlastní fragmenty kódu.
    >
    >  Chcete-li aktivovat fragment při psaní kódu, zadejte jej a vyberte klávesu **TAB** . Mnoho fragmentů kódu se zobrazí v okně **technologie IntelliSense** , což je důvod, proč si vyberete klávesu **TAB** dvakrát: nejprve vyberte fragment kódu z okna **technologie IntelliSense** a potom pro určení rozhraní IDE, aby používal fragment. (Technologie IntelliSense podporuje fragment `if`, ale ne fragment `ifelse`.)

1. Před spuštěním aplikace uložte aplikaci tak, že kliknete na tlačítko **Uložit vše** na panelu nástrojů, které by mělo vypadat podobně jako na následujícím snímku obrazovky.

     tlačítko ![Save všechna tlačítka panelu nástrojů ](../ide/media/express_iconsaveall.png)<br>
*Tlačítko* ***Uložit vše***

     Chcete-li uložit aplikaci, zvolte možnost **soubor**  > **Uložit vše** z panelu nabídek (nebo stiskněte klávesy **CTRL** +**SHIFT** +**S**). Osvědčeným postupem je ukládat včas a často.

     Když je spuštěný, váš program by měl vypadat jako na následujícím obrázku.

     ](../ide/media/express_pictureviewerdonerun.png) ![Picture Viewer<br>***Prohlížeč obrázků***

## <a name="to-test-your-app"></a>Testování aplikace

1. Klikněte na klávesu **F5** nebo vyberte tlačítko **Spustit ladění** na panelu nástrojů.

1. Kliknutím na tlačítko **Zobrazit obrázek** spusťte kód, který jste právě napsali. Nejprve aplikace otevře dialogové okno **otevřít soubor** . Ověřte, že se filtry zobrazí v rozevíracím seznamu **soubory typu** v dolní části dialogového okna. Pak přejděte na obrázek a otevřete ho. Ukázkové obrázky, které se dodávají s operačním systémem Windows, můžete obvykle najít ve složce *dokumenty* ve složce *Moje Pictures\Sample obrázky* .

    > [!TIP]
    > Pokud v dialogovém okně **Vybrat soubor obrázku** nevidíte žádné obrázky, ujistěte se, že je v rozevíracím seznamu v pravé dolní části dialogového okna vybraná možnost filtr **všechny soubory (*. \*)** .

1. Načtěte obrázek, který se zobrazí v ovládacím prvku PictureBox. Pak zkuste změnit velikost formuláře přetažením jeho ohraničení. Vzhledem k tomu, že máte ovládací prvek PictureBox ukotven uvnitř kontejneru TableLayoutPanel, který je umístěn uvnitř formuláře, změní se vaše oblast obrázku tak, aby byla stejná jako forma formuláře, a vyplní horní 90 procent formuláře. To je důvod, proč jste použili <xref:System.Windows.Forms.TableLayoutPanel> a kontejnery <xref:System.Windows.Forms.FlowLayoutPanel>: při změně velikosti uživatele udržují vaši formu správnou velikost.

     Nyní větší obrázky přecházejí nad hranicemi prohlížeče obrázků. V dalším kroku přidáte kód, který zajistí přizpůsobení obrázků v okně.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si téma **[Krok 10: zápis kódu pro další tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)** .

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si [Krok 8: napište kód pro zobrazení obslužné rutiny události tlačítka Zobrazit obrázek](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Viz také:

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
