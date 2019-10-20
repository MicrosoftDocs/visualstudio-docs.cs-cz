---
title: 'Krok 3: přiřazení náhodné ikony každému popisku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4382a450051b7626a5eb5e29bf2ce4e78f6eceda
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671828"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: Přiřaďte jednotlivým jmenovkám náhodné ikony
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud se ikony každou hru zobrazí ve stejných buňkách, není to zrovna náročné. Aby k tomu nedocházelo, přiřaďte ikony náhodně k ovládacím prvkům popisku ve formuláři pomocí metody `AssignIconsToSquares()`.

### <a name="to-assign-a-random-icon-to-each-label"></a>Přiřazení náhodné ikony každému popisku

1. Před přidáním následujícího kódu se zamyslete nad tím, jak metoda funguje. Je k dispozici nové klíčové slovo: `foreach` C# v vizuálu a `For Each` v Visual Basic. (Jeden z řádků je záměrně jako komentář, což je vysvětleno na konci této procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]

2. Přidejte metodu `AssignIconsToSquares()`, jak je znázorněno v předchozím kroku. Můžete ji umístit hned pod kód, který jste přidali v [kroku 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak bylo zmíněno dříve, je něco nového ve vaší metodě `AssignIconsToSquares()`: `foreach` smyčka v C# jazyce Visual a `For Each` v Visual Basic. @No__t_0 cyklus můžete použít kdykoli, když chcete provést stejnou akci několikrát. V tomto případě chcete spustit stejné příkazy pro každý popisek ve vašem kontejneru TableLayoutPanel podle popisu následujícím kódem. První řádek vytvoří proměnnou s názvem `control`, která každý ovládací prvek uloží po jednom v okamžiku, kdy tento ovládací prvek obsahuje příkazy ve smyčce, která je v něm spuštěna.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]

    > [!NOTE]
    > Názvy „iconLabel“ a „ovládací prvek“ se používají, protože jsou popisné. Tyto názvy můžete nahradit libovolnými názvy a kód by měl pracovat přesně stejně, dokud nezměníte název v každém výroku uvnitř smyčky.

     Metoda `AssignIconsToSquares()` projde každým ovládacím prvkem popisku v kontejneru TableLayoutPanel a provede stejné příkazy pro každý z nich. Tyto příkazy vyžádají náhodnou ikonu ze seznamu, který jste přidali v [kroku 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (To je důvod, proč jste zahrnuli dvě z každé ikony v seznamu, aby se spárovaly ikony přiřazené k náhodnému ovládacímu prvku popisku.)

     Podrobnější informace najdete v kódu, který se spouští ve `foreach` nebo `For Each` smyčce. Tento kód je reprodukován zde.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]

     První řádek převede proměnnou `control` na popisek s názvem `iconLabel`. Řádek následuje po příkazu `if`, který kontroluje, zda byl převod pracoval. Pokud převod funguje, příkazy v příkazu `if` se spustí. (Jak se můžete vrátit z předchozích kurzů, příkaz `if` slouží k vyhodnocení jakékoliv podmínky, kterou zadáte.) První řádek v příkazu `if` vytvoří proměnnou s názvem `randomNumber`, která obsahuje náhodné číslo, které odpovídá jedné z položek v seznamu ikony. K tomuto účelu používá metodu `Next` objektu `Random`, který jste vytvořili dříve. Metoda `Next` vrátí náhodné číslo. Tento řádek používá také vlastnost `Count` seznamu `icons` k určení rozsahu, ze kterého se má zvolit náhodné číslo. Další řádek přiřadí jednu položku seznamu ikon k vlastnosti `Text` popisku. Komentovaný řádek je vysvětlen později v tomto tématu. Nakonec poslední řádek v příkazu `if` odebere ze seznamu ikonu, která byla přidána do formuláře.

     Nezapomeňte, že pokud si nejste jisti, co dělá některá část kódu, můžete umístit ukazatel myši nad prvek kódu a přečíst si zobrazený popisek. Můžete také krokovat po řádcích kódu, zatímco je program spuštěn pomocí ladicího programu sady Visual Studio. Další informace najdete v tématu [Jak mohu: krokování s ladicím programem v aplikaci Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) nebo [Procházení kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md) .

3. Chcete-li vyplnit herní panel ikonami, je třeba zavolat metodu `AssignIconsToSquares()` hned po spuštění programu. Pokud používáte vizuál C#, přidejte příkaz hned pod volání metody `InitializeComponent()` v*konstruktoru*`Form1`, aby formulář zavolal vaši novou metodu pro nastavení před zobrazením. Konstruktory jsou volány při vytváření nového objektu, například třídy nebo struktury. Další informace naleznete v tématu [konstruktory (C# Průvodce programováním)](https://msdn.microsoft.com/library/ace5hbzh.aspx) nebo [Použití konstruktorů a destruktorů](https://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) v Visual Basic.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]

     Pro Visual Basic přidejte do metody `Form1_Load` volání metody `AssignIconsToSquares()`, aby kód vypadal jako následující.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Uložte program a spusťte jej. Měl by se zobrazit formulář s náhodnými ikonami přiřazenými každému popisku.

5. Ukončete program a znovu jej spusťte. Všimněte si, že každému popisku jsou přiřazeny jiné ikony, viz následující obrázek.

     ![Porovnávací hra s náhodnými ikonami](../ide/media/express-tut4step3.png "Express_Tut4Step3") Porovnávací hra s náhodnými ikonami

     Ikony jsou nyní viditelné, protože jste je neskryli. Pokud je chcete skrýt z přehrávače, můžete nastavit vlastnost `Forecolor` popisku na stejnou barvu jako vlastnost `BackColor`.

    > [!TIP]
    > Dalším způsobem, jak skrýt ovládací prvky jako popisky, je nastavit jejich vlastnost **Visible** na `False`.

6. Chcete-li skrýt ikony, zastavte program a odstraňte značky komentářů pro řádek s komentářem kódu uvnitř smyčky `For Each`.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]

7. Na řádku nabídek klikněte na tlačítko **Uložit vše** a uložte program a spusťte jej. Ikony zdánlivě zmizely – zobrazí se pouze modré pozadí. Ikony jsou ale náhodně přiřazeny a stále existují. Vzhledem k tomu, že ikony mají stejnou barvu jako pozadí, hráč je nevidí. Přece by to byla velmi jednoduchá hra, kdyby hráč hned viděl všechny ikony!

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 2: Přidání náhodného objektu a seznamu ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
