---
title: 'Krok 9: Kontrola, komentování a testování kódu'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579744"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Krok 9: Kontrola, komentování a testování kódu

Další přidat komentář do kódu. Komentář je poznámka, která nemění způsob, jakým se aplikace chová. To usnadňuje pro někoho, kdo čte váš kód pochopit, co to dělá. Přidávání komentářů do kódu je dobrý zvyk se dostat do.

V c# dva lomítka (//) označují řádek jako komentář. V jazyce Visual Basic se jedna uvozovka (') používá k označení řádku jako komentáře. Po přidání komentáře otestujete aplikaci. Je vhodné spustit a otestovat kód často při práci na projektech, takže můžete zachytit a opravit všechny problémy brzy, než se kód zkomplikuje. Tose nazývá *iterativní testování*.

Právě jste vytvořili něco, co funguje, a i když to ještě není hotové, může již načíst obrázek. Před přidáním komentáře do kódu a testování, nějakou dobu trvat, než zkontrolovat koncepty kódu, protože budete používat tyto koncepty často:

- Po poklepání na tlačítko **Zobrazit obrázek** v **Návrháři formulářů systému Windows**ide automaticky přidá *metodu* do kódu programu.

- Metody jsou způsob uspořádání kódu: Je to, jak je váš kód seskupeny dohromady.

- Ve většině případů metoda provádí malý počet věcí v určitém pořadí, například jak vaše `showButton_Click()` (nebo `ShowButton_Click()`) metoda zobrazuje dialogové okno a pak načte obrázek.

- Metoda se skládá z *příkazů*kódu nebo řádků kódu. Představte si metodu jako způsob, jak seskupit příkazy kódu dohromady.

- Při spuštění metody nebo *volání*, příkazy v metodě jsou prováděny v pořadí, jeden po druhém, počínaje první.

   Následuje příklad příkazu.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Prohlášení jsou to, co vaše programy dělat věci. V C# příkaz vždy končí středníkem. V jazyce Visual Basic je konec řádku koncem příkazu. (V jazyce Visual Basic není potřeba žádný středník.) Předchozí příkaz informuje <xref:System.Windows.Forms.PictureBox> ovládací prvek k načtení souboru, který uživatel vybral pomocí komponenty **OpenFileDialog.**

## <a name="to-add-comments"></a>Přidání komentářů

1. Přidejte do kódu následující komentář.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    Obslužná <xref:System.Windows.Forms.Control.Click> rutina události tlačítka **showButton** je nyní dokončena a funguje. Začali jste psát kód, `if` počínaje příkazem. Prohlášení `if` je, jak říct, vaše aplikace, "Zkontrolujte tuto jednu věc, a pokud je to pravda, proveďte tyto akce." V takovém případě aplikaci sdělte, aby otevřela dialogové okno **Otevřít soubor,** a pokud uživatel vybere soubor a vybere tlačítko **OK,** načtěte tento soubor v **okně PictureBox**.

    > [!TIP]
    > Integrované číslo IDE je vytvořeno tak, aby bylo pro psaní kódu snadné, a *fragmenty kódu* jsou jedním ze způsobů, jak to udělat. Úryvek je zástupce, který se rozbalí do malého bloku kódu.
    >
    >  Můžete zobrazit všechny dostupné úryvky. Na řádku nabídek zvolte Správce**výstřižků kódu** **nástrojů** > . Pro C#je `if` výstřižek ve **visual c#** . Pro visual basic `if` fragmenty jsou v **kód vzory** > **podmínky a smyčky**. Pomocí tohoto správce můžete procházet existující úryvky nebo přidávat vlastní výstřižky.
    >
    >  Chcete-li při psaní kódu aktivovat výstřižek, zadejte jej a zvolte klávesu **Tabulátor.** V okně **IntelliSense** se zobrazí mnoho úryvků, což je důvod, proč zvolíte klávesu **Tab** dvakrát: nejprve vyberte úryvek z okna **IntelliSense** a pak řeknete ide, aby použilvýstřičnou položku. (Technologie IntelliSense `if` podporuje úryvek, `ifelse` nikoli však úryvek.)

1. Před spuštěním aplikace uložte aplikaci výběrem tlačítka **Uložit vše,** které by mělo vypadat podobně jako na následujícím snímku obrazovky.

     ![Tlačítko Uložit vše](../ide/media/express_iconsaveall.png)<br>
***Tlačítko Uložit vše*** *button*

     Chcete-li aplikaci uložit, **zvolte** > Uložit**vše ze** panelu nabídek (nebo stiskněte **kombinaci kláves Ctrl**+**Shift**+**S).** Je to osvědčený postup pro ukládání brzy a často.

     Při spuštění by měl program vypadat jako na následujícím obrázku.

     ![Prohlížeč obrázků](../ide/media/express_pictureviewerdonerun.png)<br>***Prohlížeč obrázků***

## <a name="to-test-your-app"></a>Testování aplikace

1. Zvolte klávesu **F5** nebo zvolte tlačítko **Spustit ladění** panelu nástrojů.

1. Chcete-li spustit kód, který jste právě napsali, zvolte tlačítko **Zobrazit obrázek.** Nejprve aplikace otevře dialogové okno **Otevřít soubor.** Ověřte, zda se filtry zobrazují v rozevíracím seznamu **Soubory typu** v dolní části dialogového okna. Pak přejděte na obrázek a otevřete ho. Ukázkové obrázky, které jsou dodávány s operačním systémem Windows, můžete obvykle najít ve složce *Dokumenty* ve složce *Obrázky.*

    > [!TIP]
    > Pokud v dialogovém okně **Vybrat soubor obrázku** nevidíte žádné obrázky, zkontrolujte, zda je v rozevíracím seznamu na pravé dolní straně dialogového okna vybrán filtr Všechny soubory **(*.\*)** v rozevíracím seznamu.

1. Načtěte obrázek a zobrazí se v pictureboxu. Potom zkuste velikost formuláře přetažením přetažením přetažením. Vzhledem k tomu, že máte PictureBox ukotvené uvnitř TableLayoutPanel, který sám je ukotven uvnitř formuláře, bude velikost obrázku velikost sám tak, aby byl stejně široký jako formulář a vyplní horní 90 procent formuláře. To je důvod, <xref:System.Windows.Forms.TableLayoutPanel> proč <xref:System.Windows.Forms.FlowLayoutPanel> jste použili kontejnery a: Udržují velikost formuláře správně, když uživatel změní velikost.

     Právě teď, větší obrázky přesahují hranice prohlížeče obrázků. V dalším kroku přidáte kód, aby se obrázky vešly do okna.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kroku kurzu, **[přečtěte si krok 10: Napište kód pro další tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 8: Napište kód pro obslužnou rutinu události tlačítka zobrazit obrázek](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
