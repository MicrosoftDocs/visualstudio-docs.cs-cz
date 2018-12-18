---
title: Rozdělování datových sad a objektů TableAdapter do různých projektů
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 01e572a2ac20d1cfb103e1600307b51bdf58a0b8
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174316"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Rozdělování datových sad a objektů TableAdapter do různých projektů
Vylepšili jsme typové datové sady, aby [objekty TableAdapter](create-and-configure-tableadapters.md) a do samostatné projekty se můžou generovat třídy datové sady. To umožňuje rychle samostatné aplikace a generovat vícevrstvých datových aplikací.

Následující postup popisuje proces používání **Návrhář Dataset** pro generování kódu datovou sadu do projektu, který je oddělen od projektu, který obsahuje kód generované třídy TableAdapter.

## <a name="separate-datasets-and-tableadapters"></a>Rozdělování datových sad a TableAdapters
Když oddělíte datové sady kód z třídy TableAdapter kódu projektu, který obsahuje kód datovou sadu musí nacházet v aktuálním řešení. Pokud není tento projekt v aktuálním řešení, nebude k dispozici v **projektu DataSet** v seznamu **vlastnosti** okna.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Chcete rozdělit datovou sadu do jiného projektu

1.  Otevřete řešení, která obsahuje datovou sadu (*XSD* souboru).

    > [!NOTE]
    >  Pokud řešení obsahuje projekt, do kterého chcete rozdělení kódu datovou sadu, vytvořte projekt nebo přidat existující projekt do řešení.

2.  Poklikejte na soubor typové datové sady ( *XSD* souborů) v **Průzkumníku řešení** otevření datové sady v **Návrhář Dataset**.

3.  Vyberte prázdnou oblast **Návrhář Dataset**.

4.  V **vlastnosti** okna, vyhledejte **projektu DataSet** uzlu.

5.  V **projektu DataSet** vyberte název projektu, do které chcete generovat kód datové sady.

     Jakmile vyberete projekt, do které chcete generovat kód datovou sadu **soubor datové sady** vlastnost se vyplní výchozí název souboru. Tento název lze změnit v případě potřeby. Kromě toho pokud chcete generovat kód datovou sadu do konkrétního adresáře, můžete nastavit **složky projektu** nastavte na název složky.

    > [!NOTE]
    >  Když oddělíte datové sady a objekty TableAdapter (nastavením **projektu DataSet** vlastnost), existující částečné třídy v projektu nebudou automaticky přesunuty. Existující částečné třídy je nutné ručně přesunout do projektu datové sady.

6.  Uložte datovou sadu.

     Generování kódu datovou sadu do vybraného projektu v **projektu DataSet** vlastnost a **TableAdapter** do aktuálního projektu bude vygenerován kód.

Ve výchozím nastavení po oddělíte datové sady a kód třídy TableAdapter, výsledkem je soubor samostatné třídy v každém projektu. Původní projekt obsahuje soubor s názvem *DatasetName.Designer.vb* (nebo *DatasetName.Designer.cs*), která obsahuje kód objektu TableAdapter. Projekt, který je zadaný ve **projektu Dataset** vlastnost má soubor s názvem *DatasetName.DataSet.Designer.vb* (nebo *DatasetName.DataSet.Designer.cs*), který obsahuje kód datové sady.

> [!NOTE]
>  Chcete-li zobrazit soubor generované třídy, vyberte datovou sadu nebo projekt TableAdapter. Potom v **Průzkumníka řešení**vyberte **zobrazit všechny soubory**.

## <a name="see-also"></a>Viz také:

- [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)
- [Návod: Vytvoření N-vrstvá datové aplikace](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)