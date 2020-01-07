---
title: 'Návod: Vytváření DataTable v Návrháři DataSet'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1526a5f4137ece5b76c282255af3da4ab20ac119
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586000"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Návod: vytvoření DataTable v Návrhář datových sad

Tento návod vysvětluje, jak vytvořit <xref:System.Data.DataTable> (bez TableAdapter) pomocí **Návrhář datových sad**. Informace o vytváření tabulek dat, které obsahují objekty TableAdapter, najdete v tématu [Create and Configure objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Vytvoření nové aplikace model Windows Forms

1. V aplikaci Visual Studio v nabídce **soubor** vyberte **Nový** > **projekt**.

2. V levém podokně rozbalte buď **vizuál C#**  , nebo **Visual Basic** a pak vyberte **Desktop Windows**.

3. V prostředním podokně vyberte typ projektu **aplikace model Windows Forms** .

4. Pojmenujte projekt **DataTableWalkthrough**a klikněte na **tlačítko OK**.

     Projekt **DataTableWalkthrough** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="add-a-new-dataset-to-the-application"></a>Přidání nové datové sady do aplikace

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

     **Přidat novou položku** zobrazí se dialogové okno.

2. V levém podokně vyberte **data**a potom v prostředním podokně vyberte **datová sada** .

3. Zvolte **přidat**.

     Visual Studio přidá do projektu soubor s názvem **DataSet1. xsd** a otevře ho v **Návrhář datových sad**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Přidání nového objektu DataTable do datové sady

1. Přetáhněte **DataTable** z karty **DataSet** sady **nástrojů** na **Návrhář datových sad**.

     Do datové sady se přidá tabulka s názvem **datatabulka1** .

2. Klikněte na záhlaví **datatabulka1** a přejmenujte ho `Music`.

## <a name="add-columns-to-the-datatable"></a>Přidat sloupce do objektu DataTable

1. Klikněte pravým tlačítkem myši na tabulku **hudba** . Přejděte na **Přidat**a potom klikněte na **sloupec**.

2. Pojmenujte sloupec `SongID`.

3. V okně **vlastnosti** nastavte vlastnost <xref:System.Data.DataColumn.DataType%2A> na hodnotu <xref:System.Int16?displayProperty=fullName>.

4. Tento postup opakujte a přidejte následující sloupce:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Nastavte primární klíč pro tabulku.

Všechny tabulky dat musí mít primární klíč. Primární klíč jednoznačně identifikuje konkrétní záznam v tabulce dat.

Primární klíč nastavíte tak, že kliknete pravým tlačítkem na sloupec **SongID** a pak kliknete na **nastavit primární klíč**. Vedle sloupce **SongID** se zobrazí ikona klíče.

## <a name="save-your-project"></a>Uložení projektu

Chcete-li uložit projekt **DataTableWalkthrough** , vyberte v nabídce **soubor** možnost **Uložit vše**.

## <a name="see-also"></a>Viz také:

- [Vytvoření a konfigurace datových sad v sadě Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Ověřování dat](../data-tools/validate-data-in-datasets.md)
