---
title: 'Postupy: Změna pozice karty na pásu karet'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f821ea2a469fc06f80a7aaea96d07274d02a81d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544856"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Postupy: Změna pozice karty na pásu karet
  Pořadí vlastních karet na pásu karet můžete změnit pomocí **editoru kolekce karet**. Vlastní karty můžete umístit před nebo za integrovanou kartu na pásu karet. Integrovaná karta je karta, která již je na pásu karet aplikace systém Microsoft Office. Karta **data** je například Integrovaná karta v aplikaci Excel.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Změna pořadí karet na pásu karet

1. V **Průzkumník řešení**vyberte soubor kódu pásu karet (soubor *. vb* nebo *. cs* ).

2. V nabídce **zobrazení** klikněte na možnost **Návrhář**.

3. Klikněte pravým tlačítkem myši na Návrhář pásu karet a pak klikněte na **vlastnosti**.

4. V okně **vlastnosti** vyberte vlastnost **tabulátory** a potom klikněte na tlačítko se třemi tečkami (![Elipsa ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")).

     Zobrazí se **Editor kolekce karet** .

5. V **editoru kolekce karet**v seznamu **Členové** vyberte kartu, kterou chcete přesunout, a kliknutím na šipky nahoru nebo dolů změňte pořadí ovládacích prvků.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Chcete-li umístit kartu před nebo za integrovanou kartu na pásu karet

1. V Návrháři pásu karet vyberte vlastní kartu.

2. V okně **vlastnosti** rozbalte vlastnost **ControlID** a pak ověřte, zda je hodnota vlastnosti **ControlIdType** nastavena na hodnotu **Custom**.

3. V okně **vlastnosti** rozbalte vlastnost **pozice** .

4. Nastavte vlastnost **PositionType** na odpovídající hodnotu:

    - **BeforeOfficeId** umístí skupinu před zadanou vestavěnou kartu.

    - **AfterOfficeId** umístí skupinu za zadanou vestavěnou kartu.

5. Nastavte vlastnost **OfficeId** na ID ovládacího prvku předdefinované karty.

     Seznam ID ovládacích prvků najdete v tématu [soubory s nápovědu pro office 2010: identifikátory ovládacích prvků uživatelského rozhraní pro Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Viz také
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
