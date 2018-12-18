---
title: 'Krok 6: Pojmenujte své ovládací prvky tlačítek | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e02c240f8e4146ce1c87fd1d90c30eb7787cef5d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303781"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6: Pojmenujte své ovládací prvky tlačítek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve formuláři je pouze jeden ovládací prvek PictureBox. Při přidávání jej rozhraní IDE automaticky pojmenuje **pictureBox1**. Existuje pouze jeden CheckBox, který se nazývá **checkBox1**. Brzy napíšete kód a tento kód bude odkazovat na ovládací prvek CheckBox a PictureBox. Protože se nachází pouze jednu roli od každého z těchto ovládacích prvků, budete vědět, co znamenají, až se zobrazí **pictureBox1** nebo **checkBox1** ve vašem kódu.  
  
> [!NOTE]
>  V jazyce Visual Basic je výchozí první písmeno ovládacího prvku je počáteční velkým písmenem, takže názvy jsou **PictureBox1**, **CheckBox1**, a tak dále.  
  
 Existují čtyři tlačítka na formuláři a rozhraní IDE je pojmenovalo **button1**, **button2**, **button3**, a **button4**. Jen pohlédnutím na jejich názvy nevíte, které tlačítko je **Zavřít** tlačítko a který je **zobrazit obrázek** tlačítko. To je důvod, proč poskytuje své ovládací prvky tlačítek informativnějších názvů je užitečné.  
  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")video verzi tohoto tématu naleznete v tématu [kurz 1: vytvoření prohlížeče obrázků v jazyce Visual Basic - Video 3](http://go.microsoft.com/fwlink/?LinkId=205213) nebo [kurz 1: vytvoření prohlížeče obrázků v jazyce C# – Video 3](http://go.microsoft.com/fwlink/?LinkId=205202). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.  
  
### <a name="to-name-your-button-controls"></a>Pojmenujte své ovládací prvky tlačítek  
  
1.  Ve formuláři, zvolte **Zavřít** tlačítko. (Pokud stále máte všechna tlačítka vybrána, stiskněte klávesu ESC zrušte výběr.) Posouvejte **vlastnosti** okna, dokud se nezobrazí **(název)** vlastnost. ( **(Název)** vlastnost je blízko horní, pokud jsou vlastnosti v abecedním pořadí.) Změňte název na **closeButton**, jak je znázorněno na následujícím obrázku.  
  
     ![Okno Vlastnosti s názvem closeButton](../ide/media/express-setnameproperty.png "Express_SetNameProperty")  
Okno Vlastnosti s názvem closeButton  
  
    > [!NOTE]
    >  Pokud se pokusíte změnit název tlačítka na **closeButton**, s mezerou mezi slovy, zavřít a tlačítko, rozhraní IDE zobrazí chybovou zprávu: "hodnota vlastnosti není platná." Mezery (a několik jiných znaků) nejsou povoleny v názvech ovládacích prvků.  
  
2.  Přejmenujte další tři tlačítka na **backgroundButton**, **tlacitkoVymazat**, a **showButton**. Názvy můžete ověřit výběrem ovládacího prvku selektoru rozevíracího seznamu v **vlastnosti** okna. Nové názvy tlačítek se zobrazí.  
  
