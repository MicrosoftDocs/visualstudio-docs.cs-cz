---
title: 'Krok 2: přidejte náhodný objekt a seznam ikon | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7370bf956fd79f5568737af5d9a96b9c64a5316b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667303"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2: Přidejte náhodný objekt a seznam ikon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kroku vytvoříte sadu odpovídajících symbolů pro hru. Každý symbol je přidán do dvou náhodných buněk v kontejneru TableLayoutPanel ve formuláři. K tomu použijte dva `new` příkazy k vytvoření dvou objektů. První je objekt `Random`, jako ten, který jste použili ve hře matematického kvízu. V tomto kódu slouží k náhodnému výběru buněk v kontejneru TableLayoutPanel. Druhý objekt, který může být pro vás nový, je objekt `List`, který se používá k ukládání náhodně zvolených symbolů.

### <a name="to-add-a-random-object-and-a-list-of-icons"></a>Přidání náhodného objektu a seznamu ikon

1. V **Průzkumník řešení**zvolte **Form1.cs** , pokud používáte C#jazyk Visual nebo **Form1. vb** , pokud používáte Visual Basic a pak na panelu nabídek zvolte možnost **zobrazení**, **kód**. Alternativně můžete zvolit klávesu **F7** nebo dvakrát kliknout na položku **Form1** v **Průzkumník řešení**.

     Zobrazí se modul kódu pro Form1.

2. Do stávajícího kódu přidejte následující kód.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#1)]

     Pokud používáte vizuál C#, ujistěte se, že kód vložíte za levou složenou závorku a hned za deklaraci třídy (`public partial class Form1 : Form`). Pokud používáte Visual Basic, vložte kód hned za deklaraci třídy (`Public Class Form1`).

3. Při přidávání objektu `List` si všimněte okna **technologie IntelliSense** , které se otevře. Následuje příklad pro jazyk Visual C#, ale podobný text se zobrazí také při přidávání seznamu v jazyce Visual Basic.

     ![Okno Vlastnosti zobrazující událost Click](../ide/media/express-listintellisense.png "Express_ListIntellisense") Okno IntelliSense

    > [!NOTE]
    > Okno technologie Intellisense se zobrazí pouze v případě, že kód zadáte ručně. Pokud kód zkopírujete a vložíte, nezobrazí se.

     Prohlédnete-li si kód (a poznámky) v malých oddílech, snadněji jim porozumíte. Programy mohou pomocí `List` objektů sledovat mnoho různých typů položek. Seznam může obsahovat čísla, hodnoty pravda/nepravda, text nebo jiné objekty. Můžete mít i objekt `List`, který obsahuje další objekty `List`. Položky v seznamu se nazývají *prvky*a každý seznam obsahuje pouze jeden typ elementu. Takže seznam čísel může obsahovat pouze čísla – nelze na něj přidat text. Podobně nelze přidat čísla na seznam hodnot pravda/nepravda.

     Když vytvoříte objekt `List` pomocí příkazu `new`, je nutné zadat druh dat, která se mají v něm ukládat. To je důvod, proč popis tlačítka v horní části okna **technologie IntelliSense** zobrazuje typy prvků v seznamu. Také to, co `List<string>` (v jazyce Visual C#) a `List(Of String)` (v Visual Basic) znamená: Jedná se o `List` objekt, který obsahuje prvky pro `string` datový typ. Řetězec je to, co program používá k ukládání textu, což je to, co vám popis tlačítka napravo od okna **technologie IntelliSense** oznamuje.

4. Zamyslete se nad tím, proč je nutné v jazyce Visual Basic nejprve vytvořit dočasné pole, ale v jazyce Visual C# lze seznam vytvořit pomocí jednoho příkazu. Je to proto, že C# vizuální jazyk obsahuje *inicializátory kolekce*, které připravují seznam pro přijímání hodnot. V jazyce Visual Basic můžete použít inicializátor kolekce. Avšak z důvodu kompatibility s předchozí verzí jazyka Visual Basic doporučujeme použít předchozí kód.

     Použijete-li inicializátor kolekce s příkazem `new`, poté, co je vytvořen nový objekt `List`, program jej vyplní daty, která jste zadali uvnitř složených závorek. V tomto případě získáte seznam řetězců s názvem **ikony**a tento seznam bude inicializován tak, aby obsahoval šestnáct řetězců. Každý z těchto řetězců je jedno písmeno a všechny odpovídají ikonám, které budou v popiscích. Hra tak bude obsahovat pár vykřičníků, pár velkých písmen N, pár čárek atd. (Pokud jsou tyto znaky nastavené na Písmo Webdings, zobrazí se jako symboly, jako je například sběrnice, kolo, Spider atd.) Objekt `List` bude mít všechny šestnácté řetězce, jeden pro každou buňku na panelu TableLayoutPanel.

    > [!NOTE]
    > V Visual Basic získáte stejný výsledek, ale nejprve jsou řetězce vloženy do dočasného pole, které je následně převedeno na objekt `List`. Pole je podobné seznamu, s výjimkou, že pole jsou například vytvářena s pevnou velikostí. Seznamy lze zmenšit a zvětšit podle potřeby, což je v tomto programu důležité.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si část [Krok 3: přiřazení náhodné ikony každému popisku](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si téma [Krok 1: vytvoření projektu a přidání tabulky do formuláře](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
