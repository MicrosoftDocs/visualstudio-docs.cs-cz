---
title: 'Krok 3: Přiřazení náhodné ikony každému popisku'
ms.date: 03/21/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 627b798827cd0b966d1f34336c7e1119841f9d4a
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472626"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: Přiřazení náhodné ikony každému popisku

Pokud se ikony každou hru zobrazí ve stejných buňkách, není to zrovna náročné. Chcete-li tomu zabránit, přiřaďte ikony náhodně ovládacím prvkům Label ve formuláři pomocí metody. `AssignIconsToSquares()`

## <a name="to-assign-a-random-icon-to-each-label"></a>Přiřazení náhodné ikony každému popisku

1. Před přidáním následujícího kódu se zamyslete nad tím, jak metoda funguje. Je nové klíčové slovo: `foreach` v `For Each` jazyce C# a v jazyce Visual Basic. (Jeden z řádků je záměrně jako komentář, což je vysvětleno na konci této procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky zobrazíte fragment kódu jazyka C# nebo fragment kódu jazyka Visual Basic.<br><br>![Ovládání programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Přidejte `AssignIconsToSquares()` metodu, jak je znázorněno v předchozím kroku. Můžete jej umístit těsně pod kód, který jste přidali v [kroku 2: Přidat náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak již bylo zmíněno dříve, `AssignIconsToSquares()` je něco `foreach` nového ve `For Each` vaší metodě: smyčky v jazyce C# a v jazyce Visual Basic. `For Each` Smyčku můžete použít vždy, když chcete provést stejnou akci vícekrát. V tomto případě chcete provést stejné příkazy pro <xref:System.Windows.Forms.TableLayoutPanel>každý popisek na vašem , jak je vysvětleno v následujícím kódu. První řádek vytvoří proměnnou s názvem, `control` která ukládá každý ovládací prvek jeden po druhém, zatímco tento ovládací prvek má příkazy ve smyčce provedeny na něm.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > Názvy „iconLabel“ a „ovládací prvek“ se používají, protože jsou popisné. Tyto názvy můžete nahradit libovolnými názvy a kód by měl pracovat přesně stejně, dokud nezměníte název v každém výroku uvnitř smyčky.

     Metoda `AssignIconsToSquares()` iterates prostřednictvím každého ovládacího prvku popisek v TableLayoutPanel a provede stejné příkazy pro každý z nich. Tyto příkazy vytáhnout náhodnou ikonu ze seznamu, který jste přidali v [kroku 2: Přidat náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). Připomínáme, že každá z těchto ikon je písmeno v písmu Webdings, což je důvod, proč jsou vyjádřeny jako text v této metodě. Do seznamu jste zahrnuli dvě z každé ikony, takže by byla přiřazena dvojice ikon náhodným ovládacím prvkům Label.

     Podívejte se blíže na kód, `foreach` `For Each` který běží uvnitř nebo smyčky. Tento kód je reprodukován zde.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     První řádek převede **řídicí** proměnnou na popisek s názvem **iconLabel**. Řádek za tím `if` je prohlášení, které kontroluje, zda převod fungoval. Pokud převod funguje, příkazy `if` v příkazu spustit. (Jak si můžete vzpomenout z `if` předchozích kurzů, příkaz se používá k vyhodnocení jakékoli podmínky, kterou zadáte.) První řádek v `if` příkazu vytvoří proměnnou s názvem **randomNumber,** která obsahuje náhodné číslo, které odpovídá jedné z položek v seznamu ikon. Chcete-li to provést, používá metodu <xref:System.Random.Next> objektu, <xref:System.Random> který jste vytvořili dříve. Metoda `Next` vrátí náhodné číslo. Tento řádek také <xref:System.Collections.Generic.List%601.Count> používá vlastnost seznamu **ikon** k určení rozsahu, ze kterého chcete vybrat náhodné číslo. Další řádek přiřadí jednu z položek <xref:System.Windows.Forms.Label.Text> seznamu ikon vlastnosti popisku. Komentovaný řádek je vysvětlen později v tomto tématu. Nakonec poslední řádek v `if` příkazu odebere ze seznamu ikonu, která byla přidána do formuláře.

     Nezapomeňte, že pokud si nejste jisti, co dělá některá část kódu, můžete umístit ukazatel myši nad prvek kódu a přečíst si zobrazený popisek. Můžete také krokovat po řádcích kódu, zatímco je program spuštěn pomocí ladicího programu sady Visual Studio. Další [informace najdete v tématu Jak to mám: Krok ovat ladicím programem v sadě Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) [Navigate through code with the debugger](../debugger/navigating-through-code-with-the-debugger.md)

3. Chcete-li naplnit herní desku ikonami, musíte zavolat metodu, `AssignIconsToSquares()` jakmile se program spustí. Pokud používáte C#, přidejte příkaz těsně pod `InitializeComponent()` volání metody v _konstruktoru_ **Form1** , takže formulář volá novou metodu k nastavení před zobrazením. Konstruktory jsou volány při vytváření nového objektu, například třídy nebo struktury. Viz [Konstruktory (C# programovací průvodce)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) nebo [použití konstruktory a destruktory](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) v jazyce Visual Basic pro další informace.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Pro visual basic `AssignIconsToSquares()` přidejte volání `Form1_Load` metody do metody tak, aby kód vypadal takto.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Uložte program a spusťte jej. Měl by se zobrazit formulář s náhodnými ikonami přiřazenými každému popisku. 

5. Ukončete program a znovu jej spusťte. Všimněte si, že každému popisku jsou přiřazeny jiné ikony, viz následující obrázek. 

     ![Porovnávací hra s náhodnými ikonami](../ide/media/express_tut4step3.png)<br/>
*Porovnávací hra s náhodnými ikonami*

     Ikony jsou nyní viditelné, protože jste je neskryli. Chcete-li je skrýt před přehrávačem, můžete nastavit vlastnost **ForeColor** každého popisku na stejnou barvu jako jeho vlastnost **BackColor.**

6. Chcete-li skrýt ikony, zastavte program a odeberte značky komentářů pro řádek kódu s komentáři uvnitř `For Each` smyčky.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Na řádku nabídek zvolte tlačítko **Uložit vše,** chcete-li program uložit, a spusťte jej. Ikony zdánlivě zmizely – zobrazí se pouze modré pozadí. Ikony jsou ale náhodně přiřazeny a stále existují. Vzhledem k tomu, že ikony mají stejnou barvu jako pozadí, hráč je nevidí. Přece by to byla velmi jednoduchá hra, kdyby hráč hned viděl všechny ikony!

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kroku kurzu, **[přečtěte si krok 4: Přidání obslužné rutiny události kliknutí ke každému popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 2: Přidání náhodného objektu a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
