---
title: 'Krok 11: Spusťte svůj Program a vyzkoušejte další funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a80a962017cc54e6ce7aae6201079f976dee9ab1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172273"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Krok 11: Spusťte svůj program a vyzkoušejte další funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace je dokončené a připravené ke spuštění. Můžete spustit váš program a nastavit barvu pozadí pole PictureBox. Další informace, zkuste program zlepšit změnou barvy formuláře, přizpůsobením tlačítek a zaškrtávacího políčka a změnou vlastností formuláře.  
  
 Chcete-li stáhnout úplnou verzi vzorku, přečtěte si téma [ukázkový kurz pro dokončení prohlížeče obrázků](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")video verzi tohoto tématu naleznete v tématu [kurz 1: vytvoření prohlížeče obrázků v jazyce Visual Basic - Video 5](http://go.microsoft.com/fwlink/?LinkId=205216) nebo [kurz 1: vytvoření prohlížeče obrázků v jazyce C# – Video 5](http://go.microsoft.com/fwlink/?LinkId=205206). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>Spusťte program a nastavit barvu pozadí  
  
1.  Vyberte tlačítko F5 nebo na panelu nabídek zvolte **ladění**, **spustit ladění**.  
  
2.  Před otevřením obrázku vyberte **nastavit barvu pozadí** tlačítko. **Barva** zobrazí se dialogové okno.  
  
     ![Dialogové okno barev](../ide/media/express-colordialog.png "Express_ColorDialog")  
Dialogové okno barvy  
  
3.  Zvolte barvu, kterou chcete nastavit barvu pozadí ovládacího prvku PictureBox. Prohlédněte si blíže `backgroundButton_Click()` metoda pochopit, jak to funguje.  
  
    > [!NOTE]
    >  Načíst obrázek z Internetu vložením jeho URL do **otevřít soubor** dialogové okno. Pokuste se najít obrázek s průhledným pozadím, takže se zobrazí barva pozadí.  
  
4.  Zvolte **Vymazat obrázek** tlačítko, abyste měli jistotu, že se vymaže. Ukončete program výběrem **Zavřít** tlačítko.  
  
### <a name="to-try-other-features"></a>Vyzkoušení dalších funkcí  
  
-   Změňte barvu formuláře a tlačítek pomocí **BackColor** vlastnost.  
  
-   Přizpůsobte si tlačítka a zaškrtávací políčko pomocí **písmo** a **ForeColor** vlastnosti.  
  
-   Změna formuláře **FormBorderStyle** a **ControlBox** vlastnosti.  
  
-   Pomocí formuláře **AcceptButton** a **CancelButton** vlastností tohoto tlačítka je automaticky kliknuto, když uživatel stiskne klávesu ENTER nebo ESC. Nechejte program otevřít **otevřít soubor** dialogové okno když uživatel vybere klávesu ENTER a zavřít okno, když uživatel vybere klávesu ESC.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Další informace o programování v sadě Visual Studio najdete v tématu [koncepty programování](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).  
  
-   Další informace o jazyce Visual Basic, naleznete v tématu [vývoj aplikací pomocí jazyka Visual Basic](http://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).  
  
-   Další informace o jazyce Visual C# najdete v tématu [Úvod do jazyka C# a rozhraní .NET Framework](http://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).  
  
-   Chcete-li přejít k dalšímu kurzu, přečtěte si téma [kurz 2: vytvoření a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 10: napsat kód pro přídavná tlačítka a zaškrtávací políčko](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).



