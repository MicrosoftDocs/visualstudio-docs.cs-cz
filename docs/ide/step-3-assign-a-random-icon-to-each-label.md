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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80472626"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: Přiřazení náhodné ikony každému popisku

Pokud se ikony každou hru zobrazí ve stejných buňkách, není to zrovna náročné. Aby k tomu nedocházelo, přiřaďte ikony náhodně k ovládacím prvkům popisku ve formuláři pomocí `AssignIconsToSquares()` metody.

## <a name="to-assign-a-random-icon-to-each-label"></a>Přiřazení náhodné ikony každému popisku

1. Před přidáním následujícího kódu se zamyslete nad tím, jak metoda funguje. Existuje nové klíčové slovo: `foreach` v jazyce C# a `For Each` v Visual Basic. (Jeden z řádků je záměrně jako komentář, což je vysvětleno na konci této procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment kódu jazyka C# nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Přidejte `AssignIconsToSquares()` metodu, jak je znázorněno v předchozím kroku. Můžete ji umístit hned pod kód, který jste přidali v [kroku 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak bylo zmíněno dříve, je něco nového ve vaší `AssignIconsToSquares()` metodě: `foreach` smyčka v jazyce C# a `For Each` v Visual Basic. Smyčku můžete použít `For Each` kdykoli, když chcete provést stejnou akci několikrát. V tomto případě chcete spustit stejné příkazy pro každý popisek na <xref:System.Windows.Forms.TableLayoutPanel> , jak je vysvětleno v následujícím kódu. První řádek vytvoří proměnnou s názvem `control` , která ukládá každý ovládací prvek po jednom v okamžiku, kdy tento ovládací prvek obsahuje příkazy ve smyčce, která je na něm spuštěna.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > Názvy „iconLabel“ a „ovládací prvek“ se používají, protože jsou popisné. Tyto názvy můžete nahradit libovolnými názvy a kód by měl pracovat přesně stejně, dokud nezměníte název v každém výroku uvnitř smyčky.

     `AssignIconsToSquares()`Metoda projde každým ovládacím prvkem popisku v kontejneru TableLayoutPanel a provede stejné příkazy pro každý z nich. Tyto příkazy vyžádají náhodnou ikonu ze seznamu, který jste přidali v [kroku 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). Jako připomenutí je každá z těchto ikon písmenem písma Webdings, což je důvod, proč se v této metodě vyjadřují jako text. Do seznamu jste zahrnuli dvě z každé ikony, takže by existovala dvojice ikon přiřazených k náhodným ovládacím prvkům Label.

     Podrobnější informace najdete v kódu, který se spouští `foreach` uvnitř `For Each` smyčky nebo. Tento kód je reprodukován zde.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     První řádek převede proměnnou **ovládacího prvku** na popisek s názvem **iconLabel**. Řádek následuje po `if` příkazu, který zkontroluje, že se převod osvědčil. Pokud převod funguje, příkazy v `if` příkazu se spustí. (Jak se můžete vrátit z předchozích kurzů, `if` příkaz se používá k vyhodnocení libovolné podmínky, kterou zadáte.) První řádek v `if` příkazu vytvoří proměnnou s názvem **randomNumber** , která obsahuje náhodné číslo, které odpovídá jedné z položek v seznamu ikony. K tomu slouží <xref:System.Random.Next> Metoda <xref:System.Random> objektu, který jste vytvořili dříve. `Next`Metoda vrátí náhodné číslo. Tento řádek používá také <xref:System.Collections.Generic.List%601.Count> vlastnost seznamu **ikony** k určení rozsahu, ze kterého se má zvolit náhodné číslo. Další řádek přiřadí jednu položku seznamu ikon k <xref:System.Windows.Forms.Label.Text> Vlastnosti popisku. Komentovaný řádek je vysvětlen později v tomto tématu. Nakonec se poslední řádek v `if` příkazu odebere ze seznamu ikony přidané do formuláře.

     Nezapomeňte, že pokud si nejste jisti, co dělá některá část kódu, můžete umístit ukazatel myši nad prvek kódu a přečíst si zobrazený popisek. Můžete také krokovat po řádcích kódu, zatímco je program spuštěn pomocí ladicího programu sady Visual Studio. Další informace najdete v tématu [návody: krok s ladicím programem v aplikaci Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) nebo [Procházení kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md) .

3. Chcete-li vyplnit herní panel ikonami, je třeba zavolat `AssignIconsToSquares()` metodu ihned po spuštění programu. Pokud používáte jazyk C#, přidejte příkaz hned pod volání `InitializeComponent()` metody v _konstruktoru_ **Form1** , aby formulář zavolal vaši novou metodu pro nastavení před zobrazením. Konstruktory jsou volány při vytváření nového objektu, například třídy nebo struktury. Další informace naleznete v tématu [konstruktory (Průvodce programováním v C#)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) nebo [Použití konstruktorů a destruktorů](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) v Visual Basic.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Pro Visual Basic přidejte do `AssignIconsToSquares()` metody volání metody, `Form1_Load` aby kód vypadal jako následující.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Uložte program a spusťte jej. Měl by se zobrazit formulář s náhodnými ikonami přiřazenými každému popisku. 

5. Ukončete program a znovu jej spusťte. Všimněte si, že každému popisku jsou přiřazeny jiné ikony, viz následující obrázek. 

     ![Porovnávací hra s náhodnými ikonami](../ide/media/express_tut4step3.png)<br/>
*Porovnávací hra s náhodnými ikonami*

     Ikony jsou nyní viditelné, protože jste je neskryli. Pokud je chcete skrýt z přehrávače, můžete nastavit vlastnost **ForeColor** každé jmenovky na stejnou barvu jako vlastnost **BackColor** .

6. Chcete-li skrýt ikony, zastavte program a odeberte značky komentářů pro řádek s komentářem kódu uvnitř `For Each` smyčky.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Na řádku nabídek klikněte na tlačítko **Uložit vše** a uložte program a spusťte jej. Ikony zdánlivě zmizely – zobrazí se pouze modré pozadí. Ikony jsou ale náhodně přiřazeny a stále existují. Vzhledem k tomu, že ikony mají stejnou barvu jako pozadí, hráč je nevidí. Přece by to byla velmi jednoduchá hra, kdyby hráč hned viděl všechny ikony!

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md)**.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 2: Přidání náhodného objektu a seznamu ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
