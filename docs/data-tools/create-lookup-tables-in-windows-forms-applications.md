---
title: Vytváření vyhledávacích tabulek v aplikacích modelu Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9fe49ee90dba3edd0e2777817c4903c6101a1b47
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586767"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Vytváření vyhledávacích tabulek v aplikacích modelu Windows Forms

Termín *vyhledávací tabulka* popisuje ovládací prvky, které jsou svázány se dvěma tabulkami s relačními daty. Tyto vyhledávací ovládací prvky zobrazují data v první tabulce na základě hodnoty vybrané v druhé tabulce.

Vyhledávací tabulky lze vytvořit přetažením hlavního uzlu nadřazené tabulky (z [okna zdroje dat](add-new-data-sources.md#data-sources-window)) do ovládacího prvku ve formuláři, který je již svázán se sloupcem v související podřízené tabulce.

Předpokládejme například tabulku `Orders` v prodejní databázi. Každý záznam v `Orders` tabulce obsahuje `CustomerID`a indikuje, který zákazník objednávku zadal. `CustomerID` je cizí klíč odkazující na záznam zákazníka v tabulce `Customers`. V tomto scénáři rozbalíte tabulku `Orders` v okně **zdroje dat** a nastavíte hlavní uzel na **Podrobnosti**. Potom nastavte sloupec `CustomerID`, aby používal <xref:System.Windows.Forms.ComboBox> (nebo jakýkoli jiný ovládací prvek, který podporuje vyhledávací vazbu) a přetáhněte uzel `Orders` do formuláře. Nakonec Přetáhněte uzel `Customers` na ovládací prvek, který je svázán se souvisejícím sloupcem – v tomto případě <xref:System.Windows.Forms.ComboBox> svázán se sloupcem `CustomerID`.

## <a name="to-databind-a-lookup-control"></a>Vytvoření datové vazby ovládacího prvku vyhledávání

1. Otevřete projekt a otevřete okno **zdroje dat** výběrem možnosti **Zobrazit** > **jiné** **zdroje dat** > Windows.

    > [!NOTE]
    > Vyhledávací tabulky vyžadují, aby v okně **zdroje dat** byly k dispozici dvě související tabulky nebo objekty. Další informace najdete v tématu [relace v datových sadách](relationships-in-datasets.md).

2. Rozbalením uzlů v okně **zdroje dat** můžete zobrazit nadřazenou tabulku a všechny její sloupce a související podřízenou tabulku a všechny její sloupce.

    > [!NOTE]
    > Uzel podřízené tabulky je uzel, který je zobrazen v podřízeném uzlu, který lze rozbalit v nadřazené tabulce.

3. Změňte typ přetažení podřízené tabulky na **Podrobnosti** tím, že vyberete **Podrobnosti** ze seznamu ovládacích prvků v uzlu podřízené tabulky. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Vyhledejte uzel, který souvisí se dvěma tabulkami (`CustomerID` uzel v předchozím příkladu). Změňte jeho typ přetažení na <xref:System.Windows.Forms.ComboBox> tím, že vyberete položku **ComboBox** ze seznamu ovládacích prvků.

5. Přetáhněte hlavní podřízený uzel tabulky z okna **zdroje dat** do formuláře.

     Na formuláři se zobrazí ovládací prvky s datovou vazbou (včetně popisků) a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>). V zásobníku komponent se zobrazí [datová sada](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>a <xref:System.Windows.Forms.BindingNavigator>.

6. Nyní přetáhněte hlavní nadřazený uzel tabulky z okna **zdroje dat** přímo do ovládacího prvku vyhledávání (<xref:System.Windows.Forms.ComboBox>).

     Nyní jsou vytvořeny vazby vyhledávání. Konkrétní vlastnosti, které byly nastaveny v ovládacím prvku, naleznete v následující tabulce.

    |Vlastnost|Vysvětlivky k nastavení|
    |--------------| - |
    |**DataSource**|Sada Visual Studio nastaví tuto vlastnost na <xref:System.Windows.Forms.BindingSource>vytvořenou pro tabulku, kterou přetáhnete do ovládacího prvku (na rozdíl od <xref:System.Windows.Forms.BindingSource>vytvořena při vytvoření ovládacího prvku).<br /><br /> Pokud potřebujete provést úpravu, nastavte tuto hodnotu na <xref:System.Windows.Forms.BindingSource> tabulky se sloupcem, který chcete zobrazit.|
    |**DisplayMember**|Aplikace Visual Studio nastaví tuto vlastnost na první sloupec po primárním klíči, který má datový typ řetězec, u tabulky, která je přetažena na ovládací prvek.<br /><br /> Pokud potřebujete provést úpravu, nastavte tuto hodnotu na název sloupce, který chcete zobrazit.|
    |**ValueMember**|Aplikace Visual Studio nastaví tuto vlastnost na první sloupec, který je součástí primárního klíče, nebo na první sloupec v tabulce, pokud není definován žádný klíč.<br /><br /> Pokud potřebujete provést úpravu, nastavte tuto hodnotu na primární klíč v tabulce se sloupcem, který chcete zobrazit.|
    |**SelectedValue**|Sada Visual Studio nastaví tuto vlastnost na původní sloupec vyřazený z okna **zdroje dat** .<br /><br /> Pokud potřebujete provést úpravu, nastavte tuto hodnotu na sloupec cizího klíče v související tabulce.|

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
