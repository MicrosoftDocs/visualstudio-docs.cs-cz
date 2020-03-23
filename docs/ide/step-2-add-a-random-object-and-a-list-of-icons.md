---
title: 'Krok 2: Přidání náhodného objektu a seznamu ikon'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f4731778ebb3acbdc3bb7d9b5827c1015541d98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579418"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2: Přidání náhodného objektu a seznamu ikon

V tomto kroku vytvoříte sadu odpovídajících symbolů pro hru. Každý symbol je přidán do dvou náhodných buněk v kontejneru TableLayoutPanel ve formuláři. Chcete-li to provést, použijte dva `new` příkazy k vytvoření dvou objektů. První je <xref:System.Random> objekt, jako ten, který jste použili v matematické kvíz. V tomto kódu slouží k náhodnému výběru buněk v kontejneru TableLayoutPanel. Druhý objekt, který může být pro <xref:System.Collections.Generic.List%601> vás nový, je objekt, který se používá k uložení náhodně vybraných symbolů.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Přidání náhodného objektu a seznamu ikon

1. V **Průzkumníku řešení**zvolte *Form1.cs,* pokud používáte C#, nebo *Form1.vb,* pokud používáte Visual Basic, a potom na řádku nabídek zvolte **Zobrazit** > **kód**. Jako alternativu můžete zvolit klávesu **F7** nebo poklepat na **formulář1** v **Průzkumníku řešení**.

     Zobrazí se modul kódu pro Form1.

2. Do stávajícího kódu přidejte následující kód.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky zobrazíte fragment kódu jazyka C# nebo fragment kódu jazyka Visual Basic.<br><br>![Ovládání programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

      Pokud používáte C#, ujistěte se, že jste kód za otevření složené`public partial class Form1 : Form`závorky a těsně za deklarace třídy ( ). Pokud používáte Visual Basic, zadejte kód hned`Public Class Form1`za deklaraci třídy ( ).

3. Při přidávání objektu List si všimněte okna **IntelliSense,** které se otevře. Následuje příklad jazyka C#, ale podobný text se zobrazí při přidání seznamu v jazyce Visual Basic.

     ![Okno Vlastnosti zobrazující událost Click](../ide/media/express_listintellisense.png)<br/>***Okno IntelliSense***

    > [!NOTE]
    > Okno Technologie IntelliSense se zobrazí pouze v případě, že zadáte kód ručně. Pokud kód zkopírujete a vložíte, nezobrazí se.

     Prohlédnete-li si kód (a poznámky) v malých oddílech, snadněji jim porozumíte. Programy mohou pomocí objektů seznamu sledovat mnoho různých typů položek. Seznam může obsahovat čísla, hodnoty pravda/nepravda, text nebo jiné objekty. Můžete mít dokonce objekt seznamu, který obsahuje další objekty seznamu. Položky v seznamu se nazývají prvky a každý seznam obsahuje pouze jeden typ prvku. Takže seznam čísel může obsahovat pouze čísla – nelze na něj přidat text. Podobně nelze přidat čísla na seznam hodnot pravda/nepravda.

     Při vytváření `List` objektu `new` pomocí příkazu je třeba zadat druh dat, která chcete do něj uložit. Proto popisek v horní části okna **Technologie IntelliSense** zobrazuje typy prvků v seznamu. Také to je `List<string>` co (v jazyce C#) a `List(Of String)` (v `List` jazyce Visual `string` Basic) znamená: Je to objekt, který obsahuje prvky datového typu. Řetězec je to, co váš program používá k ukládání textu, což je to, co vám říká popisek napravo od okna **IntelliSense.**

4. Zvažte, proč v jazyce Visual Basic musí být nejprve vytvořeno dočasné pole, ale v jazyce C#, seznam lze vytvořit pomocí jednoho příkazu. Důvodem je, že jazyk C# má *inicializátory kolekce*, které připravují seznam přijímat hodnoty. V jazyce Visual Basic můžete použít inicializátor kolekce. Avšak z důvodu kompatibility s předchozí verzí jazyka Visual Basic doporučujeme použít předchozí kód.

     Při použití inicializátoru kolekce s příkazem, `new` po vytvoření nového List objektu jej program vyplní s daty, které jste zadali uvnitř složené závorky. V tomto případě získáte seznam řetězců s názvem ikony a tento seznam bude inicializován tak, aby obsahoval šestnáct řetězců. Každý z těchto řetězců je jedno písmeno a všechny odpovídají ikonám, které budou v popiscích. Hra tak bude obsahovat pár vykřičníků, pár velkých písmen N, pár čárek atd. (Pokud jsou tyto znaky nastaveny na písmo Webdings, zobrazí se jako symboly, například autobus, kolo, pavouk atd.) Objekt seznamu bude mít celkem šestnáct řetězců, jeden pro každou buňku v panelu TableLayoutPanel.

    > [!NOTE]
    > V jazyce Visual Basic získáte stejný výsledek, ale nejprve řetězce jsou vloženy do dočasného pole, které je pak převedeno na objekt seznamu. Pole je podobné seznamu, s výjimkou, že pole jsou například vytvářena s pevnou velikostí. Seznamy lze zmenšit a zvětšit podle potřeby, což je v tomto programu důležité.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kroku kurzu, [**přečtěte si postup 3: Přiřazení náhodné ikony ke každému štítku**](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 1: Vytvoření projektu a přidání tabulky do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
