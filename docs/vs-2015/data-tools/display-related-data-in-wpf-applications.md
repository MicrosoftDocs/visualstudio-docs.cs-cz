---
title: Zobrazit související data v aplikacích WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6efa79fc59ed9812cf6162096dd462100b71fbca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672417"
---
# <a name="display-related-data-in-wpf-applications"></a>Zobrazení souvisejících dat v aplikacích WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V některých aplikacích můžete chtít pracovat s daty, která pocházejí z více tabulek nebo entit, které jsou vzájemně propojené v relaci typu nadřazený-podřízený. Například můžete chtít zobrazit mřížku, která bude zobrazovat zákazníky z `Customers` tabulky. Když uživatel vybere konkrétního zákazníka, další mřížka zobrazí objednávky zákazníka ze související `Orders` tabulky.

 Můžete vytvořit ovládací prvky vázané na data, které zobrazují související data přetažením položek z okna **zdroje dat** do návrháře WPF.

## <a name="to-create-controls-that-display-related-records"></a>Chcete-li vytvořit ovládací prvky, které zobrazují související záznamy

1. V nabídce **data** klikněte na **Zobrazit zdroje dat** . tím otevřete okno **zdroje dat** .

2. Klikněte na tlačítko **Přidat nový zdroj dat**a dokončete průvodce **konfigurací zdroje dat** .

3. Otevřete návrháře WPF a ujistěte se, že Návrhář obsahuje kontejner, který je platným cílem přetažení pro položky v okně **zdroje dat** .

     Další informace o platných cílech přetažení naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

4. V okně **zdroje dat** rozbalte uzel, který představuje nadřazenou tabulku nebo objekt v relaci. Nadřazená tabulka nebo objekt je na straně jedna relace 1: n.

5. Přetáhněte nadřazený uzel (nebo jakékoli jednotlivé položky v nadřazeném uzlu) z okna **zdroje dat** na platný cíl přetažení v návrháři.

     Visual Studio generuje XAML, které pro každou položku, kterou přetáhnete, vytvoří nové ovládací prvky vázané na data. XAML také přidá novou <xref:System.Windows.Data.CollectionViewSource> pro nadřazenou tabulku nebo objekt do prostředků cíle přetažení. U některých zdrojů dat Visual Studio také generuje kód pro načtení dat do nadřazené tabulky nebo objektu. Další informace najdete v tématu [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. V okně **zdroje dat** vyhledejte související podřízenou tabulku nebo objekt. Související podřízené tabulky a objekty se zobrazí jako rozbalitelné uzly v dolní části seznamu dat nadřazeného uzlu.

7. Přetáhněte podřízený uzel (nebo jakékoli jednotlivé položky v podřízeném uzlu) z okna **zdroje dat** na platný cíl přetažení v návrháři.

     Visual Studio vygeneruje XAML, které vytvoří nové ovládací prvky vázané na data pro každou položku, kterou přetáhnete. XAML také přidá novou <xref:System.Windows.Data.CollectionViewSource> pro podřízenou tabulku nebo objekt do prostředků cíle přetažení. Tento nový <xref:System.Windows.Data.CollectionViewSource> je vázán na vlastnost nadřazené tabulky nebo objektu, který jste právě přetáhli do návrháře. U některých zdrojů dat Visual Studio také generuje kód pro načtení dat do podřízené tabulky nebo objektu.

     Následující obrázek znázorňuje tabulku souvisejících **objednávek** v tabulce **Customers** v datové sadě v okně **zdroje dat** .

     ![Okno zdroje dat znázorňující relaci](../data-tools/media/datasources2.gif "DataSources2")

## <a name="see-also"></a>Viz také
 [Vazba ovládacích prvků WPF k datům v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [vytváření vyhledávacích tabulek v aplikacích WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [Návod: zobrazení souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
