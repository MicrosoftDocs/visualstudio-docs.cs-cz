---
title: 'Postupy: Přizpůsobení předdefinované karty'
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
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30b4af116df218f3f778b9efa1e295fbadbad86a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257264"
---
# <a name="how-to-customize-a-built-in-tab"></a>Postupy: Přizpůsobení předdefinované karty
  Můžete přidat skupiny a ovládací prvky pro předdefinované karty. Předdefinované karta je karta, která je již na pásu karet z aplikace Microsoft Office. Například **Data** karta je předdefinované karty v aplikaci Excel. Při vytváření vlastních skupin, zobrazí se poslední na kartě, ale skupině můžete přesunout kdekoli na kartě.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Skupiny můžete přidat na předdefinované karty, ale předdefinované skupiny nelze odebrat z předdefinované karty.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>Přidání skupiny do předdefinované karty  
  
1.  Klikněte pravým tlačítkem na pásu karet souboru kódu v **Průzkumníku řešení**a potom klikněte na **Návrhář zobrazení**.  
  
    > [!NOTE]  
    >  Pokud k souboru kódu pásu karet se nezobrazí v **Průzkumníku řešení**, je nutné přidat **položek pásu karet** do projektu. V tématu [postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Klikněte pravým tlačítkem na konkrétní kartě v Návrháři pásu karet a pak klikněte na **vlastnosti**.  
  
3.  V **vlastnosti** okno, rozbalte **ControlId** vlastnost a potom nastavte **ControlIdType** vlastnost **Office**.  
  
4.  Nastavte **OfficeId** vlastnost, která má *ID ovládacího prvku* předdefinované karty, které chcete přizpůsobit.  
  
     ID ovládacího prvku je název, který jednoznačně identifikuje karty, skupiny a ovládací prvky, které jsou součástí aplikace Microsoft Office.  
  
     Seznam ID ovládacích prvků, naleznete v části [soubory nápovědy Office 2010: Office fluent uživatelské rozhraní ovládacího prvku identifikátory](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Z **ovládacích prvků pásu karet Office** kartě **sada nástrojů**, přetáhněte skupiny na kartě.  
  
    > [!NOTE]  
    >  Předdefinované skupiny se nezobrazí v návrháři. Proto je jediný způsob, jak určit, zda pracujete s předdefinované karty prozkoumat **ControlId** vlastnosti na kartě.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>Na pozici skupin na předdefinované karty  
  
1.  V Návrháři pásu karet vyberte vlastní skupiny.  
  
2.  V **vlastnosti** okno, rozbalte **pozice** vlastnost.  
  
3.  Nastavte **PositionType** vlastnost na odpovídající hodnotu:  
  
    -   **BeforeOfficeId** umisťuje skupině před zadané předdefinované skupiny.  
  
    -   **AfterOfficeId** umisťuje skupině po zadaný předdefinovanou skupinu.  
  
4.  Nastavte **OfficeId** na ID ovládacího prvku předdefinované skupiny.  
  
     Seznam ID ovládacích prvků, naleznete v části [soubory nápovědy Office 2010: Office fluent uživatelské rozhraní ovládacího prvku identifikátory](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Kódu XML pásu karet](../vsto/ribbon-xml.md)   
 [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Postupy: Změna polohy karty na pásu karet](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Postupy: Přidání ovládacích prvků do zobrazení Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Postupy: zobrazení Add-in chyby uživatelského rozhraní](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  