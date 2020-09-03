---
title: Vytváření vyhledávacích tabulek v aplikacích model Windows Forms | Microsoft Docs
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
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72630938"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Vytváření vyhledávacích tabulek v aplikacích modelu Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Termín *vyhledávací tabulka* popisuje ovládací prvky, které jsou svázány se dvěma tabulkami s relačními daty. Tyto vyhledávací ovládací prvky zobrazují data v první tabulce na základě hodnoty vybrané v druhé tabulce.

 Vyhledávací tabulky lze vytvořit přetažením hlavního uzlu nadřazené tabulky (z [okna zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) do ovládacího prvku ve formuláři, který je již svázán se sloupcem v související podřízené tabulce.

 Předpokládejme například tabulku `Orders` v prodejní databázi. Každý záznam v `Orders` tabulce obsahuje a `CustomerID` označuje, který zákazník objednávku zadal. `CustomerID` je cizí klíč odkazující na záznam zákazníka v tabulce `Customers`. V tomto scénáři rozbalíte `Orders` tabulku v okně **zdroje dat** a nastavíte hlavní uzel na **Podrobnosti**. Potom nastavte `CustomerID` sloupec na použít <xref:System.Windows.Forms.ComboBox> (nebo jakýkoli jiný ovládací prvek, který podporuje vyhledávací vazbu) a přetáhněte uzel do `Orders` formuláře. Nakonec přetáhněte `Customers` uzel na ovládací prvek, který je svázán se sloupcem v relaci – v tomto případě je <xref:System.Windows.Forms.ComboBox> svázán se `CustomerID` sloupcem.

## <a name="to-databind-a-lookup-control"></a>Vytvoření datové vazby ovládacího prvku vyhledávání

1. Otevřete okno **zdroje dat** .

    > [!NOTE]
    > Vyhledávací tabulky vyžadují, aby v okně **zdroje dat** byly k dispozici dvě související tabulky nebo objekty.

2. Rozbalením uzlů v okně **zdroje dat** můžete zobrazit nadřazenou tabulku a všechny její sloupce a související podřízenou tabulku a všechny její sloupce.

    > [!NOTE]
    > Uzel podřízené tabulky je uzel, který je zobrazen v podřízeném uzlu, který lze rozbalit v nadřazené tabulce.

3. Změňte typ přetažení podřízené tabulky na **Podrobnosti** tím, že vyberete **Podrobnosti** ze seznamu ovládacích prvků v uzlu podřízené tabulky. Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Vyhledejte uzel, který se týká dvou tabulek ( `CustomerID` uzel v předchozím příkladu). Změňte jeho typ přetažení na a <xref:System.Windows.Forms.ComboBox> , a to tak, že vyberete položku **ComboBox** ze seznamu ovládacích prvků.

5. Přetáhněte hlavní podřízený uzel tabulky z okna **zdroje dat** do formuláře.

     Na formuláři se zobrazí ovládací prvky s datovou vazbou (včetně popisků) a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>). [Datová sada](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> zobrazí se v zásobníku komponent.

6. Nyní přetáhněte hlavní nadřazený uzel tabulky z okna **zdroje dat** přímo do ovládacího prvku vyhledávání ( <xref:System.Windows.Forms.ComboBox> .).

     Nyní jsou vytvořeny vazby vyhledávání. Specifické vlastnosti, které byly nastaveny na ovládacím prvku, naleznete v tabulce níže.

    |Vlastnost|Vysvětlivky k nastavení|
    |--------------|----------------------------|
    |**Datového**|Aplikace Visual Studio nastaví tuto vlastnost na zdroj <xref:System.Windows.Forms.BindingSource> vytvořený pro tabulku, která byla přetažena na ovládací prvek (na rozdíl od zdroje <xref:System.Windows.Forms.BindingSource> vytvořeného při vytvoření ovládacího prvku).<br /><br /> Pokud je nutné provést úpravu, nastavte ji na zdroj <xref:System.Windows.Forms.BindingSource> tabulky se sloupcem, který chcete zobrazit.|
    |**DisplayMember**|Aplikace Visual Studio nastaví tuto vlastnost na první sloupec po primárním klíči, který má datový typ řetězec, u tabulky, která je přetažena na ovládací prvek.<br /><br /> Pokud je nutné provést úpravu, nastavte tuto vlastnost na název sloupce, který chcete zobrazit.|
    |**ValueMember**|Aplikace Visual Studio nastaví tuto vlastnost na první sloupec, který je součástí primárního klíče, nebo na první sloupec v tabulce, pokud není definován žádný klíč.<br /><br /> Pokud je nutné provést úpravu, nastavte tuto vlastnost na primární klíč u tabulky se sloupcem, který chcete zobrazit.|
    |**SelectedValue**|Sada Visual Studio nastaví tuto vlastnost na původní sloupec vyřazený z okna **zdroje dat** .<br /><br /> Pokud je nutné provést úpravu, proveďte nastavení na sloupec cizího klíče v související tabulce.|

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
