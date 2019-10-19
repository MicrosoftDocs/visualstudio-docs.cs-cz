---
title: Vytváření vyhledávacích tabulek v aplikacích WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a2a2179a759bc11a9466361d3c8cc2df45c12f20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648597"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Vytváření vyhledávacích tabulek v aplikacích WPF

*Vyhledávací tabulka* termínů (někdy označované jako *vyhledávací vazba*) popisuje ovládací prvek, který zobrazuje informace z jedné tabulky dat na základě hodnoty pole cizího klíče v jiné tabulce. Vyhledávací tabulku lze vytvořit přetažením hlavního uzlu nadřazené tabulky nebo objektu v okně **zdroje dat** do ovládacího prvku, který je již svázán se sloupcem nebo vlastností v související podřízené tabulce.

Předpokládejme například tabulku `Orders` v prodejní databázi. Každý záznam v `Orders` tabulce obsahuje `CustomerID`, které označují zákazníka, který objednávku zadal. @No__t_0 je cizí klíč, který odkazuje na záznam zákazníka v tabulce `Customers`. Když zobrazíte seznam objednávek z `Orders` tabulky, možná budete chtít místo `CustomerID` zobrazit skutečný název zákazníka. Vzhledem k tomu, že se název zákazníka nachází v tabulce `Customers`, je nutné vytvořit vyhledávací tabulku pro zobrazení názvu zákazníka. Vyhledávací tabulka používá hodnotu `CustomerID` v záznamu `Orders` k navigaci mezi relacemi a vrácení názvu zákazníka.

## <a name="to-create-a-lookup-table"></a>Vytvoření vyhledávací tabulky

1. Přidejte do projektu jeden z následujících typů zdrojů dat se souvisejícími daty:

    - Datová sada nebo model EDM (Entity Data Model).

    - WCF Data Service, služba WCF nebo webová služba. Další informace najdete v tématu [Postup: připojení k datům ve službě](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Objekty. Další informace naleznete v tématu [vazba na objekty v aplikaci Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Předtím, než můžete vytvořit vyhledávací tabulku, musí existovat dva související tabulky nebo objekty jako zdroj dat pro projekt.

2. Otevřete **Návrháře WPF**a ujistěte se, že Návrhář obsahuje kontejner, který je platným cílem přetažení pro položky v okně **zdroje dat** .

     Další informace o platných cílech přetažení naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3. V nabídce **data** klikněte na **Zobrazit zdroje dat** . tím otevřete okno **zdroje dat** .

4. Rozbalte uzly v okně **zdroje dat** , dokud neuvidíte nadřazenou tabulku nebo objekt a související podřízenou tabulku nebo objekt.

    > [!NOTE]
    > Související podřízená tabulka nebo objekt je uzel, který se zobrazí jako rozšiřitelný podřízený uzel v nadřazené tabulce nebo objektu.

5. Klikněte na rozevírací nabídku podřízeného uzlu a vyberte **Podrobnosti**.

6. Rozbalte podřízený uzel.

7. V podřízeném uzlu klikněte na rozevírací nabídku pro položku, která souvisí s podřízenými a nadřazenými daty. (V předchozím příkladu je to uzel **KódZákazníka** .) Vyberte jeden z následujících typů ovládacích prvků, které podporují vyhledávací vazbu:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Pokud se ovládací prvek **ListBox** nebo **ListView** v seznamu nezobrazí, můžete tyto ovládací prvky přidat do seznamu. Informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Libovolný vlastní ovládací prvek, který je odvozen z <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Informace o tom, jak přidat vlastní ovládací prvky do seznamu ovládacích prvků, které můžete vybrat pro položky v okně **zdroje dat** , naleznete v tématu [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Přetáhněte podřízený uzel z okna **zdroje dat** do kontejneru v Návrháři WPF. (V předchozím příkladu je podřízený uzel uzlem **objednávky** .)

     Visual Studio generuje XAML, které vytvoří nové ovládací prvky vázané na data pro každou položku, kterou přetáhnete. XAML také přidá novou <xref:System.Windows.Data.CollectionViewSource> pro podřízenou tabulku nebo objekt do prostředků cíle přetažení. U některých zdrojů dat Visual Studio také generuje kód pro načtení dat do tabulky nebo objektu. Další informace najdete v tématu [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Přetáhněte nadřazený uzel z okna **zdroje dat** do ovládacího prvku pro vyhledávání vazeb, který jste vytvořili dříve. (V předchozím příkladu je nadřazený uzel uzel **Customers (zákazníci** )).

     Sada Visual Studio nastaví některé vlastnosti ovládacího prvku pro konfiguraci vazby vyhledávání. V následující tabulce jsou uvedeny vlastnosti, které aplikace Visual Studio mění. V případě potřeby lze tyto vlastnosti změnit v souboru XAML nebo v okně **vlastnosti** .

    |Vlastnost|Vysvětlivky k nastavení|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Tato vlastnost určuje kolekci nebo vazbu, která se používá k získání dat zobrazených v ovládacím prvku. Sada Visual Studio nastaví tuto vlastnost na <xref:System.Windows.Data.CollectionViewSource> pro nadřazená data, která jste přetáhli do ovládacího prvku.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Tato vlastnost určuje cestu položky dat, která se zobrazí v ovládacím prvku. Sada Visual Studio nastaví tuto vlastnost na první sloupec nebo vlastnost v nadřazených datech za primární klíč, který má datový typ String.<br /><br /> Pokud chcete zobrazit v nadřazených datech jiný sloupec nebo vlastnost, změňte tuto vlastnost na cestu jiné vlastnosti.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio váže tuto vlastnost k sloupci nebo vlastnosti podřízených dat, která jste přetáhli do návrháře. Toto je cizí klíč pro nadřazená data.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Sada Visual Studio nastaví tuto vlastnost na cestu sloupce nebo vlastnosti podřízených dat, která je cizím klíčem pro nadřazená data.|

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Zobrazení souvisejících dat v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Návod: zobrazení souvisejících dat v aplikaci WPF](../data-tools/display-related-data-in-wpf-applications.md)