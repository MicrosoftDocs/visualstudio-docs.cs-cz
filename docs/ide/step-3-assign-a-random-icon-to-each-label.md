---
title: 'Krok 3: přiřazení náhodné ikony každému popisku'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29cb8d4b94b812040e83c4b80a8c7c7a08831219
ms.sourcegitcommit: 6244689e742e551e7b6933959bd42df56928ece3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72516370"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: přiřazení náhodné ikony každému popisku

Pokud se ikony každou hru zobrazí ve stejných buňkách, není to zrovna náročné. Aby k tomu nedocházelo, přiřaďte ikony náhodně k ovládacím prvkům popisku ve formuláři pomocí metody `AssignIconsToSquares()`.

## <a name="to-assign-a-random-icon-to-each-label"></a>Přiřazení náhodné ikony každému popisku

1. Před přidáním následujícího kódu se zamyslete nad tím, jak metoda funguje. Je k dispozici nové klíčové slovo: C# `foreach` v a `For Each` v Visual Basic. (Jeden z řádků je záměrně jako komentář, což je vysvětleno na konci této procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Programming jazykové řízení pro ](../ide/media/docs-programming-language-control.png) Docs.Microsoft.com

2. Přidejte metodu `AssignIconsToSquares()`, jak je znázorněno v předchozím kroku. Můžete ji umístit hned pod kód, který jste přidali v [kroku 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak bylo zmíněno dříve, je něco nového ve vaší `AssignIconsToSquares()` metodě: `foreach` smyčka C# v a `For Each` v Visual Basic. @No__t_0 cyklus můžete použít kdykoli, když chcete provést stejnou akci několikrát. V takovém případě chcete spustit stejné příkazy pro každý popisek na <xref:System.Windows.Forms.TableLayoutPanel>, jak je vysvětleno v následujícím kódu. První řádek vytvoří proměnnou s názvem `control`, která každý ovládací prvek uloží po jednom v okamžiku, kdy tento ovládací prvek obsahuje příkazy ve smyčce, která je v něm spuštěna.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > Názvy „iconLabel“ a „ovládací prvek“ se používají, protože jsou popisné. Tyto názvy můžete nahradit libovolnými názvy a kód by měl pracovat přesně stejně, dokud nezměníte název v každém výroku uvnitř smyčky.

     Metoda `AssignIconsToSquares()` projde každým ovládacím prvkem popisku v kontejneru TableLayoutPanel a provede stejné příkazy pro každý z nich. Tyto příkazy vyžádají náhodnou ikonu ze seznamu, který jste přidali v [kroku 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (To je důvod, proč jste do seznamu zahrnuli dvě ikony, takže by existovala dvojice ikon přiřazených k náhodným ovládacím prvkům Label.)

     Podrobnější informace najdete v kódu, který se spouští ve `foreach` nebo `For Each` smyčce. Tento kód je reprodukován zde.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     První řádek převede proměnnou **ovládacího prvku** na popisek s názvem **iconLabel**. Řádek následuje po příkazu `if`, který kontroluje, zda byl převod pracoval. Pokud převod funguje, příkazy v příkazu `if` se spustí. (Jak se můžete vrátit z předchozích kurzů, příkaz `if` slouží k vyhodnocení jakékoliv podmínky, kterou zadáte.) První řádek v příkazu `if` vytvoří proměnnou s názvem **randomNumber** , která obsahuje náhodné číslo, které odpovídá jedné z položek v seznamu ikony. K tomuto účelu používá metodu <xref:System.Random.Next> objektu <xref:System.Random>, který jste vytvořili dříve. Metoda `Next` vrátí náhodné číslo. Tento řádek používá také vlastnost <xref:System.Collections.Generic.List%601.Count> seznamu **ikony** k určení rozsahu, ze kterého se má zvolit náhodné číslo. Další řádek přiřadí jednu položku seznamu ikon k vlastnosti <xref:System.Windows.Forms.Label.Text> popisku. Komentovaný řádek je vysvětlen později v tomto tématu. Nakonec poslední řádek v příkazu `if` odebere ze seznamu ikonu, která byla přidána do formuláře.

     Nezapomeňte, že pokud si nejste jisti, co dělá některá část kódu, můžete umístit ukazatel myši nad prvek kódu a přečíst si zobrazený popisek. Můžete také krokovat po řádcích kódu, zatímco je program spuštěn pomocí ladicího programu sady Visual Studio. Další informace najdete v tématu [návody: krok s ladicím programem v aplikaci Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) nebo [Procházení kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md) .

3. Chcete-li vyplnit herní panel ikonami, je třeba zavolat metodu `AssignIconsToSquares()` hned po spuštění programu. Pokud používáte C#, přidejte příkaz hned pod volání metody `InitializeComponent()` v_konstruktoru_ **Form1**, aby formulář zavolal vaši novou metodu pro nastavení před zobrazením. Konstruktory jsou volány při vytváření nového objektu, například třídy nebo struktury. Další informace naleznete v tématu [konstruktory (C# Průvodce programováním)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) nebo [Použití konstruktorů a destruktorů](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) v Visual Basic.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Pro Visual Basic přidejte do metody `Form1_Load` volání metody `AssignIconsToSquares()`, aby kód vypadal jako následující.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Uložte program a spusťte jej. Měl by se zobrazit formulář s náhodnými ikonami přiřazenými každému popisku.

5. Ukončete program a znovu jej spusťte. Všimněte si, že každému popisku jsou přiřazeny jiné ikony, viz následující obrázek.

     ![Matching hry s náhodnými ikonami ](../ide/media/express_tut4step3.png)<br/>
*Porovnávací hra s náhodnými ikonami*

     Ikony jsou nyní viditelné, protože jste je neskryli. Pokud je chcete skrýt z přehrávače, můžete nastavit vlastnost **ForeColor** každé jmenovky na stejnou barvu jako vlastnost **BackColor** .

    > [!TIP]
    > Dalším způsobem, jak skrýt ovládací prvky jako popisky, je nastavit vlastnost **Visible** na **hodnotu false (NEPRAVDA**).

6. Chcete-li skrýt ikony, zastavte program a odstraňte značky komentářů pro řádek s komentářem kódu uvnitř smyčky `For Each`.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Na řádku nabídek klikněte na tlačítko **Uložit vše** a uložte program a spusťte jej. Ikony zdánlivě zmizely – zobrazí se pouze modré pozadí. Ikony jsou ale náhodně přiřazeny a stále existují. Vzhledem k tomu, že ikony mají stejnou barvu jako pozadí, hráč je nevidí. Přece by to byla velmi jednoduchá hra, kdyby hráč hned viděl všechny ikony!

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 2: Přidání náhodného objektu a seznamu ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
