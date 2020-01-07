---
title: Vytvoření a konfigurace datových sad
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8222b1985ab7f765be9b06fdd6abf7cb1e1cb2dc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586910"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Postupy: vytváření a konfigurace datových sad v sadě Visual Studio

Datová sada je sada objektů, které ukládají data z databáze v paměti a podporují sledování změn, aby bylo možné u těchto dat Povolit operace vytvoření, čtení, aktualizace a odstranění (CRUD), aniž by bylo nutné je vždy připojit k databázi. Datové sady byly navržené pro jednoduchou *formy nad daty* obchodních aplikací. Pro nové aplikace zvažte použití rozhraní Entity Framework ukládat a modelovat data v paměti. Pro práci s datovými sadami, byste měli mít základní znalost konceptů databáze.

Můžete vytvořit typovou třídu <xref:System.Data.DataSet> v aplikaci Visual Studio v době návrhu pomocí **Průvodce konfigurací zdroje dat**. Informace o tom, jak vytvořit datové sady prostřednictvím kódu programu, najdete v tématu [Vytvoření datové sady (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Vytvoření nové datové sady pomocí Průvodce konfigurací zdroje dat

1. Otevřete projekt v aplikaci Visual Studio a pak zvolte možnost **projekt** > **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

2. Vyberte typ zdroje dat, ke kterému se budete připojovat.

     ![Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png)

3. Vyberte databázi nebo databáze, které budou zdrojem dat pro datovou sadu.

     ![Zdroj dat – zvolit připojení](../data-tools/media/data-source-choose-a-connection.png)

4. Zvolte tabulky (nebo jednotlivé sloupce), uložených procedur, funkcí a zobrazení z databáze, kterou chcete být zastoupeny v datové sadě.

     ![Výběr databázových objektů](../data-tools/media/raddata-chose-objects.png)

5. Klikněte na **Dokončit**.

   Datová sada se zobrazí jako uzel v **Průzkumník řešení**.

   ![Datová sada v Průzkumník řešení](../data-tools/media/dataset-in-solution-explorer.png)

6. Kliknutím na uzel datová sada v **Průzkumník řešení** otevřete datovou sadu v **Návrháři DataSet**. Každá tabulka v datové sadě má přidružený objekt `TableAdapter`, který je reprezentován v dolní části. Adaptér tabulka slouží k naplnění datové sady a volitelně odesílat příkazy do databáze.

   ![Návrhář DataSet](../data-tools/media/dataset-designer.png)

7. Vztahu čáry, které spojují tabulky představují relací mezi tabulkami, jak jsou definovány v databázi. Ve výchozím omezení cizího klíče v databázi jsou reprezentovány jako vztah, aktualizace a odstranění pravidla nastavená na hodnotu none. Obvykle se jedná o co chcete. Kliknutím na řádky můžete ale vyvolat dialog **relace** , kde můžete změnit chování hierarchických aktualizací. Další informace najdete v tématu [vztahy v datových sadách](../data-tools/relationships-in-datasets.md) a [hierarchické aktualizace](../data-tools/hierarchical-update.md).

     ![Dialogové okno relace datové sady](../data-tools/media/raddata-relation-dialog.png)

8. Klepněte na tabulku, adaptér tabulky nebo název sloupce v tabulce zobrazíte její vlastnosti v **vlastnosti** okna. Některé hodnoty Tady můžete upravit. Jenom nezapomeňte, že budete upravovat datovou sadu, ne zdrojové databáze.

     ![Vlastnosti sloupce datové sady](../data-tools/media/dataset-column-properties.png)

9. Do datové sady můžete přidat nové tabulky nebo adaptéry tabulek nebo přidat nové dotazy pro existující adaptéry tabulky nebo můžete zadat nové relace mezi tabulkami přetažením těchto položek z karty **panelu nástrojů** . Tato karta se zobrazí, když je **Návrhář DataSet** aktivní.

     ![Sada nástrojů DataSet](../data-tools/media/raddata-dataset-toolbox.png)

Dále je vhodné určit, jak naplnit datovou sadu daty. K tomu použijete **Průvodce nastavením TableAdapter**. Další informace najdete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Přidat tabulku databáze nebo jiný objekt na existující sadu dat

Tento postup ukazuje, jak přidat tabulku ze stejné databáze, který jste použili k vytvoření datové sady.

1. Kliknutím na uzel datová sada v **Průzkumník řešení** přepněte **Návrháře datových sad** na fokus.

2. Klikněte na kartu **zdroje dat** na levém okraji sady Visual Studio nebo do vyhledávacího pole zadejte **zdroje dat** .

3. Klikněte pravým tlačítkem myši na uzel DataSet a vyberte možnost **Konfigurovat zdroj dat pomocí Průvodce**.

     ![Kontextová nabídka zdroje dat](../data-tools/media/data-source-context-menu.png)

4. Průvodce použijte k určení dalších tabulek, uložených procedur nebo jiných databázových objektů, které chcete přidat do datové sady.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Přidání samostatné datové tabulky do datové sady

1. Otevřete svou datovou sadu v **Návrhář Dataset**.

2. Přetáhněte <xref:System.Data.DataTable> třídy z **datovou sadu** kartě **nástrojů** na **Návrhář Dataset**.

3. Přidáte sloupce pro definování dat tabulky. Klikněte pravým tlačítkem na tabulku a vyberte **přidat** > **sloupec**. V případě potřeby nastavte datový typ sloupce a klíč pomocí okna **vlastnosti** .

Nutné implementovat samostatné tabulky `Fill` logiku v samostatných tabulkách tak, aby vám je naplnit daty. Informace o vyplnění tabulky samostatné dat, naleznete v tématu [naplnění datové sady z adaptéru dat](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Viz také:

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relace v datových sadách](../data-tools/relationships-in-datasets.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
