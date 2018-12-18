---
title: 'Krok 6: Pojmenujte své ovládací prvky tlačítek'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b11bace93efc253ffcb0f8d2b97ecc57c7462bb8
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748394"
---
# <a name="step-6-name-your-button-controls"></a>Krok 6: Pojmenujte své ovládací prvky tlačítek
Existuje pouze jeden <xref:System.Windows.Forms.PictureBox> ve formuláři. Pokud jste ji přidali rozhraní IDE automaticky pojmenuje **pictureBox1**. Existuje pouze jeden <xref:System.Windows.Forms.CheckBox>, která má název **checkBox1**. Později, brzy bude napsat kód, a tento kód bude odkazovat na zaškrtávací políčko a PictureBox. Protože se nachází pouze jeden z těchto ovládacích prvků, budete vědět, co znamená až uvidíte **pictureBox1** nebo **checkBox1** ve vašem kódu.

> [!NOTE]
>  V jazyce Visual Basic je výchozí první písmeno ovládací prvek je velké písmeno, takže budou mít názvy **PictureBox1**, **CheckBox1**a tak dále.

 Existují čtyři tlačítka ve formuláři a s názvem rozhraní IDE, je **button1**, **button2**, **button3**, a **button4**. Právě pohledem na jejich názvy nevíte, které tlačítko je **Zavřít** tlačítko a která je **zobrazit obrázek** tlačítko. To je důvod, proč poskytnutí vaše tlačítka informativnější názvy je užitečné.

 ![odkaz na video](../data-tools/media/playvideo.gif)video verzi tohoto tématu naleznete v části [kurzu 1: vytvoření prohlížeče obrázků v jazyce Visual Basic – Video 3](http://go.microsoft.com/fwlink/?LinkId=205213) nebo [kurzu 1: vytvoření prohlížeče obrázků v jazyce C# - Video 3](http://go.microsoft.com/fwlink/?LinkId=205202). Tyto videa pomocí starší verze sady Visual Studio, takže drobné rozdíly v některé příkazy a další prvky uživatelského rozhraní. Však koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.

## <a name="to-name-your-button-controls"></a>Chcete-li název své ovládací prvky tlačítek

1.  Ve formuláři, vyberte **Zavřít** tlačítko. (Pokud máte všechna tlačítka vybrána, vyberte **Esc** klíč, zrušte výběr.) Posuňte se v **vlastnosti** okno, dokud neuvidíte **(název)** vlastnost. ( **(Název)** vlastnost je v horní, když jsou vlastnosti v abecedním pořadí.) Změňte název **closeButton**, jak je znázorněno na následujícím obrázku.

     ![Vlastnosti – okno s názvem closeButton](../ide/media/express_setnameproperty.png)
**vlastnosti** okno s **closeButton** název

    > [!NOTE]
    >  Pokud se pokusíte změnit název vašeho tlačítko **closeButton**, mezera mezi slovy zavřít a tlačítko, rozhraní IDE zobrazí chybovou zprávu: "hodnota vlastnosti není platná." V názvech řízení nejsou povoleny mezery (a několik dalších znaků).

2.  Přejmenujte další tři tlačítka na **backgroundButton**, **tlacitkoVymazat**, a **showButton**. Názvy můžete ověřit tak, že zvolíte rozevíracího seznamu pro výběr ovládacího prvku v **vlastnosti** okno. Zobrazí se nové názvy tlačítko.

3.  Dvakrát klikněte **zobrazit obrázek** tlačítko ve formuláři. Jako alternativu, vyberte **zobrazit obrázek** tlačítko ve formuláři a potom vyberte **Enter** klíč. Pokud to uděláte, rozhraní IDE otevře další karta v hlavním okně názvem **Form1.cs** (**Form1.vb** Pokud používáte Visual Basic). Tato karta ukazuje soubor kódu pozadí formuláře, jak je znázorněno na následujícím obrázku.

     ![Karta Form1.cs s Visual C&#35; kód](../ide/media/express_showbuttoncode.png)
**Form1.cs** karta s kódem jazyka Visual C#

4.  Soustřeďte se na tuto část kódu. (Vyberte **VB** kartě níže, pokud používáte zobrazení jazyka Visual Basic verze kódu jazyka Visual Basic.)

     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]
     [!code-csharp[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]

     Prohlížení kódu volaného `showButton_Click()`. Rozhraní IDE přidalo to do kódu formuláře při otevření souboru kódu pro **showButton** tlačítko. V době návrhu při otevření souboru kódu ovládacího prvku ve formuláři, se generuje kód pro ovládací prvek Pokud ještě neexistuje. Tento kód, označuje jako *metoda*, spustí spusťte svůj program a vyberte ovládací prvek – v takovém případě **zobrazit obrázek** tlačítko.

    > [!NOTE]
    >  V tomto kurzu je jednodušší kód jazyka Visual Basic, který se automaticky vygeneroval odebráním vše v závorkách `()`. Vždy, když k tomu dojde, můžete odebrat stejný kód. Váš program bude fungovat v obou případech. Pro zbývající kurzů k žádné automaticky generovaný kód je jednodušší, kdykoli je to možné.

5.  Vyberte **Návrhář formulářů Windows** kartě znovu (**Form1.cs [Design]** v jazyce Visual C# **Form1.vb [Design]** v jazyce Visual Basic) a pak otevřete v souboru kódu **Vymazat obrázek** tlačítko vytvořte metodu pro něj v kódu formuláře. Tento postup opakujte pro zbývající dvě tlačítka. Pokaždé, když, rozhraní IDE přidá nové metody do souboru kódu formuláře.

6.  Chcete-li přidat další metodu, otevřete soubor kódu pro **políčko** řídit ve **Návrhář formulářů Windows** aby rozhraní IDE přidat `checkBox1_CheckedChanged()` metoda. Tato metoda je volána, když uživatel vybere nebo zruší zaškrtnutí políčka.

    > [!NOTE]
    >  Při práci na program, často přesunutí mezi editoru kódu a **Návrhář formulářů Windows**. Prostředí IDE usnadňuje přejděte ve vašem projektu. Použití **Průzkumníku řešení** otevřete **Návrhář formulářů Windows** dvojitým kliknutím na soubor *Form1.cs* v jazyce Visual C# nebo *Form1.vb* v jazyce Visual Basic nebo v řádku nabídek zvolte **zobrazení** > **Návrhář**.

     Následující zobrazuje nový kód, který se zobrazí v editoru kódu.

     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]
     [!code-csharp[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

     Pět metod, které jste přidali, se nazývají *obslužné rutiny událostí*, protože program volá vždy, když nastane událost (např. uživatel, volbu tlačítka nebo vybírá pole).

     Při zobrazení kód pro ovládací prvek v prostředí IDE v době návrhu, Visual Studio přidá metodu obslužné rutiny události pro ovládací prvek, pokud jeden není k dispozici. Například když dvakrát kliknete na tlačítko rozhraní IDE přidá obslužné rutiny události pro jeho <xref:System.Windows.Forms.Control.Click> událost (která je volána, když uživatel vybere tlačítko). Pokud dvakrát klikněte na zaškrtávací políčko rozhraní IDE přidá obslužné rutiny události pro jeho <xref:System.Windows.Forms.CheckBox.CheckedChanged> událost (která je volána, když uživatel vybere nebo vymaže pole).

     Po přidání obslužné rutiny události pro ovládací prvek, můžete k němu mohli vrátit kdykoli **Návrhář formulářů Windows** poklepáním na ovládací prvek, nebo v nabídce panelu Výběr **zobrazení**  >  **Kód**.

     Názvy jsou důležité při vytváření programů a metody (včetně obslužné rutiny událostí) může mít libovolný název, který chcete. Když přidáváte obslužné rutiny události pomocí rozhraní IDE, vytvoří název na základě jeho názvu a události ke zpracování. Například událost klikněte na tlačítko s názvem **showButton** je volána `showButton_Click()` obslužná rutina události. Navíc otvírání a zavírání závorkách `()` jsou obvykle přidány po název metody k označení, že jsou právě popsané metody. Pokud se rozhodnete, kterou chcete změnit název proměnné kódu, klikněte pravým tlačítkem v proměnné a pak zvolte **Refaktorovat** > **přejmenovat**. Všechny instance této proměnné v kódu jsou přejmenovat. V tématu [refaktoring pro přejmenování](../ide/reference/rename.md) Další informace.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Chcete-li přejít k dalšímu kroku kurzu, přečtěte si téma [krok 7: přidejte do svého formuláře komponenty dialogových oken](../ide/step-7-add-dialog-components-to-your-form.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 5: Přidání ovládacích prvků do svého formuláře](../ide/step-5-add-controls-to-your-form.md).
