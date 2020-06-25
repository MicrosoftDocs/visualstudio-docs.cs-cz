---
title: Vytváření vyhledávacích tabulek v aplikacích modelu Windows Forms
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9a1ae368b7d2bf8548bf78a6a9795e19206bc277
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282654"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Vytváření vyhledávacích tabulek v aplikacích modelu Windows Forms

Termín *vyhledávací tabulka* popisuje ovládací prvky, které jsou svázány se dvěma tabulkami s relačními daty. Tyto vyhledávací ovládací prvky zobrazují data v první tabulce na základě hodnoty vybrané v druhé tabulce.

Vyhledávací tabulky lze vytvořit přetažením hlavního uzlu nadřazené tabulky (z [okna zdroje dat](add-new-data-sources.md#data-sources-window)) do ovládacího prvku ve formuláři, který je již svázán se sloupcem v související podřízené tabulce.

Předpokládejme například tabulku `Orders` v prodejní databázi. Každý záznam v `Orders` tabulce obsahuje a `CustomerID` označuje, který zákazník objednávku zadal. `CustomerID` je cizí klíč odkazující na záznam zákazníka v tabulce `Customers`. V tomto scénáři rozbalíte `Orders` tabulku v okně **zdroje dat** a nastavíte hlavní uzel na **Podrobnosti**. Potom nastavte `CustomerID` sloupec na použití <xref:System.Windows.Forms.ComboBox> (nebo jakýkoli jiný ovládací prvek, který podporuje vyhledávací vazbu) a přetáhněte `Orders` uzel do formuláře. Nakonec přetáhněte `Customers` uzel na ovládací prvek, který je svázán se sloupcem v relaci – v tomto případě je <xref:System.Windows.Forms.ComboBox> svázán se `CustomerID` sloupcem.

## <a name="to-databind-a-lookup-control"></a>Vytvoření datové vazby ovládacího prvku vyhledávání

1. Otevřete projekt a otevřete okno **zdroje dat** výběrem možnosti **Zobrazit**  >  **ostatní**  >  **zdroje dat**systému Windows.

    > [!NOTE]
    > Vyhledávací tabulky vyžadují, aby v okně **zdroje dat** byly k dispozici dvě související tabulky nebo objekty. Další informace najdete v tématu [relace v datových sadách](relationships-in-datasets.md).

2. Rozbalením uzlů v okně **zdroje dat** můžete zobrazit nadřazenou tabulku a všechny její sloupce a související podřízenou tabulku a všechny její sloupce.

    > [!NOTE]
    > Uzel podřízené tabulky je uzel, který je zobrazen v podřízeném uzlu, který lze rozbalit v nadřazené tabulce.

3. Změňte typ přetažení podřízené tabulky na **Podrobnosti** tím, že vyberete **Podrobnosti** ze seznamu ovládacích prvků v uzlu podřízené tabulky. Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Vyhledejte uzel, který se týká dvou tabulek ( `CustomerID` uzel v předchozím příkladu). Změňte jeho typ přetažení na a <xref:System.Windows.Forms.ComboBox> , a to tak, že vyberete položku **ComboBox** ze seznamu ovládacích prvků.

5. Přetáhněte hlavní podřízený uzel tabulky z okna **zdroje dat** do formuláře.

     Na formuláři se zobrazí ovládací prvky s datovou vazbou (včetně popisků) a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>). [Datová sada](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> zobrazí se v zásobníku komponent.

6. Nyní přetáhněte hlavní nadřazený uzel tabulky z okna **zdroje dat** přímo do ovládacího prvku vyhledávání ( <xref:System.Windows.Forms.ComboBox> .).

     Nyní jsou vytvořeny vazby vyhledávání. Konkrétní vlastnosti, které byly nastaveny v ovládacím prvku, naleznete v následující tabulce.

    |Vlastnost|Vysvětlivky k nastavení|
    |--------------| - |
    |**Datového**|Sada Visual Studio nastaví tuto vlastnost na hodnotu <xref:System.Windows.Forms.BindingSource> vytvořenou pro tabulku, kterou přetáhnete do ovládacího prvku (na rozdíl od třídy <xref:System.Windows.Forms.BindingSource> , která byla vytvořena při vytvoření ovládacího prvku).<br /><br /> Pokud potřebujete provést úpravu, nastavte tuto hodnotu na <xref:System.Windows.Forms.BindingSource> tabulku se sloupcem, který chcete zobrazit.|
    |**DisplayMember**|Aplikace Visual Studio nastaví tuto vlastnost na první sloupec po primárním klíči, který má datový typ řetězec, u tabulky, která je přetažena na ovládací prvek.<br /><br /> Pokud potřebujete provést úpravu, nastavte tuto hodnotu na název sloupce, který chcete zobrazit.|
    |**ValueMember**|Aplikace Visual Studio nastaví tuto vlastnost na první sloupec, který je součástí primárního klíče, nebo na první sloupec v tabulce, pokud není definován žádný klíč.<br /><br /> Pokud potřebujete provést úpravu, nastavte tuto hodnotu na primární klíč v tabulce se sloupcem, který chcete zobrazit.|
    |**SelectedValue**|Sada Visual Studio nastaví tuto vlastnost na původní sloupec vyřazený z okna **zdroje dat** .<br /><br /> Pokud potřebujete provést úpravu, nastavte tuto hodnotu na sloupec cizího klíče v související tabulce.|

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
