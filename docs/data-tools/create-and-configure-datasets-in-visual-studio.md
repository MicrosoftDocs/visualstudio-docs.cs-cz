---
title: Vytvoření a konfigurace datových sad
description: Vytváření a konfigurace datových sad v sadě Visual Studio. Datová sada je sada objektů, které ukládají data z databáze v paměti a podporují operace CRUD u těchto dat.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5a9a10d68b5b0617b5c4e2152cbbbb920a7c683f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435401"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Postupy: vytváření a konfigurace datových sad v sadě Visual Studio

Datová sada je sada objektů, které ukládají data z databáze v paměti a podporují sledování změn, aby bylo možné u těchto dat Povolit operace vytvoření, čtení, aktualizace a odstranění (CRUD), aniž by bylo nutné je vždy připojit k databázi. Datové sady byly navrženy pro jednoduché *formy datových* podnikových aplikací. U nových aplikací zvažte použití Entity Framework k ukládání a modelování dat v paměti. Pokud chcete pracovat s datovými sadami, měli byste mít základní znalosti konceptů databáze.

Můžete vytvořit typovou <xref:System.Data.DataSet> třídu v aplikaci Visual Studio v době návrhu pomocí **Průvodce konfigurací zdroje dat**. Informace o tom, jak vytvořit datové sady prostřednictvím kódu programu, najdete v tématu [Vytvoření datové sady (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Vytvoření nové datové sady pomocí Průvodce konfigurací zdroje dat

1. Otevřete projekt v aplikaci Visual Studio a pak zvolte **projekt**  >  **Přidat nový zdroj dat** . spustí se **Průvodce konfigurací zdroje dat**.

2. Vyberte typ zdroje dat, ke kterému se budete připojovat.

     ![Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png)

3. Vyberte databázi nebo databáze, které budou zdrojem dat pro datovou sadu.

     ![Zdroj dat – zvolit připojení](../data-tools/media/data-source-choose-a-connection.png)

4. Vyberte tabulky (nebo jednotlivé sloupce), uložené procedury, funkce a zobrazení z databáze, které chcete znázornit v datové sadě.

     ![Výběr databázových objektů](../data-tools/media/raddata-chose-objects.png)

5. Klikněte na **Finish** (Dokončit).

   Datová sada se zobrazí jako uzel v **Průzkumník řešení**.

   ![Datová sada v Průzkumník řešení](../data-tools/media/dataset-in-solution-explorer.png)

6. Kliknutím na uzel datová sada v **Průzkumník řešení** otevřete datovou sadu v **Návrháři DataSet**. Každá tabulka v datové sadě má přidružený `TableAdapter` objekt, který je reprezentován v dolní části. K naplnění datových sad a volitelně posílání příkazů do databáze slouží adaptér s tabulkou.

   ![Návrhář DataSet](../data-tools/media/dataset-designer.png)

7. Řádky relace, které spojují tabulky, znázorňují relace tabulek, jak jsou definovány v databázi. Ve výchozím nastavení jsou omezení cizího klíče v databázi reprezentována pouze jako relace, přičemž pravidla aktualizace a odstranění jsou nastavena na hodnotu None. Obvykle to je to, co chcete. Kliknutím na řádky můžete ale vyvolat dialog **relace** , kde můžete změnit chování hierarchických aktualizací. Další informace najdete v tématu [relace v datových sadách](../data-tools/relationships-in-datasets.md) a [hierarchické aktualizaci](../data-tools/hierarchical-update.md).

     ![Dialogové okno relace datové sady](../data-tools/media/raddata-relation-dialog.png)

8. Kliknutím na tabulku, adaptér tabulky nebo název sloupce v tabulce zobrazíte její vlastnosti v okně **vlastnosti** . Tady můžete upravit některé z těchto hodnot. Stačí si pamatovat, že upravujete datovou sadu, nikoli zdrojovou databázi.

     ![Vlastnosti sloupce datové sady](../data-tools/media/dataset-column-properties.png)

9. Do datové sady můžete přidat nové tabulky nebo adaptéry tabulek nebo přidat nové dotazy pro existující adaptéry tabulky nebo můžete zadat nové relace mezi tabulkami přetažením těchto položek z karty **panelu nástrojů** . Tato karta se zobrazí, když je **Návrhář DataSet** aktivní.

     ![Sada nástrojů DataSet](../data-tools/media/raddata-dataset-toolbox.png)

Dále je vhodné určit, jak naplnit datovou sadu daty. V takovém případě použijete **Průvodce konfigurací TableAdapter**. Další informace najdete v tématu [vyplňování datových sad pomocí objekty TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Přidat databázovou tabulku nebo jiný objekt do existující datové sady

Tento postup ukazuje, jak přidat tabulku ze stejné databáze, kterou jste použili k prvnímu vytvoření datové sady.

1. Kliknutím na uzel datová sada v **Průzkumník řešení** přepněte **Návrháře datových sad** na fokus.

2. Klikněte na kartu **zdroje dat** na levém okraji sady Visual Studio nebo do vyhledávacího pole zadejte **zdroje dat** .

3. Klikněte pravým tlačítkem myši na uzel DataSet a vyberte možnost **Konfigurovat zdroj dat pomocí Průvodce**.

     ![Kontextová nabídka zdroje dat](../data-tools/media/data-source-context-menu.png)

4. Průvodce použijte k určení dalších tabulek, uložených procedur nebo jiných databázových objektů, které chcete přidat do datové sady.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Přidat do datové sady samostatnou datovou tabulku

1. Otevřete datovou sadu v **Návrhář datových sad**.

2. Přetáhněte <xref:System.Data.DataTable> třídu z karty **datová sada** **panelu nástrojů** na **Návrhář datových sad**.

3. Přidejte sloupce pro definování tabulky dat. Klikněte pravým tlačítkem myši na tabulku a vyberte možnost **Přidat**  >  **sloupec**. V případě potřeby nastavte datový typ sloupce a klíč pomocí okna **vlastnosti** .

Samostatné tabulky musí implementovat `Fill` logiku v samostatných tabulkách, abyste je mohli vyplnit daty. Informace o tom, jak vyplnit samostatné tabulky dat, naleznete v tématu [naplnění datové sady z DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Viz také

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relace v datových sadách](../data-tools/relationships-in-datasets.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
