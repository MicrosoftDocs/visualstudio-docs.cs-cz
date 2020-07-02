---
title: 'Postupy: zobrazení karty Vývojář na pásu karet'
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 41070c92d0c27c1ee8fbf480f7461c22421b8fdc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545844"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Postupy: zobrazení karty Vývojář na pásu karet
  Chcete-li získat přístup k kartě **vývojář** na pásu karet aplikace sady Office, je nutné ji nakonfigurovat tak, aby se tato karta zobrazila, protože se ve výchozím nastavení nezobrazuje. Například je třeba zobrazit tuto kartu, pokud chcete přidat <xref:Microsoft.Office.Tools.Word.GroupContentControl> do přizpůsobení na úrovni dokumentu pro aplikaci Word.

> [!NOTE]
> Tento návod se vztahuje pouze na aplikace Office 2010 nebo novější. Chcete-li zobrazit tuto kartu v systému 2007 systém Microsoft Office, přečtěte si následující verzi tohoto tématu [: zobrazení karty Vývojář na pásu karet](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Přístup nemá kartu **vývojář** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Zobrazení karty Vývojář

1. Spusťte libovolnou aplikaci Office podporovanou tímto tématem. Viz část **platí pro:** Poznámka výše v tomto tématu.

2. Na kartě **soubor** klikněte na tlačítko **Možnosti** .

     Následující obrázek ukazuje kartu **soubor** a tlačítko **Možnosti** v sadě Office 2010.

     ![Výběr souboru, možností v aplikaci Outlook 2010](../vsto/media/vsto-office-file-tab.png "Výběr souboru, možností v aplikaci Outlook 2010")

     Následující obrázek ukazuje kartu **soubor** v sadě Office 2013.

     ![Karta soubor v aplikaci Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Karta soubor v aplikaci Outlook 2013")

     Následující obrázek ukazuje tlačítko **Možnosti** v sadě Office 2013.

     ![Tlačítko Možnosti v aplikaci Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Tlačítko Možnosti v aplikaci Outlook 2013 Preview")

3. V dialogovém okně**Možnosti** _ApplicationName_klikněte na tlačítko **přizpůsobit pás karet** .

     Následující obrázek ukazuje dialogové okno **Možnosti** a tlačítko **přizpůsobit pás karet** v aplikaci Excel 2010. Umístění tohoto tlačítka je podobné jako u všech ostatních aplikací, které jsou uvedeny v části "platí pro" v horní části tohoto tématu.

     ![Tlačítko Přizpůsobit pás karet](../vsto/media/vsto-office2010-customizeribbonbutton.png "Tlačítko Přizpůsobit pás karet")

4. V seznamu hlavních karet zaškrtněte políčko **vývojář** .

     Následující obrázek ukazuje zaškrtávací políčko **vývojář** ve wordu 2010 a [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . Umístění tohoto zaškrtávacího políčka je podobné jako u všech ostatních aplikací, které jsou uvedeny v části "platí pro" v horní části tohoto tématu.

     ![Zaškrtávací políčko Vývojář v dialogovém okně Možnosti aplikace Word](../vsto/media/vsto-office2010-developercheckbox.png "Zaškrtávací políčko Vývojář v dialogovém okně Možnosti aplikace Word")

5. Kliknutím na tlačítko **OK** zavřete dialogové okno **Možnosti** .

## <a name="see-also"></a>Viz také:
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
