---
title: Vytváření vyhledávacích tabulek v aplikacích Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c52e5f157dcbc6dcfeacf72df465bd3d8d9d172e
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304911"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Vytváření vyhledávacích tabulek v aplikacích Windows Forms

Termín *vyhledávací tabulka* popisuje ovládací prvky, které jsou vázány na dvě související tabulky dat. Tyto vyhledávací ovládací prvky zobrazují data v první tabulce na základě hodnoty vybrané v druhé tabulce.

Vyhledávací tabulky lze vytvořit přetažením hlavního uzlu nadřazené tabulky (z [okna zdroje dat](add-new-data-sources.md#data-sources-window)) na ovládací prvek na formuláři, který je již vázán na sloupec v související podřízené tabulky.

Předpokládejme například tabulku `Orders` v prodejní databázi. Každý záznam v `Orders` obsahuje tabulku `CustomerID`, určující, který zákazník objednávku vystavil. `CustomerID` je cizí klíč odkazující na záznam zákazníka v tabulce `Customers`. V tomto scénáři, rozbalte `Orders` v tabulku **zdroje dat** okno a nastavit hlavní uzel **podrobnosti**. Potom nastavte `CustomerID` sloupce <xref:System.Windows.Forms.ComboBox> (nebo jakýkoli jiný ovládací prvek, který podporuje vazbu vyhledávání) a přetáhněte ji `Orders` uzlu do formuláře. A konečně, přetáhněte `Customers` uzlu na ovládací prvek, který je vázán na odpovídající sloupec – v tomto případě <xref:System.Windows.Forms.ComboBox> vázán na `CustomerID` sloupce.

## <a name="to-databind-a-lookup-control"></a>Vytvoření datové vazby ovládacího prvku vyhledávání

1.  S projektem open, Otevřít **zdroje dat** okno výběrem **zobrazení** > **ostatní Windows** > **zdroje dat**.

    > [!NOTE]
    > Vyhledávací tabulky vyžadují dvě souvisejících tabulky nebo objekty jsou k dispozici v **zdroje dat** okna. Další informace najdete v tématu [vztahy v datových sadách](relationships-in-datasets.md).

2.  Rozbalte uzly v **zdroje dat** okna, dokud se nezobrazí nadřazená tabulka a všechny její sloupce a také související podřízené tabulky a všechny jejich sloupce.

    > [!NOTE]
    > Uzel podřízené tabulky je uzel, který je zobrazen v podřízeném uzlu, který lze rozbalit v nadřazené tabulce.

3.  Změňte typ přetažení podřízené tabulky na **podrobnosti** tak, že vyberete **podrobnosti** ze seznamu ovládacího prvku na uzlu podřízené tabulky. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  Vyhledejte uzel, který odpovídá oběma tabulkám ( `CustomerID` uzlu v předchozím příkladu). Změnit jeho typ přetažení <xref:System.Windows.Forms.ComboBox> tak, že vyberete **– pole se seznamem** ze seznamu ovládacích prvků.

5.  Přetáhněte hlavní uzel podřízené tabulky z **zdroje dat** okna do formuláře.

     Na formuláři se zobrazí ovládací prvky s datovou vazbou (včetně popisků) a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>). A [datovou sadu](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.

6.  Nyní přetáhněte hlavní uzel nadřazené tabulky z **zdroje dat** okno přímo na ovládací prvek vyhledávání ( <xref:System.Windows.Forms.ComboBox>).

     Nyní jsou vytvořeny vazby vyhledávání. Naleznete v následující tabulce pro konkrétní vlastnosti, které byly nastaveny na ovládacím prvku.

    |Vlastnost|Vysvětlivky k nastavení|
    |--------------| - |
    |**Zdroj dat**|Visual Studio nastaví tuto vlastnost <xref:System.Windows.Forms.BindingSource>, které byly vytvořeny pro tabulky přetažena na ovládací prvek (nikoli <xref:System.Windows.Forms.BindingSource>, vytvořené při vytvoření ovládacího prvku).<br /><br /> Pokud potřebujete provést úpravu, nastavte <xref:System.Windows.Forms.BindingSource> tabulky se sloupcem, kterou chcete zobrazit.|
    |**DisplayMember**|Aplikace Visual Studio nastaví tuto vlastnost na první sloupec po primárním klíči, který má datový typ řetězec, u tabulky, která je přetažena na ovládací prvek.<br /><br /> Pokud potřebujete provést úpravu, nastavte na název sloupce, které chcete zobrazit.|
    |**ValueMember**|Aplikace Visual Studio nastaví tuto vlastnost na první sloupec, který je součástí primárního klíče, nebo na první sloupec v tabulce, pokud není definován žádný klíč.<br /><br /> Pokud potřebujete provést úpravu, nastavte na primární klíč tabulky se sloupcem, který chcete zobrazit.|
    |**SelectedValue**|Visual Studio nastaví tuto vlastnost na původní sloupec vyřadit z **zdroje dat** okna.<br /><br /> Pokud potřebujete provést úpravu, nastavte na sloupce cizího klíče v související tabulce.|

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)