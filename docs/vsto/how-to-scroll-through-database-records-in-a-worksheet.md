---
title: 'Postupy: procházení databázových záznamů na listu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e9ffaffdefda98e3e074467fcd4df8cacce91b4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676077"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Postupy: procházení databázových záznamů na listu
  Následující postup ukazuje, jak používat návrháře zobrazíte jedno pole z databázové tabulky v aplikaci Microsoft Office Excel listu s ovládacími prvky, které umožňují koncovým uživatelům procházet všechny záznamy.  
  
 Návrháři můžete použít jenom v projektech na úrovni dokumentu. Můžete však také přidat ovládací prvky a svázat s daty prostřednictvím kódu programu za běhu. Další informace najdete v tématu [návod: jednoduché datové vazby v projektu doplňku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Procházení databázových záznamů na listu  
  
1.  Otevřete projekt aplikace Excel v sadě Visual Studio.  
  
2.  Otevřít **zdroje dat** okno a vytvořit zdroj dat z databáze. Další informace najdete v tématu [přidat nové připojení](../data-tools/add-new-connections.md).  
  
3.  Rozbalit tabulku, která obsahuje data, která chcete zobrazit a vybrat konkrétní sloupec.  
  
4.  Otevřete seznam ovládacích prvků a vyberte **NamedRange**.  
  
5.  Přetáhněte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do buňky, kam chcete data zobrazí.  
  
6.  Z **Windows Forms** kartě **nástrojů**, přidejte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek do listu a nastavit ovládací prvky, které chcete použít. Další informace najdete v tématu [BindingNavigator – Přehled ovládacího prvku &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Viz také:  
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  