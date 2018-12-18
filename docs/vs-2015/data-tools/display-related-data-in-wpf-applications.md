---
title: Zobrazení souvisejících dat v aplikacích WPF | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f6c939ee1a64834bd305d0ae744d9ac02e3b4410
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174139"
---
# <a name="display-related-data-in-wpf-applications"></a>Zobrazení souvisejících dat v aplikacích WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V některých aplikacích můžete chtít pracovat s daty, která pochází z více tabulkami nebo entitami, které se vztahují k sobě navzájem ve vztahu nadřazený podřízený. Například můžete chtít zobrazit mřížku, která zobrazí zákazníky z `Customers` tabulky. Když uživatel vybere konkrétního zákazníka, jiné mřížce zobrazené objednávek tohoto zákazníka ze se souvisejícím `Orders` tabulky.  
  
 Můžete vytvořit ovládací prvky vázané na data, které zobrazují související data přetažením položek z **zdroje dat** okno do Návrháře WPF.  
  
## <a name="to-create-controls-that-display-related-records"></a>Chcete-li vytvořit ovládací prvky, které zobrazení souvisejících záznamů  
  
1.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat** otevřít **zdroje dat** okna.  
  
2.  Klikněte na tlačítko **přidat nový zdroj dat**a proveďte **konfigurace zdroje dat** průvodce.  
  
3.  Otevření Návrháře WPF a ujistěte se, že návrhář obsahuje kontejner, který je platný cíl pro položky v **zdroje dat** okna.  
  
     Další informace o platné cíle přetažení najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  V **zdroje dat** okna, rozbalte uzel, který představuje nadřazené tabulky nebo objekt v relaci. Nadřazené tabulky nebo objektu je na straně "1" vztah jeden mnoho.  
  
5.  Přetáhněte nadřazený uzel (nebo všechny jednotlivé položky v nadřazeném uzlu) z **zdroje dat** okna do cíle přetažení platný v návrháři.  
  
     Visual Studio generuje XAML, který vytvoří nové ovládací prvky vázané na data pro každou položku, která se při přetahování. XAML také přidá nový <xref:System.Windows.Data.CollectionViewSource> nadřazené tabulky nebo objektu k prostředkům cíl přetažení. U některých zdrojů dat sady Visual Studio také vygeneruje kód pro načtení dat do nadřazené tabulky nebo objektu. Další informace najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  V **zdroje dat** okně vyhledejte související podřízené tabulky nebo objektu. Související podřízené tabulky a objekty se zobrazí jako rozbalovací uzly v dolní části seznamu nadřazený uzel data.  
  
7.  Přetáhněte podřízený uzel (nebo všechny jednotlivé položky v podřízený uzel) z **zdroje dat** okna do cíle přetažení platný v návrháři.  
  
     Visual Studio generuje XAML, který vytvoří nové ovládací prvky vázané na data pro každou z položek, které při přetahování. XAML také přidá nový <xref:System.Windows.Data.CollectionViewSource> podřízené tabulky nebo objektu k prostředkům cíl přetažení. Tato nová <xref:System.Windows.Data.CollectionViewSource> vazba na vlastnost nadřazené tabulky nebo objekt, který jste právě přetáhli do návrháře. U některých zdrojů dat sady Visual Studio také vygeneruje kód pro načtení dat do podřízené tabulky nebo objektu.  
  
     Následující obrázek ukazuje související **objednávky** tabulku **zákazníkům** tabulky v datové sadě v **zdroje dat** okna.  
  
     ![Okno zdroje dat zobrazuje vztah](../data-tools/media/datasources2.gif "DataSources2")  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Vytváření vyhledávacích tabulek v aplikacích WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Návod: Zobrazování souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)

