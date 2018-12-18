---
title: Vytváření vyhledávacích tabulek v aplikacích WPF | Dokumentace Microsoftu
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6ce3b1cb07256c35949591b4d6ea012f56e432c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303339"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Vytváření vyhledávacích tabulek v aplikacích WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Termín *vyhledávací tabulka* (říká se jim *vazbu vyhledávání*) popisuje ovládací prvek, který se zobrazí informace z jedné datové tabulky na základě hodnoty pole cizího klíče v druhé tabulce. Můžete vytvořit vyhledávací tabulku přetažením hlavního uzlu nadřazené tabulky nebo v objektu **zdroje dat** okna do ovládacího prvku, který je již vázán na sloupec nebo vlastnosti v související podřízené tabulce.  
  
 Předpokládejme například tabulku `Orders` v prodejní databázi. Každý záznam v `Orders` obsahuje tabulku `CustomerID` , která označuje, který zákazník objednávku vystavil. `CustomerID` Je cizí klíč odkazující na záznam zákazníka v `Customers` tabulky. Při zobrazení seznamu objednávek z `Orders` tabulky, můžete zobrazovaný název skutečných zákazníků místo `CustomerID`. Protože název zákazníka se `Customers` tabulky, je potřeba vytvořit vyhledávací tabulky pro zobrazované jméno zákazníka. Používá tabulky vyhledávání `CustomerID` hodnotu `Orders` záznam se má přejít relace a vrátí jméno zákazníka.  
  
## <a name="to-create-a-lookup-table"></a>Vytvoření vyhledávací tabulky  
  
1.  Jedním z následujících typů zdrojů dat se souvisejícími daty, přidejte do projektu:  
  
    -   Datová sada nebo modelu Entity Data Model. Další informace najdete v tématu [postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
    -   WCF Data Service, služby WCF nebo webové službě. Další informace najdete v tématu [postupy: připojení k datům ve službě](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   Objekty. Další informace najdete v tématu [postupy: připojení k datům v objektech](http://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).  
  
    > [!NOTE]
    >  Než vytvoříte vyhledávací tabulky, musí existovat dvě souvisejících tabulky nebo objekty jako zdroj dat pro projekt.  
  
2.  Otevřít**Návrhář WPF**a ujistěte se, že návrhář obsahuje kontejner, který je platný cíl pro položky v **zdroje dat** okna.  
  
     Další informace o platné cíle přetažení najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
3.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat** otevřít **zdroje dat** okna.  
  
4.  Rozbalte uzly v **zdroje dat** okna, dokud se nezobrazí nadřazená tabulka nebo objekt a související podřízené tabulky nebo objektu.  
  
    > [!NOTE]
    >  Související podřízené tabulky nebo objektu je uzel, který se zobrazí jako jeden podřízený uzel v rámci nadřazené tabulky nebo objektu.  
  
5.  Klikněte na rozevírací nabídku pro podřízený uzel a vyberte **podrobnosti**.  
  
6.  Podřízený uzel.  
  
7.  V části podřízený uzel klikněte na rozevírací nabídky, které se týkají data podřízené a nadřazené položky. (V předchozím příkladu je to **CustomerID** uzlu.) Vyberte jednu z následujících typů ovládacích prvků, které podporují vazbu vyhledávání:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Pokud **ListBox** nebo **ListView** ovládací prvek se nezobrazí v seznamu těchto ovládacích prvků můžete přidat do seznamu. Informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Vlastní ovládací prvek, který je odvozen od <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Pro informace o tom, jak přidat vlastní ovládací prvky pro seznam ovládacích prvků můžete určit pro položky v **zdroje dat** okna, naleznete v tématu [přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Přetáhněte podřízený uzel z **zdroje dat** okna do kontejneru v Návrháře WPF. (V předchozím příkladu je podřízený uzel **objednávky** uzlu.)  
  
     Visual Studio generuje XAML, který vytvoří nové ovládací prvky vázané na data pro každou z položek, které se při přetahování. XAML také přidá nový <xref:System.Windows.Data.CollectionViewSource> podřízené tabulky nebo objektu k prostředkům cíl přetažení. U některých zdrojů dat sady Visual Studio také vygeneruje kód pro načtení dat do tabulky nebo objektu. Další informace najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
9. Přetáhněte nadřazený uzel z **zdroje dat** oken na ovládací prvek vyhledávání vazby, který jste vytvořili dříve. (V předchozím příkladu je nadřazený uzel **zákazníkům** uzlu).  
  
     Visual Studio nastaví některé vlastnosti u ovládacího prvku ke konfiguraci vazby vyhledávání. V následující tabulce jsou uvedeny vlastnosti, které Visual Studio změní. Pokud třeba, můžete změnit tyto vlastnosti XAML nebo v **vlastnosti** okna.  
  
    |Vlastnost|Vysvětlivky k nastavení|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Tato vlastnost určuje vazbu, která se používá ke stahování dat, která se zobrazí v ovládacím prvku nebo kolekci. Visual Studio nastaví tuto vlastnost <xref:System.Windows.Data.CollectionViewSource> nadřazené dat jste přetáhli do ovládacího prvku.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Tato vlastnost určuje cestu položky dat, který se zobrazí v ovládacím prvku. Visual Studio nastaví tuto vlastnost na první sloupec nebo vlastnosti v nadřazené data po primárním klíči, který má datový typ string.<br /><br /> Pokud chcete zobrazit jiného sloupce nebo vlastnosti v nadřazené dat, změňte tuto vlastnost na cestu jinou vlastnost.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio váže tato vlastnost na sloupec nebo vlastnost podřízených dat, kterou jste přetáhli do návrháře. Toto je cizí klíč k datům nadřazeného.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio nastaví tuto vlastnost na cestě sloupce nebo vlastnosti podřízených dat, která je cizí klíč k datům nadřazeného.|  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Zobrazení souvisejících dat v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Návod: Zobrazování souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)

