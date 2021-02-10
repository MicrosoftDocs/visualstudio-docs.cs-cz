---
title: 'Postupy: Přizpůsobení předdefinované karty'
description: Přečtěte si, jak můžete přidat skupiny a ovládací prvky na integrovanou kartu. Integrovaná karta je karta, která je již na pásu karet aplikace systém Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94cf4d256cafa03ee4604138f7233ff9fd3cf6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953991"
---
# <a name="how-to-customize-a-built-in-tab"></a>Postupy: Přizpůsobení předdefinované karty
  Můžete přidat skupiny a ovládací prvky na integrovanou kartu. Integrovaná karta je karta, která je již na pásu karet aplikace systém Microsoft Office. Karta **data** je například Integrovaná karta v aplikaci Excel. Když vytvoříte vlastní skupinu, zobrazí se na kartě jako poslední, ale skupinu můžete přesunout kdekoli na kartě.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> Skupiny můžete přidat na integrovanou kartu, nemůžete ale odebrat předdefinované skupiny z předdefinované karty.

### <a name="to-add-groups-to-a-built-in-tab"></a>Přidání skupin na integrovanou kartu

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor kódu pásu karet a pak klikněte na tlačítko **Návrhář zobrazení**.

    > [!NOTE]
    > Pokud se soubor kódu pásu karet v **Průzkumník řešení** nezobrazí, musíte do projektu přidat **položku pásu karet** . Přečtěte si téma [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Klikněte pravým tlačítkem myši na libovolnou kartu v Návrháři pásu karet a pak klikněte na **vlastnosti**.

3. V okně **vlastnosti** rozbalte vlastnost **ControlID** a pak nastavte vlastnost **ControlIdType** na hodnotu **Office**.

4. Nastavte vlastnost **OfficeId** na *ID ovládacího prvku* předdefinované karty, kterou chcete přizpůsobit.

     ID ovládacího prvku je název, který jednoznačně identifikuje karty, skupiny a ovládací prvky, které jsou integrovány v aplikacích systém Microsoft Office.

     Seznam ID ovládacích prvků najdete v tématu [soubory s nápovědu pro office 2010: identifikátory ovládacích prvků uživatelského rozhraní pro Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

5. Na kartě **ovládací prvky pásu karet Office** v **panelu nástrojů** přetáhněte skupiny na kartu.

    > [!NOTE]
    > Předdefinované skupiny se nezobrazí v návrháři. Proto jediným způsobem, jak určit, zda pracujete s integrovanou kartou, je prozkoumávat vlastnost **ControlID** karty.

### <a name="to-position-groups-on-a-built-in-tab"></a>Umístění skupin na integrovanou kartu

1. V Návrháři pásu karet vyberte vlastní skupinu.

2. V okně **vlastnosti** rozbalte vlastnost **pozice** .

3. Nastavte vlastnost **PositionType** na odpovídající hodnotu:

    - **BeforeOfficeId** umístí skupinu před zadanou vestavěnou skupinu.

    - **AfterOfficeId** umístí skupinu po zadané předdefinované skupině.

4. Nastavte vlastnost **OfficeId** na ID ovládacího prvku předdefinované skupiny.

     Seznam ID ovládacích prvků najdete v tématu [soubory s nápovědu pro office 2010: identifikátory ovládacích prvků uživatelského rozhraní pro Office Fluent](https://www.microsoft.com/download/details.aspx?id=6627).

## <a name="see-also"></a>Viz také
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Postupy: Změna pozice karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Postupy: zobrazení chyb uživatelského rozhraní doplňku](../vsto/how-to-show-add-in-user-interface-errors.md)
