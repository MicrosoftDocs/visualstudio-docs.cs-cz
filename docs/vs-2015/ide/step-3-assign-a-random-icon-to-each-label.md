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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671828"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Krok 3: Přiřaďte jednotlivým jmenovkám náhodné ikony
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud se ikony každou hru zobrazí ve stejných buňkách, není to zrovna náročné. Aby k tomu nedocházelo, přiřaďte ikony náhodně k ovládacím prvkům popisku ve formuláři pomocí `AssignIconsToSquares()` metody.

### <a name="to-assign-a-random-icon-to-each-label"></a>Přiřazení náhodné ikony každému popisku

1. Před přidáním následujícího kódu se zamyslete nad tím, jak metoda funguje. Existuje nové klíčové slovo: `foreach` v jazyce Visual C# a `For Each` v Visual Basic. (Jeden z řádků je záměrně jako komentář, což je vysvětleno na konci této procedury.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]

2. Přidejte `AssignIconsToSquares()` metodu, jak je znázorněno v předchozím kroku. Můžete ji umístit hned pod kód, který jste přidali v [kroku 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Jak bylo zmíněno dříve, v metodě je něco nového `AssignIconsToSquares()` : `foreach` smyčka v jazyce Visual C# a `For Each` v Visual Basic. Smyčku můžete použít `For Each` kdykoli, když chcete provést stejnou akci několikrát. V tomto případě chcete spustit stejné příkazy pro každý popisek ve vašem kontejneru TableLayoutPanel podle popisu následujícím kódem. První řádek vytvoří proměnnou s názvem `control` , která ukládá každý ovládací prvek po jednom v okamžiku, kdy tento ovládací prvek obsahuje příkazy ve smyčce, která je na něm spuštěna.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]

    > [!NOTE]
    > Názvy „iconLabel“ a „ovládací prvek“ se používají, protože jsou popisné. Tyto názvy můžete nahradit libovolnými názvy a kód by měl pracovat přesně stejně, dokud nezměníte název v každém výroku uvnitř smyčky.

     `AssignIconsToSquares()`Metoda projde každým ovládacím prvkem popisku v kontejneru TableLayoutPanel a provede stejné příkazy pro každý z nich. Tyto příkazy vyžádají náhodnou ikonu ze seznamu, který jste přidali v [kroku 2: přidejte náhodný objekt a seznam ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (To je důvod, proč jste zahrnuli dvě z každé ikony v seznamu, aby se spárovaly ikony přiřazené k náhodnému ovládacímu prvku popisku.)

     Podrobnější informace najdete v kódu, který se spouští `foreach` uvnitř `For Each` smyčky nebo. Tento kód je reprodukován zde.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]

     První řádek převede `control` proměnnou na popisek s názvem `iconLabel` . Řádek následuje po `if` příkazu, který zkontroluje, že se převod osvědčil. Pokud převod funguje, příkazy v `if` příkazu se spustí. (Jak se můžete vrátit z předchozích kurzů, `if` příkaz se používá k vyhodnocení libovolné podmínky, kterou zadáte.) První řádek v `if` příkazu vytvoří proměnnou s názvem `randomNumber` , která obsahuje náhodné číslo, které odpovídá jedné z položek v seznamu ikony. K tomu slouží `Next` Metoda `Random` objektu, který jste vytvořili dříve. `Next`Metoda vrátí náhodné číslo. Tento řádek používá také `Count` vlastnost `icons` seznamu k určení rozsahu, ze kterého se má zvolit náhodné číslo. Další řádek přiřadí jednu položku seznamu ikon k `Text` Vlastnosti popisku. Komentovaný řádek je vysvětlen později v tomto tématu. Nakonec se poslední řádek v `if` příkazu odebere ze seznamu ikony přidané do formuláře.

     Nezapomeňte, že pokud si nejste jisti, co dělá některá část kódu, můžete umístit ukazatel myši nad prvek kódu a přečíst si zobrazený popisek. Můžete také krokovat po řádcích kódu, zatímco je program spuštěn pomocí ladicího programu sady Visual Studio. Další informace najdete v tématu [Jak mohu: krokování s ladicím programem v aplikaci Visual Studio?](https://msdn.microsoft.com/vstudio/ee672313.aspx) nebo [Procházení kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md) .

3. Chcete-li vyplnit herní panel ikonami, je třeba zavolat `AssignIconsToSquares()` metodu ihned po spuštění programu. Pokud používáte jazyk Visual C#, přidejte příkaz hned pod volání `InitializeComponent()` metody v `Form1` *konstruktoru*, aby formulář zavolal vaši novou metodu pro nastavení před zobrazením. Konstruktory jsou volány při vytváření nového objektu, například třídy nebo struktury. Další informace naleznete v tématu [konstruktory (Průvodce programováním v C#)](https://msdn.microsoft.com/library/ace5hbzh.aspx) nebo [Použití konstruktorů a destruktorů](https://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) v Visual Basic.

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]

     Pro Visual Basic přidejte do `AssignIconsToSquares()` metody volání metody, `Form1_Load` aby kód vypadal jako následující.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Uložte program a spusťte jej. Měl by se zobrazit formulář s náhodnými ikonami přiřazenými každému popisku.

5. Ukončete program a znovu jej spusťte. Všimněte si, že každému popisku jsou přiřazeny jiné ikony, viz následující obrázek.

     ![Porovnávací hra s náhodnými ikonami](../ide/media/express-tut4step3.png "Express_Tut4Step3") Porovnávací hra s náhodnými ikonami

     Ikony jsou nyní viditelné, protože jste je neskryli. Pokud je chcete skrýt z přehrávače, můžete nastavit vlastnost každé jmenovky `Forecolor` na stejnou barvu jako `BackColor` vlastnost.

    > [!TIP]
    > Dalším způsobem, jak skrýt ovládací prvky jako popisky, je nastavit jejich vlastnost **Visible** na `False` .

6. Chcete-li skrýt ikony, zastavte program a odeberte značky komentářů pro řádek s komentářem kódu uvnitř `For Each` smyčky.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]

7. Na řádku nabídek klikněte na tlačítko **Uložit vše** a uložte program a spusťte jej. Ikony zdánlivě zmizely – zobrazí se pouze modré pozadí. Ikony jsou ale náhodně přiřazeny a stále existují. Vzhledem k tomu, že ikony mají stejnou barvu jako pozadí, hráč je nevidí. Přece by to byla velmi jednoduchá hra, kdyby hráč hned viděl všechny ikony!

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 4: Přidání obslužné rutiny události Click do každého popisku](../ide/step-4-add-a-click-event-handler-to-each-label.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 2: Přidání náhodného objektu a seznamu ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
