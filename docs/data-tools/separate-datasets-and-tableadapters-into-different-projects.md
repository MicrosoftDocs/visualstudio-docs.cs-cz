---
title: Rozdělování datových sad a objektů TableAdapter do různých projektů
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9198378c5acf492216e2bebaceb210073766ea23
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648190"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Rozdělování datových sad a objektů TableAdapter do různých projektů
Typové datové sady byly vylepšeny, takže třídy [objekty TableAdapter](create-and-configure-tableadapters.md) a DataSet lze generovat do samostatných projektů. Díky tomu můžete rychle oddělit aplikační vrstvy a generovat n-vrstvou datovou aplikaci.

Následující postup popisuje proces použití **Návrhář datových sad** k vygenerování kódu datové sady do projektu, který je oddělený od projektu, který obsahuje generovaný kód TableAdapter.

## <a name="separate-datasets-and-tableadapters"></a>Oddělení datových sad a objekty TableAdapter
Když oddělíte kód datové sady z TableAdapter kódu, projekt, který obsahuje kód datové sady, se musí nacházet v aktuálním řešení. Pokud tento projekt není v aktuálním řešení, nebude k dispozici v seznamu **projektů DataSet** v okně **vlastnosti** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Oddělení datové sady do jiného projektu

1. Otevřete řešení, které obsahuje datovou sadu (soubor *. xsd* ).

    > [!NOTE]
    > Pokud řešení neobsahuje projekt, ve kterém chcete oddělit svůj kód datové sady, vytvořte projekt nebo přidejte existující projekt do řešení.

2. Dvojím kliknutím na typový soubor DataSet (soubor *. xsd* ) v **Průzkumník řešení** otevřete datovou sadu v **Návrhář datových sad**.

3. Vyberte prázdnou oblast **Návrhář datových sad**.

4. V okně **vlastnosti** vyhledejte uzel **projekt datové sady** .

5. V seznamu **projekt datové sady** vyberte název projektu, do kterého chcete generovat kód datové sady.

     Po výběru projektu, do kterého chcete generovat kód datové sady, se vlastnost **souboru DataSet** naplní výchozím názvem souboru. V případě potřeby můžete tento název změnit. Kromě toho, pokud chcete vygenerovat kód datové sady do konkrétního adresáře, můžete nastavit vlastnost **Složka projektu** na název složky.

    > [!NOTE]
    > Při oddělení datových sad a objekty TableAdapter (nastavením vlastnosti **projektu DataSet** ) existující částečné třídy datové sady v projektu nebudou automaticky přesunuty. Existující třídy částečné datové sady je nutné přesunout ručně do projektu datové sady.

6. Uložte datovou sadu.

     Kód datové sady je vygenerován do vybraného projektu ve vlastnosti **projektu DataSet** a kód **TableAdapter** je vygenerován do aktuálního projektu.

Ve výchozím nastavení platí, že po oddělení datové sady a kódu TableAdapter je výsledkem diskrétní soubor třídy v každém projektu. Původní projekt obsahuje soubor s názvem *DataSet. Designer. vb* (nebo *DatasetName.Designer.cs*), který obsahuje kód TableAdapter. Projekt, který je určen vlastností **projektu DataSet** , má soubor pojmenovaný *DataSet. DataSet. Designer. vb* (nebo *DatasetName.DataSet.Designer.cs*), který obsahuje kód datové sady.

> [!NOTE]
> Chcete-li zobrazit vygenerovaný soubor třídy, vyberte projekt DataSet nebo TableAdapter. Pak v **Průzkumník řešení**vyberte možnost **Zobrazit všechny soubory**.

## <a name="see-also"></a>Viz také:

- [Přehled N-vrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)
- [Návod: vytvoření N-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)