---
title: 'Krok 4: Přidejte k jednotlivým jmenovkám obslužnou rutinu události Click | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93ce8f97f32ac41c4724db3c4cc08389f052f1ef
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923378"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Krok 4: Přidejte k jednotlivým jmenovkám obslužnou rutinu události kliknutí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Porovnávací hra probíhá takto:  
  
1. Když hráč zvolí některý čtverec se skrytou ikonou, program zobrazí ikonu hráči změnou barvy ikony na černou.  
  
2. Potom hráč zvolí jinou skrytou ikonu.  
  
3. Jestliže se ikony shodují, zůstávají viditelné. Pokud tomu tak není, jsou obě ikony opět skryty.  
  
   Aby program takto fungoval, přidejte obslužnou rutinu události Click, která změní barvu vybraného popisku.  
  
### <a name="to-add-a-click-event-handler-to-each-label"></a>Přidání obslužné rutiny události Click ke každému popisku  
  
1.  Otevřete formulář v Návrháři formulářů Windows. V Průzkumníku řešení vyberte soubor Form1.cs nebo Form1.vb. V panelu nabídky zvolte **zobrazení**, **návrháře**.  
  
2.  Vyberte první ovládací prvek popisku. Potom podržte klávesu Ctrl a postupně klikněte na každý další popisek, abyste je vybrali. Je nutné vybrat všechny popisky.  
  
3.  Zvolte **události** tlačítko na panelu nástrojů v **vlastnosti** okno zobrazení **události** stránku **vlastnosti** okna. Přejděte dolů k položce **klikněte na tlačítko** události a zadejte **výraz label_Click** v poli, jak je znázorněno na následujícím obrázku.  
  
     ![Okno Vlastnosti zobrazující klikněte na událost](../ide/media/express-labelclick.png "Express_labelClick")  
Okno Vlastnosti zobrazující událost Click  
  
4.  Poté stiskněte klávesu ENTER. Rozhraní IDE přidá obslužnou rutinu události Click, která se nazývá `label_Click()` kódu a připojí ji k jednotlivým popiskům ve formuláři.  
  
5.  Vyplňte zbývající část kódu takto:  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#4)]  
  
    > [!NOTE]
    >  Pokud zkopírujete a vložíte `label_Click()` blok kódu, spíše než ručního zadání kódu, nezapomeňte nahradit stávající `label_Click()` kódu. Jinak budete mít duplicitní kód bloku.  
  
    > [!NOTE]
    >  Si možná pamatujete `object sender` v horní části obslužné rutiny události jako stejný jako ten používané [kurz 2: vytvoření a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md) kurzu. Protože jste připojili různé události Click ovládacího prvku popisku k jedné metodě obslužné rutiny události, volá se stejná metoda bez ohledu na to, který popisek uživatel zvolil. Metoda obslužné rutiny události potřebuje vědět, který popisek byl vybrán, takže použije jméno **odesílatele** k identifikaci ovládacího prvku popisku. První řádek metody dává pokyn programu, že není pouze obecný objekt, ale specificky ovládací prvek popisku a používá název **clickedLabel** pro přístup k vlastnostem a metodám popisku.  
  
     Tato metoda nejprve zkontroluje, jestli **clickedLabel** byl úspěšně převeden (přetypován) z objektu do ovládacího prvku popisku. Pokud neúspěšný, má hodnotu `null` (C#) nebo `Nothing` (Visual Basic), a nechcete provést zbytek kódu v metodě. Dále metoda zkontroluje barvu textu vybraného popisku pomocí popisku **ForeColor** vlastnost. Pokud je barva textu popisku černá, znamená to, že ikona již byla vybrána a metoda je provedena. (To `return` provádí příkaz: říká programu, že má zastavit spouštění metody.) V opačném případě ikona nebyla vybrána, takže program změní barvu textu popisku na černou.  
  
6.  V panelu nabídky zvolte **souboru**, **Uložit vše** rozdělanou práci uložit, a pak na panelu nabídek zvolte **ladění**, **spustit ladění** ke spuštění váš program. Měl by se zobrazit prázdný formulář s modrým pozadím. Vyberte jakékoli buňky ve formuláři. Měla by se zobrazit jedna z ikon. Pokračujte ve výběru různých míst ve formuláři. Ikony by se měly výběrem postupně zobrazovat.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 5: Add Label References](../ide/step-5-add-label-references.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 3: přiřazení náhodné ikony pro každý popisek](../ide/step-3-assign-a-random-icon-to-each-label.md).



