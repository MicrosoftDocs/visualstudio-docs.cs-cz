---
title: 'Krok 3: Přiřaďte jednotlivým jmenovkám náhodné ikony | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ce8047cbdf6d487a1b4ff00ae99c617a9548fca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298776"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: Přiřaďte jednotlivým jmenovkám náhodné ikony
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud se ikony každou hru zobrazí ve stejných buňkách, není to zrovna náročné. Abyste tomu předešli, přiřaďte ikony náhodně k ovládacím prvkům popisku ve formuláři pomocí `AssignIconsToSquares()` metody.  
  
### <a name="to-assign-a-random-icon-to-each-label"></a>Přiřazení náhodné ikony každému popisku  
  
1.  Před přidáním následujícího kódu se zamyslete nad tím, jak metoda funguje. Existuje nové klíčové slovo: `foreach` v jazyce Visual C# a `For Each` v jazyce Visual Basic. (Jeden z řádků je záměrně jako komentář, což je vysvětleno na konci této procedury.)  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]  
  
2.  Přidat `AssignIconsToSquares()` způsob, jak je znázorněno v předchozím kroku. Můžete ji umístit přímo pod kód, který jste přidali v [krok 2: Add Random Object and List of Icons](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
     Jak bylo zmíněno výše, je něco nového v vaše `AssignIconsToSquares()` metoda: `foreach` smyčky v jazyce Visual C# a `For Each` v jazyce Visual Basic. Můžete použít `For Each` smyčky kdykoli chcete provést stejnou akci více než jednou. V tomto případě chcete spustit stejné příkazy pro každý popisek ve vašem kontejneru TableLayoutPanel podle popisu následujícím kódem. První řádek vytvoří proměnnou s názvem `control` , který ukládá vždy jeden ovládací prvek v době při, výroky ve smyčce na něm spustily.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]  
  
    > [!NOTE]
    >  Názvy „iconLabel“ a „ovládací prvek“ se používají, protože jsou popisné. Tyto názvy můžete nahradit libovolnými názvy a kód by měl pracovat přesně stejně, dokud nezměníte název v každém výroku uvnitř smyčky.  
  
     `AssignIconsToSquares()` Metoda iteruje jednotlivé ovládací prvky popisku v kontejneru TableLayoutPanel a pro každý z nich spustí stejný příkaz. Tyto příkazy vyžádají náhodnou ikonu ze seznamu, který jste přidali v [krok 2: Add Random Object and List of Icons](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (To je důvod, proč jste zahrnuli dvě z každé ikony v seznamu, aby se spárovaly ikony přiřazené k náhodnému ovládacímu prvku popisku.)  
  
     Podívejte se důkladněji na kód, který běží v rámci `foreach` nebo `For Each` smyčky. Tento kód je reprodukován zde.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]  
  
     První řádek převede `control` proměnné pro popisek s názvem `iconLabel`. Následující řádek, který je `if` příkaz, který zkontroluje, ujistěte se, že převod pracovali. Pokud byl převod úspěšný, příkazy `if` příkaz spustit. (Jak si pravděpodobně pamatujete z předchozích tutoriálů, `if` prohlášení se používá k vyhodnocení libovolné podmínky.) První řádek `if` příkaz vytvoří proměnnou s názvem `randomNumber` , která obsahuje náhodné číslo, které odpovídá jedné z položek v seznamu ikon. K tomu použije `Next` metodu `Random` objekt, který jste vytvořili dříve. `Next` Metoda vrátí náhodné číslo. Tento řádek také používá `Count` vlastnost `icons` seznamu k určení rozsahu, ze kterého se náhodné číslo vybere. Další řádek přiřadí jednu ikony položky seznamu `Text` popisku. Komentovaný řádek je vysvětlen později v tomto tématu. Nakonec poslední řádek v `if` příkaz odebere ze seznamu ikonu, která byla přidána do formuláře.  
  
     Nezapomeňte, že pokud si nejste jisti, co dělá některá část kódu, můžete umístit ukazatel myši nad prvek kódu a přečíst si zobrazený popisek. Můžete také krokovat po řádcích kódu, zatímco je program spuštěn pomocí ladicího programu sady Visual Studio. Zobrazit [návody: krokování s ladicím programem v sadě Visual Studio?](http://msdn.microsoft.com/vstudio/ee672313.aspx) nebo [procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md) Další informace.  
  
3.  Pokud chcete zaplnit hrací plochu ikonami, je potřeba volat `AssignIconsToSquares()` metoda co nejdříve po spuštění programu. Pokud používáte jazyk Visual C#, přidejte příkaz pod volání `InitializeComponent()` metodu `Form1` *konstruktor*, aby formulář volal vaši novou metodu pro vlastní nastavení, než se zobrazí. Konstruktory jsou volány při vytváření nového objektu, například třídy nebo struktury. Zobrazit [konstruktory (C# Programming Guide)](http://msdn.microsoft.com/library/ace5hbzh.aspx) nebo [používání konstruktorů a destruktorů](http://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) v jazyce Visual Basic pro další informace.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]  
  
     V jazyce Visual Basic přidejte `AssignIconsToSquares()` volání metod, které `Form1_Load` metodu tak, aby kód vypadá následovně.  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AssignIconsToSquares()  
    End Sub  
    ```  
  
4.  Uložte program a spusťte jej. Měl by se zobrazit formulář s náhodnými ikonami přiřazenými každému popisku.  
  
5.  Ukončete program a znovu jej spusťte. Všimněte si, že každému popisku jsou přiřazeny jiné ikony, viz následující obrázek.  
  
     ![Porovnávací hra s náhodnými ikonami](../ide/media/express-tut4step3.png "Express_Tut4Step3")  
Porovnávací hra s náhodnými ikonami  
  
     Ikony jsou nyní viditelné, protože jste je neskryli. Skrýt hráče, můžete nastavit každý popisek `Forecolor` vlastnost na stejnou barvu jako jeho `BackColor` vlastnost.  
  
    > [!TIP]
    >  Dalším způsobem, jak skrýt ovládací prvky jako popisky je nastavit jejich **Visible** vlastnost `False`.  
  
6.  Chcete-li skrýt ikony, ukončete program a odeberte značky komentáře komentovaného řádku kódu uvnitř `For Each` smyčky.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]  
  
7.  V panelu nabídek zvolte **Uložit vše** tlačítko uložte program a spusťte jej. Ikony zdánlivě zmizely – zobrazí se pouze modré pozadí. Ikony jsou ale náhodně přiřazeny a stále existují. Vzhledem k tomu, že ikony mají stejnou barvu jako pozadí, hráč je nevidí. Přece by to byla velmi jednoduchá hra, kdyby hráč hned viděl všechny ikony!  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 4: přidejte obslužné rutiny události Click pro každý popisek](../ide/step-4-add-a-click-event-handler-to-each-label.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 2: Add Random Object and List of Icons](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).



