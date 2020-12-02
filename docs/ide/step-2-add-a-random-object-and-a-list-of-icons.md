---
title: 'Krok 2: přidejte náhodný objekt a seznam ikon'
description: Naučte se vytvořit sadu vyhovujících symbolů pro hru.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1018b390f6ebbf67fab88554aa85fe6a8ecec88d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480691"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2: přidejte náhodný objekt a seznam ikon

V tomto kroku vytvoříte sadu odpovídajících symbolů pro hru. Každý symbol je přidán do dvou náhodných buněk v kontejneru TableLayoutPanel ve formuláři. K tomu použijte dva `new` příkazy k vytvoření dvou objektů. První je <xref:System.Random> objekt, jako ten, který jste použili ve hře matematického kvízu. V tomto kódu slouží k náhodnému výběru buněk v kontejneru TableLayoutPanel. Druhý objekt, který může být pro vás nový, je objekt, <xref:System.Collections.Generic.List%601> který se používá k ukládání náhodně zvolených symbolů.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Přidání náhodného objektu a seznamu ikon

1. V **Průzkumník řešení** zvolte *Form1.cs* , pokud používáte jazyk C# nebo *Form1. vb* , pokud používáte Visual Basic a pak na panelu nabídek zvolte **Zobrazit**  >  **kód**. Alternativně můžete zvolit klávesu **F7** nebo dvakrát kliknout na položku **Form1** v **Průzkumník řešení**.

     Zobrazí se modul kódu pro Form1.

2. Do stávajícího kódu přidejte následující kód.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment kódu jazyka C# nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

      Pokud používáte jazyk C#, nezapomeňte vložit kód za levou složenou závorku a hned za deklarací třídy ( `public partial class Form1 : Form` ). Pokud používáte Visual Basic, vložte kód hned za deklaraci třídy ( `Public Class Form1` ).

3. Při přidávání objektu seznamu si všimněte okna **technologie IntelliSense** , které se otevře. Následuje příklad v jazyce C#, ale podobný text se zobrazí při přidání seznamu do Visual Basic.

     ![Okno Vlastnosti zobrazující událost Click](../ide/media/express_listintellisense.png)<br/>*Okno *_IntelliSense_**

    > [!NOTE]
    > Okno technologie IntelliSense se zobrazí pouze v případě, že zadáte kód ručně. Pokud kód zkopírujete a vložíte, nezobrazí se.

     Prohlédnete-li si kód (a poznámky) v malých oddílech, snadněji jim porozumíte. Programy mohou používat objekty seznamu k udržení přehledu o mnoha různých typech položek. Seznam může obsahovat čísla, hodnoty pravda/nepravda, text nebo jiné objekty. Můžete dokonce mít i objekt seznamu, který obsahuje jiné objekty seznamu. Položky v seznamu se nazývají prvky a každý seznam obsahuje pouze jeden typ elementu. Takže seznam čísel může obsahovat pouze čísla – nelze na něj přidat text. Podobně nelze přidat čísla na seznam hodnot pravda/nepravda.

     Když vytvoříte `List` objekt pomocí `new` příkazu, je nutné zadat druh dat, která chcete v něm Uložit. To je důvod, proč popis tlačítka v horní části okna **technologie IntelliSense** zobrazuje typy prvků v seznamu. To je také to, co `List<string>` (v jazyce C#) a `List(Of String)` (v Visual Basic) znamená: Jedná se o `List` objekt, který obsahuje prvky `string` datového typu. Řetězec je to, co program používá k ukládání textu, což je to, co vám popis tlačítka napravo od okna **technologie IntelliSense** oznamuje.

4. Zvažte, proč je nutné nejprve vytvořit dočasné pole Visual Basic, ale v jazyce C# lze vytvořit seznam pomocí jednoho příkazu. Je to proto, že jazyk C# obsahuje *inicializátory kolekce*, které připravují seznam pro přijímání hodnot. V jazyce Visual Basic můžete použít inicializátor kolekce. Avšak z důvodu kompatibility s předchozí verzí jazyka Visual Basic doporučujeme použít předchozí kód.

     Použijete-li inicializátor kolekce s `new` příkazem, poté, co je vytvořen nový objekt seznamu, program jej vyplní daty, která jste zadali uvnitř složených závorek. V tomto případě získáte seznam řetězců s názvem ikony a tento seznam bude inicializován tak, aby obsahoval šestnáct řetězců. Každý z těchto řetězců je jedno písmeno a všechny odpovídají ikonám, které budou v popiscích. Hra tak bude obsahovat pár vykřičníků, pár velkých písmen N, pár čárek atd. (Pokud jsou tyto znaky nastavené na Písmo Webdings, zobrazí se jako symboly, jako je například sběrnice, kolo, Spider atd.) Váš objekt seznamu bude mít šestnáct řetězců ve všech, jeden pro každou buňku na panelu TableLayoutPanel.

    > [!NOTE]
    > V Visual Basic získáte stejný výsledek, ale nejprve jsou řetězce vloženy do dočasného pole, které je následně převedeno na objekt seznamu. Pole je podobné seznamu, s výjimkou, že pole jsou například vytvářena s pevnou velikostí. Seznamy lze zmenšit a zvětšit podle potřeby, což je v tomto programu důležité.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si část [**Krok 3: přiřazení náhodné ikony každému popisku**](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si téma [Krok 1: vytvoření projektu a přidání tabulky do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
