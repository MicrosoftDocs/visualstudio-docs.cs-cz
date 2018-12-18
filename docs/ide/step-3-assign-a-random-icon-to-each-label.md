---
title: 'Krok 3: Přiřaďte jednotlivým jmenovkám náhodné ikony'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 593d778247e3c1e6b9a09358c82b5fd7139cfbb9
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672909"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: Přiřaďte jednotlivým jmenovkám náhodné ikony
Pokud se ikony každou hru zobrazí ve stejných buňkách, není to zrovna náročné. Abyste tomu předešli, přiřaďte ikony náhodně k ovládacím prvkům popisku ve formuláři pomocí `AssignIconsToSquares()` metody.

## <a name="to-assign-a-random-icon-to-each-label"></a>Přiřazení náhodné ikony každému popisku

1.  Před přidáním následujícího kódu se zamyslete nad tím, jak metoda funguje. Existuje nové klíčové slovo: `foreach` v jazyce Visual C# a `For Each` v jazyce Visual Basic. (Jeden z řádků je záměrně jako komentář, což je vysvětleno na konci této procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

2.  Přidat `AssignIconsToSquares()` způsob, jak je znázorněno v předchozím kroku. Můžete ji umístit přímo pod kód, který jste přidali v [krok 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak bylo zmíněno výše, je něco nového v vaše `AssignIconsToSquares()` metoda: `foreach` smyčky v jazyce Visual C# a `For Each` v jazyce Visual Basic. Můžete použít `For Each` smyčky kdykoli chcete provést stejnou akci více než jednou. V tomto případě chcete spustit stejné příkazy pro každý popisek na vaše <xref:System.Windows.Forms.TableLayoutPanel>, jak je popsáno v následujícím kódu. První řádek vytvoří proměnnou s názvem `control` , který ukládá vždy jeden ovládací prvek v době při, výroky ve smyčce na něm spustily.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    >  Názvy „iconLabel“ a „ovládací prvek“ se používají, protože jsou popisné. Tyto názvy můžete nahradit libovolnými názvy a kód by měl pracovat přesně stejně, dokud nezměníte název v každém výroku uvnitř smyčky.

     `AssignIconsToSquares()` Metoda iteruje jednotlivé ovládací prvky popisku v kontejneru TableLayoutPanel a pro každý z nich spustí stejný příkaz. Tyto příkazy vyžádají náhodnou ikonu ze seznamu, který jste přidali v [krok 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (To je důvod, proč jste zahrnuli dvě z každé ikony v seznamu, aby se spárovaly ikony přiřazené k náhodnému ovládacímu prvku popisku.)

     Podívejte se důkladněji na kód, který běží v rámci `foreach` nebo `For Each` smyčky. Tento kód je reprodukován zde.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     První řádek převede **ovládací prvek** proměnné pro popisek s názvem **iconLabel**. Následující řádek, který je `if` příkaz, který zkontroluje, ujistěte se, že převod pracovali. Pokud byl převod úspěšný, příkazy `if` příkaz spustit. (Jak si pravděpodobně pamatujete z předchozích tutoriálů, `if` prohlášení se používá k vyhodnocení libovolné podmínky.) První řádek `if` příkaz vytvoří proměnnou s názvem **nahodneCislo** , která obsahuje náhodné číslo, které odpovídá jedné z položek v seznamu ikon. K tomu použije <xref:System.Random.Next> metodu <xref:System.Random> objekt, který jste vytvořili dříve. `Next` Metoda vrátí náhodné číslo. Tento řádek také používá <xref:System.Collections.Generic.List%601.Count> vlastnost **ikony** seznamu k určení rozsahu, ze kterého se náhodné číslo vybere. Další řádek přiřadí jednu ikony položky seznamu <xref:System.Windows.Forms.Label.Text> popisku. Komentovaný řádek je vysvětlen později v tomto tématu. Nakonec poslední řádek v `if` příkaz odebere ze seznamu ikonu, která byla přidána do formuláře.

     Nezapomeňte, že pokud si nejste jisti, co dělá některá část kódu, můžete umístit ukazatel myši nad prvek kódu a přečíst si zobrazený popisek. Můžete také krokovat po řádcích kódu, zatímco je program spuštěn pomocí ladicího programu sady Visual Studio. Zobrazit [jak na to: krokování s ladicím programem v sadě Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) nebo [Navigovat prostřednictvím kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md) Další informace.

3.  Pokud chcete zaplnit hrací plochu ikonami, je potřeba volat `AssignIconsToSquares()` metoda co nejdříve po spuštění programu. Pokud používáte jazyk Visual C#, přidejte příkaz pod volání `InitializeComponent()` metodu **Form1**_konstruktor_, aby formulář volal vaši novou metodu pro vlastní nastavení, než se zobrazí. Konstruktory jsou volány při vytváření nového objektu, například třídy nebo struktury. Zobrazit [konstruktory (C# programováním)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) nebo [použijte konstruktory a destruktory](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) v jazyce Visual Basic pro další informace.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     V jazyce Visual Basic přidejte `AssignIconsToSquares()` volání metod, které `Form1_Load` metodu tak, aby kód vypadá následovně.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4.  Uložte program a spusťte jej. Měl by se zobrazit formulář s náhodnými ikonami přiřazenými každému popisku.

5.  Ukončete program a znovu jej spusťte. Všimněte si, že každému popisku jsou přiřazeny jiné ikony, viz následující obrázek.

     ![Porovnávací hra s náhodnými ikonami](../ide/media/express_tut4step3.png) Porovnávací hra s náhodnými ikonami

     Ikony jsou nyní viditelné, protože jste je neskryli. Skrýt hráče, můžete nastavit každý popisek **ForeColor** vlastnost na stejnou barvu jako jeho **BackColor** vlastnost.

    > [!TIP]
    >  Dalším způsobem, jak skrýt ovládací prvky jako popisky je nastavit jejich **Visible** vlastnost **False**.

6.  Chcete-li skrýt ikony, ukončete program a odeberte značky komentáře komentovaného řádku kódu uvnitř `For Each` smyčky.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7.  V panelu nabídek zvolte **Uložit vše** tlačítko uložte program a spusťte jej. Ikony zdánlivě zmizely – zobrazí se pouze modré pozadí. Ikony jsou ale náhodně přiřazeny a stále existují. Vzhledem k tomu, že ikony mají stejnou barvu jako pozadí, hráč je nevidí. Přece by to byla velmi jednoduchá hra, kdyby hráč hned viděl všechny ikony!

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 4: přidejte k jednotlivým jmenovkám obslužnou rutinu události click](../ide/step-4-add-a-click-event-handler-to-each-label.md).

-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
