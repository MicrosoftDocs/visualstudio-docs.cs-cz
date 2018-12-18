---
title: 'Krok 2: Přidejte náhodný objekt a seznam ikon | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2740e61de964f3b0c72f44e9a5c11018894c4fe0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226652"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2: Přidejte náhodný objekt a seznam ikon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kroku vytvoříte sadu odpovídajících symbolů pro hru. Každý symbol je přidán do dvou náhodných buněk v kontejneru TableLayoutPanel ve formuláři. Chcete-li to provést pomocí dvou `new` příkazy k vytvoření dvou objektů. První je `Random` objektů, jako je ten, který jste použili ve hře matematický kvíz. V tomto kódu slouží k náhodnému výběru buněk v kontejneru TableLayoutPanel. Druhý objekt, který může být pro vás nová, se `List` objekt, který se používá k ukládání náhodně zvolených symbolů.  
  
### <a name="to-add-a-random-object-and-a-list-of-icons"></a>Přidání náhodného objektu a seznamu ikon  
  
1.  V **Průzkumníka řešení**, zvolte **Form1.cs** Pokud používáte jazyk Visual C# nebo **Form1.vb** Pokud používáte jazyk Visual Basic a pak na panelu nabídek zvolte **zobrazení** , **Kód**. Jako alternativu můžete použít **F7** klíče (nebo poklikáním) **Form1** v **Průzkumníka řešení**.  
  
     Zobrazí se modul kódu pro Form1.  
  
2.  Do stávajícího kódu přidejte následující kód.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#1)]  
  
     Pokud používáte jazyk Visual C#, nezapomeňte jej vložit kód za otevírající složenou závorku a hned za deklaraci třídy (`public partial class Form1 : Form`). Pokud používáte jazyk Visual Basic, umístěte kód hned za deklaraci třídy (`Public Class Form1`).  
  
3.  Při přidávání `List` objektu, Všimněte si, že **IntelliSense** okno, které se otevře. Následuje příklad pro jazyk Visual C#, ale podobný text se zobrazí také při přidávání seznamu v jazyce Visual Basic.  
  
     ![Okno Vlastnosti zobrazující klikněte na událost](../ide/media/express-listintellisense.png "Express_ListIntellisense")  
Okno IntelliSense  
  
    > [!NOTE]
    >  Okno technologie Intellisense se zobrazí pouze v případě, že kód zadáte ručně. Pokud kód zkopírujete a vložíte, nezobrazí se.  
  
     Prohlédnete-li si kód (a poznámky) v malých oddílech, snadněji jim porozumíte. Programy mohou používat `List` objekty ke sledování mnoho různých typů položek. Seznam může obsahovat čísla, hodnoty pravda/nepravda, text nebo jiné objekty. Může probíhat dokonce `List` objekt, který obsahuje jiné `List` objekty. Položky v seznamu se nazývají *prvky*, a každý seznam obsahuje pouze jeden typ prvku. Takže seznam čísel může obsahovat pouze čísla – nelze na něj přidat text. Podobně nelze přidat čísla na seznam hodnot pravda/nepravda.  
  
     Při vytváření `List` pomocí `new` příkaz, musíte určit druh dat chcete do ní uložte. To je důvod, proč popis tlačítka v horní části **IntelliSense** okno zobrazí typy prvků v seznamu. Kromě toho, co je `List<string>` (v jazyce Visual C#) a `List(Of String)` (v jazyce Visual Basic) znamená, že: je `List` objekt, který obsahuje prvky `string` datového typu. Řetězec je program používá k uložení textu, který je co popis tlačítka vpravo **IntelliSense** vám sděluje okno.  
  
4.  Zamyslete se nad tím, proč je nutné v jazyce Visual Basic nejprve vytvořit dočasné pole, ale v jazyce Visual C# lze seznam vytvořit pomocí jednoho příkazu. Důvodem je, že jazyk Visual C# má *inicializátory kolekce*, které připraví seznam na přijetí hodnot. V jazyce Visual Basic můžete použít inicializátor kolekce. Avšak z důvodu kompatibility s předchozí verzí jazyka Visual Basic doporučujeme použít předchozí kód.  
  
     Při použití inicializátoru kolekce s `new` příkazem za nové `List` je vytvořen objekt, jej program vyplní daty, které jste zadali uvnitř složených závorek. V tomto případě získáte seznam řetězců s názvem **ikony**, a tento seznam bude inicializován tak, aby obsahoval šestnáct řetězců. Každý z těchto řetězců je jedno písmeno a všechny odpovídají ikonám, které budou v popiscích. Hra tak bude obsahovat pár vykřičníků, pár velkých písmen N, pár čárek atd. (Pokud jsou tyto znaky nastaveny na písmo Webdings, zobrazí se jako symboly, například jako autobus, kolo, pavouk a atd.) Vaše `List` objektu bude mít dohromady šestnáct řetězců ve všech, jeden pro každou buňku na panelu TableLayoutPanel.  
  
    > [!NOTE]
    >  V jazyce Visual Basic získáte stejný výsledek, ale nejprve jsou řetězce vloženy do přechodného pole, které je pak převedeno do `List` objektu. Pole je podobné seznamu, s výjimkou, že pole jsou například vytvářena s pevnou velikostí. Seznamy lze zmenšit a zvětšit podle potřeby, což je v tomto programu důležité.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 3: přiřazení náhodné ikony pro každý popisek](../ide/step-3-assign-a-random-icon-to-each-label.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 1: Vytvořte projekt a přidat tabulku do vašeho formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).



