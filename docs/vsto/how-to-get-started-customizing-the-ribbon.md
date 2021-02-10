---
title: 'Postupy: Začínáme s přizpůsobením pásu karet'
description: Naučte se přizpůsobit pás karet aplikace systém Microsoft Office, přidejte položku pásu karet (vizuální Návrhář) nebo položku pásu karet (XML) do projektu Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d82d059166b9efbb80ed6ce4cffcbb973235b01b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953913"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Postupy: Začínáme s přizpůsobením pásu karet
  Chcete-li přizpůsobit pás systém Microsoft Office aplikace, přidejte položku pás **karet (vizuální Návrhář)** nebo položku **pásu karet (XML)** do projektu sady Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Přidání pásu karet do projektu

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte možnost **pás karet (vizuální Návrhář)** nebo **pás karet (XML)**. Další informace o těchto šablonách najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

3. Do pole **název** zadejte název položky pásu karet.

    Názvy nesmí obsahovat tyto znaky:

   - Libra (#)

   - Procento (%)

   - Ampersand (&)

   - Hvězdička (*)

   - Svislá čára (|)

   - Zpětné lomítko ( \\ )

   - Dvojtečka (:)

   - Dvojité uvozovky (")

   - Menší než ( \< )

   - Větší než (>)

   - Otazník (?)

   - Lomítko (/)

   - Mezery na začátku nebo na konci (' ')

   - Názvy vyhrazené pro Windows nebo DOS, například (nul, AUX, "con", "COM1", "LPT1" atd.)

4. Klikněte na **OK**.

   Položka pásu karet se zobrazí v **Průzkumník řešení**. Další informace o dalších krocích najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Viz také
- [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
- [Pás karet – XML](../vsto/ribbon-xml.md)
- [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
