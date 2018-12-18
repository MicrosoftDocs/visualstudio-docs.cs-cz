---
title: 'Krok 7: Přidejte do svého formuláře komponenty dialogových oken | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca17a6958a3c66054b89fc65c30bf397c4e6b821
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192943"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Krok 7: Přidejte do svého formuláře komponenty dialogových oken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li povolit programu otevírání souborů obrázků a výběr barvy pozadí, v tomto kroku přidáte **OpenFileDialog** komponenty a **ColorDialog** komponentu do formuláře.  
  
 Komponenta je jako ovládací prvek v některých ohledech. Pomocí panelu nástrojů přidáte komponentu do formuláře a nastavíte její vlastnosti pomocí **vlastnosti** okna. Ale na rozdíl od ovládacího prvku, přidání komponenty do formuláře nepřidává viditelnou položku, kterou může uživatel vidět ve formuláři. Místo toho poskytuje určité druhy chování, které můžete aktivovat s kódem. Jedná se o součást, která se otevře **otevřít soubor** dialogové okno.  
  
 ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")video verzi tohoto tématu naleznete v tématu [kurz 1: vytvoření prohlížeče obrázků v jazyce Visual Basic - Video 3](http://go.microsoft.com/fwlink/?LinkId=205213) nebo [kurz 1: vytvoření prohlížeče obrázků v jazyce C# – Video 3](http://go.microsoft.com/fwlink/?LinkId=205202). Tato videa používají starší verzi sady Visual Studio, takže existují mírné rozdíly v některých příkazech nabídek a jiných prvcích uživatelského rozhraní. Nicméně koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.  
  
### <a name="to-add-dialog-components-to-your-form"></a>Přidat do svého formuláře komponenty dialogových oken  
  
1.  Zvolte Návrhář formulářů Windows (Form1.cs [Design] nebo Form1.vb [Design]) a pak otevřete **dialogová okna** skupiny v panelu nástrojů.  
  
    > [!NOTE]
    >  **Dialogová okna** skupiny v panelu nástrojů má komponenty, které otevírají mnoho užitečných dialogových oken, které lze použít pro otevírání a ukládání souborů, procházení složek a výběru písma a barvy. V tomto projektu použijete dvě komponenty dialogového okna: **OpenFileDialog** a **ColorDialog**.  
  
2.  K přidání komponenty s názvem **openFileDialog1** do formuláře dvakrát klikněte na panel **OpenFileDialog**. K přidání komponenty s názvem **colorDialog1** do formuláře dvakrát klikněte na panel **ColorDialog** na panelu nástrojů. (Můžete použít v dalším kroku výukového programu.) Měli byste vidět plochu v dolní části Windows Návrháře formulářů (pod formulářem prohlížeče obrázků), který má ikonu pro každou z komponent dvou dialogových oken, které jste přidali, jak je znázorněno na následujícím obrázku.  
  
     ![Komponenty dialogového okna](../ide/media/express-dialogsadded.png "Express_DialogsAdded")  
Komponenty dialogového okna  
  
3.  Zvolte **openFileDialog1** ikony v oblasti v dolní části okna Návrháře formulářů Windows. Nastavte dvě vlastnosti:  
  
    -   Nastavte **filtr** vlastnost následující (můžete zkopírovat a vložit):  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    -   Nastavte **název** pro následující vlastnost: **vyberte soubor s obrázkem**  
  
         **Filtr** nastavení vlastností zadejte druhy typů souborů, které se zobrazí v **vybrat obrázek** dialogové okno souboru.  
  
    > [!NOTE]
    >  Chcete-li zobrazit příklad **otevřít soubor** dialogové okno v jiné aplikaci otevřete Poznámkový blok nebo Malování a na panelu nabídek zvolte **souboru**, **otevřete**. Všimněte si, jak je **soubory typu** rozevírací seznam v dolní části. Právě jste použili **filtr** vlastnost v **OpenFileDialog** součásti k tomuto nastavení. Všimněte si také, jak **Title** a **filtr** vlastnosti jsou zobrazeny tučným písmem v **vlastnosti** okna. Rozhraní IDE toto dělá, abyste viděli všechny vlastnosti, které byly změněny z výchozí hodnoty.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 8: zapište kód pro zobrazení obslužné rutiny události obrázku tlačítka](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 6: název si ovládací prvky tlačítka](../ide/step-6-name-your-button-controls.md).



