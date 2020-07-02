---
title: 'Postupy: Přidání ovládacích prvků do zobrazení Backstage '
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5b4ea5cdcd869f16f987e9431359511831af9573
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538343"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Postupy: Přidání ovládacích prvků do zobrazení Backstage
  Pomocí Návrháře pásu karet můžete přidat ovládací prvky do nabídky, která se otevře po kliknutí na kartu **soubor** . Když aplikaci spustíte, ovládací prvky, které přidáte na kartu **soubor** , se zobrazí ve skupině s názvem **Doplňky**.

 Ovládací prvky nelze umístit před nebo za předdefinované ovládací prvky pomocí Návrháře pásu karet v aplikaci Visual Studio. Předdefinovaný ovládací prvek je ovládací prvek, který se již zobrazuje v zobrazení Backstage. Chcete-li umístit ovládací prvky před nebo po předdefinovaných ovládacích prvcích, je nutné použít kód XML pásu karet. Další informace o **pásu karet (XML)** najdete v tématu [XML pásu karet](../vsto/ribbon-xml.md). Další informace o přizpůsobení zobrazení Backstage najdete v tématu [Úvod do zobrazení Backstage office 2010 pro vývojáře](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) a [přizpůsobení zobrazení Backstage Office 2010 pro vývojáře](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Přidání ovládacích prvků do zobrazení Backstage

1. Otevřete položku pásu karet v zobrazení Návrh.

     Informace o tom, jak přidat položku **pásu karet (vizuální Návrhář)** do projektu, naleznete v tématu [How to: Začínáme Customizing a na pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. V Návrháři pásu karet klikněte na kartu **soubor** .

     Zobrazí se Návrhář nabídek. Tato návrhová plocha neobsahuje žádné ovládací prvky.

3. Na kartě **ovládací prvky pásu karet sady Office** **přetáhněte do návrháře**nabídky libovolný z následujících ovládacích prvků:

    - Tlačítko

    - CheckBox

    - Galerie

    - Nabídka

    - Oddělovač

    - SplitButton

    - ToggleButton

4. Přetáhněte ovládací prvky pro přesunutí na nové pozice v nabídce.

## <a name="see-also"></a>Viz také:
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
