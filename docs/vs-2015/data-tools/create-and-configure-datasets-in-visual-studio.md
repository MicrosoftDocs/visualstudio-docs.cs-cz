---
title: Vytvoření a konfigurace datových sad
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
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631195"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Vytvoření a konfigurace datových sad v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Datová sada* je sada objektů, které ukládají data z databáze v paměti a podporují sledování změn, aby bylo možné u těchto dat Povolit operace vytvoření, čtení, aktualizace a odstranění (CRUD), aniž by bylo nutné je vždy připojit k databázi. Datové sady byly navrženy pro jednoduché *formy datových* podnikových aplikací. U nových aplikací zvažte použití Entity Framework k ukládání a modelování dat v paměti. Pokud chcete pracovat s datovými sadami, měli byste mít základní znalosti konceptů databáze.

 Můžete vytvořit typovou třídu <xref:System.Data.DataSet> v aplikaci Visual Studio v době návrhu pomocí **Průvodce konfigurací zdroje dat**. Informace o tom, jak vytvořit datovou sadu programově, naleznete v tématu [Vytvoření datové sady](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Vytvoření nové datové sady pomocí Průvodce konfigurací zdroje dat

1. V nabídce **projekt** klikněte na možnost **Přidat nový zdroj dat** a spusťte **Průvodce konfigurací zdroje dat**.

2. Vyberte typ zdroje dat, ke kterému se budete připojovat.

     ![Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png "Průvodce konfigurací zdroje dat")

3. Pro databáze vyberte databázi nebo databáze, které budou zdrojem dat pro datovou sadu.

     ![Zdroj dat – zvolit připojení](../data-tools/media/data-source-choose-a-connection.png "Zdroj dat – zvolit připojení")

4. Vyberte tabulky (nebo jednotlivé sloupce), uložené procedury, funkce a zobrazení z databáze, které chcete znázornit v datové sadě.

     ![Výběr databázových objektů](../data-tools/media/raddata-chose-objects.png "raddata zvolit objekty")

5. Klikněte na tlačítko **Dokončit**.

6. Datová sada se zobrazí jako uzel v **Průzkumník řešení**:

     ![Datová sada v Průzkumník řešení](../data-tools/media/dataset-in-solution-explorer.png "Datová sada v Průzkumník řešení")

     Klikněte na tento uzel a datová sada se zobrazí v **Návrháři DataSet**. Všimněte si, že každá tabulka v datové sadě má přidružený objekt TableAdapter, který je reprezentován v dolní části. K naplnění datových sad a volitelně posílání příkazů do databáze slouží adaptér s tabulkou.

     ![Návrhář DataSet](../data-tools/media/dataset-designer.png "Návrhář DataSet")

7. Řádky relace, které spojují tabulky, znázorňují relace tabulek, jak jsou definovány v databázi. Ve výchozím nastavení jsou omezení cizího klíče v databázi reprezentována pouze jako relace, přičemž pravidla aktualizace a odstranění jsou nastavena na hodnotu None. Obvykle to je to, co chcete. Kliknutím na řádky můžete ale vyvolat dialog **relace** , kde můžete změnit chování hierarchických aktualizací. Další informace najdete v tématu [relace v datových sadách](../data-tools/relationships-in-datasets.md) a [hierarchické aktualizaci](../data-tools/hierarchical-update.md).

     ![Dialogové okno relace datové sady](../data-tools/media/raddata-relation-dialog.png "dialog vztahu raddata")

8. Kliknutím na tabulku, adaptér tabulky nebo název sloupce v tabulce zobrazíte její vlastnosti v okně **vlastnosti** . Tady můžete upravit některé z těchto hodnot. Stačí si pamatovat, že upravujete datovou sadu, nikoli zdrojovou databázi.

     ![Vlastnosti sloupce datové sady](../data-tools/media/dataset-column-properties.png "Vlastnosti sloupce datové sady")

9. Do datové sady můžete přidat nové tabulky nebo adaptéry tabulek nebo přidat nové dotazy pro existující adaptéry tabulky nebo můžete zadat nové relace mezi tabulkami přetažením těchto položek z karty **panelu nástrojů** . Tato karta se zobrazí, když je **Návrhář DataSet** aktivní.

     ![Sada nástrojů DataSet](../data-tools/media/raddata-dataset-toolbox.png "Sada nástrojů DataSet raddata")

10. Dále budete pravděpodobně chtít zadat, jak naplnit datovou sadu daty. V takovém případě použijete **Průvodce konfigurací TableAdapter**. Další informace najdete v tématu [vyplňování datových sad pomocí objekty TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Přidat databázovou tabulku nebo jiný objekt do existující datové sady
 Tento postup ukazuje, jak přidat tabulku ze stejné databáze, kterou jste použili k prvnímu vytvoření datové sady.

1. Kliknutím na uzel datová sada v **Průzkumník řešení** přepněte návrháře datových sad na fokus.

2. Klikněte na kartu **zdroje dat** na levém okraji sady Visual Studio nebo zadejte `Data Sources` v **Rychlé spuštění**.

3. Klikněte pravým tlačítkem myši na uzel DataSet a vyberte možnost **Konfigurovat zdroj dat pomocí Průvodce** .

     ![Kontextová nabídka zdroje dat](../data-tools/media/data-source-context-menu.png "Kontextová nabídka zdroje dat")

4. Průvodce použijte k určení dalších tabulek, uložených procedur nebo jiného databázového objektu, který chcete přidat do datové sady.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Přidat do datové sady samostatnou datovou tabulku

1. Otevřete datovou sadu v **Návrhář datových sad**.

2. Přetáhněte třídu <xref:System.Data.DataTable> z karty **DataSet** sady **nástrojů** na **Návrhář datových sad**.

3. Přidejte sloupce pro definování tabulky dat. Další informace najdete v tématu [Postup: Přidání sloupců do objektu DataTable](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Samostatné tabulky musí implementovat logiku `Fill` v samostatných tabulkách, abyste je mohli vyplnit daty. Informace o tom, jak vyplnit samostatné tabulky dat, naleznete v tématu [naplnění datové sady z DataAdapter](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
