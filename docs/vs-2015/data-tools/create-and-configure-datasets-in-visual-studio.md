---
title: Vytvoření a konfigurace datové sady
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 33b272143c58058d23945986ea9b6594183307c9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065214"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Vytvoření a konfigurace datových sad v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


A *datovou sadu* je sada objektů, které ukládají data z databáze v paměti a podporují řešení change tracking umožňuje vytvářet, číst, aktualizovat a odstranění (CRUD) operací na těchto datech, aniž byste museli být neustále připojeni k databázi. Datové sady byly navržené pro jednoduchou *formy nad daty* obchodních aplikací. Pro nové aplikace zvažte použití rozhraní Entity Framework ukládat a modelovat data v paměti. Pro práci s datovými sadami, byste měli mít základní znalost konceptů databáze.

 Vytvoříte typovaného <xref:System.Data.DataSet> třídy v sadě Visual Studio v době návrhu pomocí **Průvodce konfigurací zdroje dat**. Informace o vytváření datových sad prostřednictvím kódu programu najdete v tématu [vytvoření datové sady](http://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Vytvoření nové datové sady pomocí Průvodce konfigurací zdroje dat

1.  Na **projektu** nabídky, klikněte na tlačítko **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.

2.  Zvolte typ zdroje dat, který se budou připojovat k.

     ![Průvodce konfigurací zdroje dat](../data-tools/media/data-source-configuration-wizard.png "Průvodce konfigurací zdroje dat")

3.  Pro databáze zvolte databázi nebo databáze, které mají být zdroje dat pro datové sady.

     ![Zdroj dat zvolte připojení](../data-tools/media/data-source-choose-a-connection.png "zvolte připojení zdroje dat")

4.  Zvolte tabulky (nebo jednotlivé sloupce), uložených procedur, funkcí a zobrazení z databáze, kterou chcete být zastoupeny v datové sadě.

     ![Zvolit databázové objekty](../data-tools/media/raddata-chose-objects.png "raddata zvolit objekty")

5.  Klikněte na tlačítko **Dokončit**.

6.  Datová sada se zobrazí jako uzel v **Průzkumníka řešení**:

     ![Datová sada v Průzkumníku řešení](../data-tools/media/dataset-in-solution-explorer.png "datovou sadu v Průzkumníku řešení")

     Klikněte na tento uzel a datová sada se zobrazí v **Návrhář DataSet**. Všimněte si, že má každá tabulka v datové sadě přidruženého objektu TableAdapter, který je reprezentován v dolní části. Adaptér tabulka slouží k naplnění datové sady a volitelně odesílat příkazy do databáze.

     ![Návrhář DataSet](../data-tools/media/dataset-designer.png "návrháře datových sad")

7.  Vztahu čáry, které spojují tabulky představují relací mezi tabulkami, jak jsou definovány v databázi. Ve výchozím omezení cizího klíče v databázi jsou reprezentovány jako vztah, aktualizace a odstranění pravidla nastavená na hodnotu none. Obvykle se jedná o co chcete. Ale můžete kliknout na řádky, zobrazí se **vztah** dialogové okno, kde můžete změnit chování hierarchických aktualizací. Další informace najdete v tématu [vztahy v datových sadách](../data-tools/relationships-in-datasets.md) a [hierarchické aktualizace](../data-tools/hierarchical-update.md).

     ![Dialogové okno datové sady vztah](../data-tools/media/raddata-relation-dialog.png "raddata vztah dialogového okna")

8.  Klepněte na tabulku, adaptér tabulky nebo název sloupce v tabulce zobrazíte její vlastnosti v **vlastnosti** okna. Některé hodnoty Tady můžete upravit. Jenom nezapomeňte, že budete upravovat datovou sadu, ne zdrojové databáze.

     ![Vlastnosti sloupce datové sady](../data-tools/media/dataset-column-properties.png "vlastnosti sloupce datové sady")

9. Můžete přidat nové tabulky nebo adaptéry tabulek do datové sady, nebo přidejte nové dotazy pro existující adaptéry tabulek nebo zadejte nové vztahy mezi tabulkami přetažením položky z **nástrojů** kartu. Na této kartě se zobrazí, když **Návrhář DataSet** je aktivní.

     ![Datová sada nástrojů](../data-tools/media/raddata-dataset-toolbox.png "raddata datové sady nástrojů")

10. V dalším kroku budete pravděpodobně chtít určete, jak k naplnění datové sady daty. K tomu použijete **Průvodce nastavením TableAdapter**. Další informace najdete v tématu [vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Přidat tabulku databáze nebo jiný objekt na existující sadu dat
 Tento postup ukazuje, jak přidat tabulku ze stejné databáze, který jste použili k vytvoření datové sady.

1.  Klikněte na uzel datové sady v **Průzkumníka řešení** zapojit návrháři datových sad do fokus.

2.  Klikněte na tlačítko **zdroje dat** kartu na levém okraji sady Visual Studio, nebo zadejte `Data Sources` v **rychlé spuštění**.

3.  Klikněte pravým tlačítkem na uzel datové sady a vyberte **konfigurace zdroje dat pomocí průvodce** .

     ![Kontextová nabídka zdroje dat](../data-tools/media/data-source-context-menu.png "zdroj dat místní nabídky")

4.  Chcete-li určit, jaké další tabulky, nebo uložené procedury nebo jiný objekt databáze, přidat do datové sady pomocí průvodce.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Přidání samostatné datové tabulky do datové sady

1.  Otevřete svou datovou sadu v **Návrhář Dataset**.

2.  Přetáhněte <xref:System.Data.DataTable> třídy z **datovou sadu** kartě **nástrojů** na **Návrhář Dataset**.

3.  Přidáte sloupce pro definování dat tabulky. Další informace najdete v tématu [postupy: Přidání sloupců do DataTable určitého](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4.  Nutné implementovat samostatné tabulky `Fill` logiku v samostatných tabulkách tak, aby vám je naplnit daty. Informace o vyplnění tabulky samostatné dat, naleznete v tématu [naplnění datové sady z adaptéru dat](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
