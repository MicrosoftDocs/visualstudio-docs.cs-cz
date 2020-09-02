---
title: Vytváření vyhledávacích tabulek v aplikacích WPF | Microsoft Docs
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6816b7465b8a3271ec6ebc0db5046d76e60ec5b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657428"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Vytváření vyhledávacích tabulek v aplikacích WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Vyhledávací tabulka* termínů (někdy označované jako *vyhledávací vazba*) popisuje ovládací prvek, který zobrazuje informace z jedné tabulky dat na základě hodnoty pole cizího klíče v jiné tabulce. Vyhledávací tabulku lze vytvořit přetažením hlavního uzlu nadřazené tabulky nebo objektu v okně **zdroje dat** do ovládacího prvku, který je již svázán se sloupcem nebo vlastností v související podřízené tabulce.

 Předpokládejme například tabulku `Orders` v prodejní databázi. Každý záznam v `Orders` tabulce obsahuje položku `CustomerID` , která označuje zákazníka, který objednávku zadal. `CustomerID`Je cizí klíč, který odkazuje na záznam zákazníka v `Customers` tabulce. Když zobrazíte seznam objednávek z `Orders` tabulky, možná budete chtít zobrazit skutečný název zákazníka namísto `CustomerID` . Vzhledem k tomu, že je název zákazníka v `Customers` tabulce, je nutné vytvořit vyhledávací tabulku pro zobrazení názvu zákazníka. Vyhledávací tabulka používá `CustomerID` `Orders` k navigaci vztahu hodnotu v záznamu a vrací jméno zákazníka.

## <a name="to-create-a-lookup-table"></a>Vytvoření vyhledávací tabulky

1. Přidejte do projektu jeden z následujících typů zdrojů dat se souvisejícími daty:

    - Datová sada nebo model EDM (Entity Data Model).

    - WCF Data Service, služba WCF nebo webová služba. Další informace najdete v tématu [Postup: připojení k datům ve službě](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Objekty. Další informace najdete v tématu [Postup: připojení k datům v objektech](https://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).

    > [!NOTE]
    > Předtím, než můžete vytvořit vyhledávací tabulku, musí existovat dva související tabulky nebo objekty jako zdroj dat pro projekt.

2. Otevřete**Návrháře WPF**a ujistěte se, že Návrhář obsahuje kontejner, který je platným cílem přetažení pro položky v okně **zdroje dat** .

     Další informace o platných cílech přetažení naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

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

    - Libovolný vlastní ovládací prvek, který je odvozen z <xref:System.Windows.Controls.Primitives.Selector> .

        > [!NOTE]
        > Informace o tom, jak přidat vlastní ovládací prvky do seznamu ovládacích prvků, které můžete vybrat pro položky v okně **zdroje dat** , naleznete v tématu [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Přetáhněte podřízený uzel z okna **zdroje dat** do kontejneru v Návrháři WPF. (V předchozím příkladu je podřízený uzel uzlem **objednávky** .)

     Visual Studio generuje XAML, které vytvoří nové ovládací prvky vázané na data pro každou položku, kterou přetáhnete. XAML také přidá novou <xref:System.Windows.Data.CollectionViewSource> pro podřízenou tabulku nebo objekt do prostředků cíle přetažení. U některých zdrojů dat Visual Studio také generuje kód pro načtení dat do tabulky nebo objektu. Další informace najdete v tématu [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

9. Přetáhněte nadřazený uzel z okna **zdroje dat** do ovládacího prvku pro vyhledávání vazeb, který jste vytvořili dříve. (V předchozím příkladu je nadřazený uzel uzel **Customers (zákazníci** )).

     Sada Visual Studio nastaví některé vlastnosti ovládacího prvku pro konfiguraci vazby vyhledávání. V následující tabulce jsou uvedeny vlastnosti, které aplikace Visual Studio mění. V případě potřeby lze tyto vlastnosti změnit v souboru XAML nebo v okně **vlastnosti** .

    |Vlastnost|Vysvětlivky k nastavení|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Tato vlastnost určuje kolekci nebo vazbu, která se používá k získání dat zobrazených v ovládacím prvku. Sada Visual Studio nastaví tuto vlastnost na <xref:System.Windows.Data.CollectionViewSource> Nadřazená data, která jste přetáhli do ovládacího prvku.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Tato vlastnost určuje cestu položky dat, která se zobrazí v ovládacím prvku. Sada Visual Studio nastaví tuto vlastnost na první sloupec nebo vlastnost v nadřazených datech za primární klíč, který má datový typ String.<br /><br /> Pokud chcete zobrazit v nadřazených datech jiný sloupec nebo vlastnost, změňte tuto vlastnost na cestu jiné vlastnosti.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio váže tuto vlastnost k sloupci nebo vlastnosti podřízených dat, která jste přetáhli do návrháře. Toto je cizí klíč pro nadřazená data.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Sada Visual Studio nastaví tuto vlastnost na cestu sloupce nebo vlastnosti podřízených dat, která je cizím klíčem pro nadřazená data.|

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků WPF k datům v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [BIND ovládací prvky WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Zobrazit související data v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md) [Návod: zobrazení souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
