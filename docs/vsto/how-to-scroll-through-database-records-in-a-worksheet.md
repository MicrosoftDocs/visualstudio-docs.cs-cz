---
title: 'Postupy: procházení databázových záznamů na listu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8127a5f61e292fb777be4854796535bbe01226aa
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545792"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Postupy: procházení databázových záznamů na listu
  Následující postup ukazuje, jak použít návrháře k zobrazení jednoho pole z databázové tabulky v systém Microsoft Office excelovém listu s ovládacími prvky, které umožňují koncovému uživateli procházet všechny záznamy.

 Návrhář lze použít pouze v projektech na úrovni dokumentu. Můžete však také přidat ovládací prvky a vytvořit jejich svázání s daty programově v době běhu. Další informace najdete v tématu [Návod: jednoduché datové vazby v projektu doplňku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Procházení záznamů databáze na listu

1. Otevřete projekt aplikace Excelu v aplikaci Visual Studio.

2. Otevřete okno **zdroje dat** a vytvořte z databáze zdroj dat. Další informace najdete v tématu [Přidání nových připojení](../data-tools/add-new-connections.md).

3. Rozbalte tabulku obsahující data, která chcete zobrazit, a vyberte konkrétní sloupec.

4. Otevřete seznam ovládacích prvků a vyberte **NamedRange**.

5. Přetáhněte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek na buňku, kde se mají zobrazovat data.

6. Na kartě **model Windows Forms** **panelu nástrojů**přidejte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek do listu a nastavte ovládací prvky, které chcete použít. Další informace najdete v tématu [Přehled ovládacího prvku BindingNavigator &#40;model Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Viz také:
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
