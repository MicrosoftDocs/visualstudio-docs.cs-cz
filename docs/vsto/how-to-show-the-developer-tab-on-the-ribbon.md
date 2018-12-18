---
title: 'Postupy: zobrazení karty Vývojář na pásu karet'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: edcbcb969e45403d9ca138b259073e3cf4d73be0
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349621"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Postupy: zobrazení karty Vývojář na pásu karet
  Pro přístup **Developer** kartu na pásu karet aplikace sady Office, je nutné nakonfigurovat ji k zobrazení této karty, protože se nezobrazuje ve výchozím nastavení. Například můžete musíte zobrazit kartu, pokud chcete přidat <xref:Microsoft.Office.Tools.Word.GroupContentControl> k přizpůsobení úrovni dokumentu pro aplikaci Word.  
  
> [!NOTE]  
>  Tyto pokyny platí pro Office 2010 nebo novější pouze aplikací. Pokud chcete zobrazit tuto kartu v systému Microsoft Office 2007, přečtěte si následující verzi tohoto tématu [postupy: zobrazení karty Vývojář na pásu karet](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Nemá přístup **Developer** kartu.  
  
## <a name="to-show-the-developer-tab"></a>Chcete-li zobrazit kartu Vývojář  
  
1.  Spustíte některou z aplikací Office, které jsou podporovány v tomto tématu. Zobrazit **platí pro:** Poznámka: výše v tomto tématu.  
  
2.  Na **souboru** , vyberte **možnosti** tlačítko.  
  
     Následující obrázek ukazuje **souboru** kartu a **možnosti** tlačítko v aplikaci Office 2010.  
  
     ![Výběr souboru, možnosti v aplikaci Outlook 2010](../vsto/media/vsto-office-file-tab.png "výběr souboru, možnosti v aplikaci Outlook 2010")  
  
     Následující obrázek ukazuje **souboru** kartě v aplikaci Office 2013.  
  
     ![Karta soubor v Outlooku 2013](../vsto/media/vsto-office2013-filetab.png "karta soubor v aplikaci Outlook 2013")  
  
     Následující obrázek ukazuje **možnosti** tlačítko v aplikaci Office 2013.  
  
     ![Tlačítko Možnosti v aplikaci Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "tlačítko Možnosti v aplikaci Outlook 2013 Preview")  
  
3.  V _ApplicationName_**možnosti** dialogového okna zvolte **Přizpůsobit pás karet** tlačítko.  
  
     Následující obrázek ukazuje **možnosti** dialogové okno a **Přizpůsobit pás karet** tlačítko v aplikaci Excel 2010. Umístění tohoto tlačítka je podobné jako u všech ostatních aplikací uvedených v části "Platí pro" v horní části tohoto tématu.  
  
     ![Vlastní nastavení pásu karet tlačítko](../vsto/media/vsto-office2010-customizeribbonbutton.png "The vlastní nastavení pásu karet tlačítko")  
  
4.  Vyberte v seznamu hlavních karet **Developer** zaškrtávací políčko.  
  
     Následující obrázek ukazuje **Developer** zaškrtávací políčko v aplikaci Word 2010 a [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Umístění tohoto zaškrtávacího políčka je podobné jako u všech ostatních aplikací uvedených v části "Platí pro" v horní části tohoto tématu.  
  
     ![Zaškrtněte políčko pro vývojáře v dialogovém okně Možnosti v aplikaci Word](../vsto/media/vsto-office2010-developercheckbox.png "políčko Vývojář v dialogovém okně Možnosti v aplikaci Word")  
  
5.  Zvolte **OK** tlačítko pro uzavření **možnosti** dialogové okno.  
  
## <a name="see-also"></a>Viz také:  
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)  
  
  