3.  Dvakrát klikněte **zobrazit obrázek** tlačítko na formuláři. Jako alternativu zvolte **zobrazit obrázek** tlačítko na formuláři a potom stiskněte klávesu ENTER. Když použijete, rozhraní IDE otevře další kartu v hlavním okně volá **Form1.cs** (**Form1.vb** Pokud používáte jazyk Visual Basic). Tato karta zobrazuje soubor kódu za formulářem, jak je znázorněno na následujícím obrázku.  
  
     ![Karta Form1.cs s Visual C&#35; kód](../ide/media/express-showbuttoncode.png "Express_ShowButtonCode")  
Karta Form1.cs s kódem Visual C#  
  
4.  Zaměřte se na tuto část kódu. (Zvolte **VB** kartě níže, pokud používáte jazyk Visual Basic k zobrazení verze kódu jazyka Visual Basic.)  
  
     [!code-csharp[VbExpressTutorial1Step6#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step6#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#1)]  
  
     Díváte se na kód nazvaný `showButton_Click()`. Rozhraní IDE toto přidal do kódu formuláře při otevření souboru kódu **showButton** tlačítko. V době návrhu když otevřete soubor kódu pro ovládací prvek ve formuláři, kód je generován pro ovládací prvek Pokud ještě neexistuje. Tento kód se označuje jako *metoda*, spustí při spuštění programu a zvolte ovládacího prvku – v takovém případě **zobrazit obrázek** tlačítko.  
  
    > [!NOTE]
    >  V tomto kurzu kódu jazyka Visual Basic, který je automaticky generován byl zjednodušen odebráním všeho mezi závorkami, (). Pokaždé, když se v takovém případě můžete odebrat stejný kód. Váš program bude fungovat v obou případech. Pro zbývající část kurzů je všechen automaticky generovaný kód zjednodušen, kdykoli je to možné.  
  
5.  Zvolte znovu kartu Návrhář formulářové aplikace Windows (**Form1.cs [Design]** v jazyce Visual C# **Form1.vb [Design]** v jazyce Visual Basic) a pak otevřete soubor kódu **Vymazat obrázek** tlačítko Vytvořit metodu pro něj v kódu formuláře. Tento postup opakujte pro zbývající dvě tlačítka. Pokaždé, když, rozhraní IDE přidá novou metodu do souboru kódu formuláře.  
  
6.  Chcete-li přidat další metodu, otevřete soubor kódu pro ovládací prvek CheckBox v Návrháři formulářů Windows rozhraní IDE, přidejte `checkBox1_CheckedChanged()` metody. Tato metoda je volána pokaždé, když uživatel vybere nebo zruší zaškrtávací políčko.  
  
    > [!NOTE]
    >  Při práci na programu se často přesouváte mezi editorem kódu a Návrhář formulářů Windows. Rozhraní IDE usnadňuje navigaci v projektu. Použití **Průzkumníka řešení** otevřít Návrhář formulářů Windows dvojitým kliknutím **Form1.cs** v jazyce Visual C# nebo **Form1.vb** v jazyce Visual Basic nebo na panelu nabídek zvolte **Zobrazení**, **návrháře**.  
  
     Následující znázorňuje nový kód, na který se zobrazí v editoru kódu.  
  
     [!code-csharp[VbExpressTutorial1Step6#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step6#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#2)]  
  
     Pět metod, které jste přidali, se nazývají *obslužné rutiny událostí*, protože je program volá vždy, když se stane, událost (podobně jako uživatel vybírá tlačítko nebo pole).  
  
     Při zobrazení kódu pro ovládací prvek v integrovaném vývojovém prostředí v době návrhu, Visual Studio přidá metodu obslužné rutiny události pro ovládací prvek, pokud není k dispozici. Například když dvakrát kliknete na tlačítko, rozhraní IDE přidá obslužnou rutinu události pro jeho událost Click (která je volána pokaždé, když uživatel vybere tlačítko). Když dvakrát kliknete na zaškrtávací políčko, rozhraní IDE přidá obslužnou rutinu události pro událost CheckedChanged (která se volá vždy, když uživatel vybere nebo zruší pole).  
  
     Po přidání obslužné rutiny události pro ovládací prvek, můžete k němu můžete vrátit kdykoli z Návrháře formulářů Windows dvojitým kliknutím ovládací prvek nebo na panelu nabídek, výběrem **zobrazení**, **kód**.  
  
     Názvy jsou důležité při vytváření programů a metody (včetně obslužné rutiny události) mohou mít libovolný název, který chcete. Při přidání obslužné rutiny události pomocí rozhraní IDE vytvoří název založený na názvu ovládacího prvku a události zpracovávanou na. Například událost Click pro tlačítko s názvem **showButton** je volána `showButton_Click()` metoda obslužné rutiny události. Levé a pravé závorky () se také, obvykle přidány po názvu metody k označení, že metody byly diskutovány. Pokud se rozhodnete, kterou chcete změnit název proměnné kódu, klikněte pravým tlačítkem myši proměnnou kódu a klikněte na tlačítko **Refaktorovat**, **přejmenovat**. Všechny výskyty této proměnné v kódu budou přejmenovány. Zobrazit [refaktoring přejmenování (C#)](../csharp-ide/rename-refactoring-csharp.md) nebo [Refactoring a dialogové okno Přejmenovat](http://msdn.microsoft.com/library/001d2d81-9bb6-4e8e-ae3a-20c0daaa3959) Další informace.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 7: komponenty dialogového okna Přidat na svůj formulář](../ide/step-7-add-dialog-components-to-your-form.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 5: Přidání ovládacích prvků na svůj formulář](../ide/step-5-add-controls-to-your-form.md).



