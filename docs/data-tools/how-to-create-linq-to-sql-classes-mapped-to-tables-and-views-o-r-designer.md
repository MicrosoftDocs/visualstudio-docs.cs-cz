---
title: 'Postupy: vytvoření LINQ na třídy SQL namapovaných na tabulky a zobrazení (Návrhář O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b66559061f0d66699a7505c71541b237814812c4
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305595"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Postupy: vytvoření LINQ na třídy SQL namapovaných na tabulky a zobrazení (O/R Designer)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] třídy, které jsou mapovány na databázové tabulky a zobrazení se nazývají *tříd entit*. Třída entity se mapuje na záznam, zatímco jednotlivé vlastnosti třídy entity se mapují na jednotlivé sloupce, které tvoří záznam. Vytvoření tříd entit, které jsou založené na databázových tabulek nebo zobrazení přetažením tabulky a zobrazení z **Průzkumníka serveru** nebo **Průzkumník databáze** na [technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **O/R Designer** vygeneruje třídy a platí konkrétní [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atributy se mají povolit [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funkce (datovou komunikaci a možnosti Úpravy <xref:System.Data.Linq.DataContext>). Podrobné informace o [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] naleznete v tématu třídy, [The LINQ to SQL objektový model](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> **O/R Designer** je jednoduchý objekt relační Mapovač, protože podporuje pouze relace mapování 1:1. Jinými slovy třídu entity může mít pouze mapování 1:1 relaci s databázové tabulky nebo zobrazení. Komplexní mapování, jako je například mapování třídu entity k několika tabulkám, se nepodporuje. Ale můžete namapovat třídu entity k zobrazení, které spojí více souvisejícími tabulkami.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Vytvoření LINQ na třídy SQL, které jsou mapovány do databáze tabulky a zobrazení

Přetažení tabulky nebo zobrazení z **Průzkumníka serveru** nebo **Průzkumník databáze** na **O/R Designer** vytvoří tříd entit kromě <xref:System.Data.Linq.DataContext> metody, která slouží k provádění aktualizací.

Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] modul runtime vytvoří logiku pro uložení změn z třídy aktualizovat entitu zpět do databáze. Tato logika je založená na schéma tabulky (definice sloupců a informacemi o primárním klíči). Pokud nechcete, aby toto chování, můžete nakonfigurovat třídu entity k pouze pomocí uložených procedur provést vložení, aktualizace a odstranění, místo použití výchozí hodnoty [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] chování za běhu. Další informace najdete v tématu [postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>K vytvoření LINQ na třídy SQL, které jsou mapovány do databáze tabulky a zobrazení

1.  V **Server** nebo **Průzkumník databáze**, rozbalte **tabulky** nebo **zobrazení** a vyhledejte databázové tabulky nebo zobrazení, že chcete používat ve vaší aplikace.

2.  Přetáhněte tabulku nebo zobrazení do **O/R Designer**.

     Třídu entity se vytvoří a zobrazí na návrhové ploše. Třída entity má vlastnosti, které se mapují na sloupce ve vybrané tabulky nebo zobrazení.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Vytvořit objektový zdroj dat a zobrazení dat ve formuláři

Po vytvoření tříd entit pomocí **O/R Designer**, můžete vytvořit objektový zdroj dat a naplnění [okna zdroje dat](add-new-data-sources.md#data-sources-window) pomocí tříd entit.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Chcete-li vytvořit zdroj dat objektu, který je založen na LINQ třídy SQL entity

1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení** k sestavení projektu.

2.  Chcete-li otevřít **zdroje dat** okno na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

3.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.

4.  Klikněte na tlačítko **objekt** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.

5.  Rozbalte uzly a vyhledejte a vyberte třídu.

    > [!NOTE]
    > Pokud **zákazníka** třída není k dispozici, zavřete průvodce, sestavte projekt a spusťte průvodce znovu.

6.  Klikněte na tlačítko **Dokončit** vytvořit zdroj dat a přidat **zákazníka** třídu entity **zdroje dat** okna.

7.  Přetáhněte položky z **zdroje dat** okna do formuláře.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: Vytvoření LINQ na třídy SQL (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL objektový model](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Postupy: Vytvoření přidružení (relace) mezi třídami LINQ to SQL (Návrhář relací objektů)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)