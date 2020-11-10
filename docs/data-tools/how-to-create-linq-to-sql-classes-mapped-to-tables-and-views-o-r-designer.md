---
title: Mapování tříd LINQ to SQL na tabulky nebo zobrazení (O-R Designer)
description: Pochopte, jak vytvořit LINQ to SQL třídy entit (třídy, které jsou namapované na tabulky a zobrazení) v Návrhář relací objektů (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 79e5c529c1aefb4777e174489fc8fd1ca95a4111
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436343"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Postupy: Vytvoření tříd LINQ to SQL namapovaných na tabulky a zobrazení (Návrhář relací objektů)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] třídy, které jsou mapovány k tabulkám a zobrazením databáze, se nazývají *třídy entit*. Třída entity se mapuje na záznam, zatímco jednotlivé vlastnosti třídy entity jsou mapovány na jednotlivé sloupce, které tvoří záznam. Vytvořte třídy entit založené na databázových tabulkách nebo zobrazeních přetažením tabulek nebo zobrazení z **Průzkumník serveru** nebo **Průzkumníka databáze** do [nástrojů LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **Návrhář o/R** generuje třídy a použije konkrétní [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atributy pro povolení [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funkcí (možnosti komunikace a úprav dat v nástroji <xref:System.Data.Linq.DataContext> ). Podrobné informace o [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] třídách naleznete [v tématu model objektu LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> **Návrhář o/R** je jednoduché relační mapování objektů, protože podporuje jenom 1:1 vztahů s mapováním. Jinými slovy, Třída entity může mít pouze vztah 1:1 mapování s databázovou tabulkou nebo zobrazením. Komplexní mapování, jako je například mapování třídy entity na více tabulek, není podporováno. Třídu entity však lze namapovat na zobrazení, které spojuje více souvisejících tabulek.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Vytvořit LINQ to SQL třídy, které jsou mapovány na tabulky nebo zobrazení databáze

Přetahování tabulek nebo zobrazení z **Průzkumník serveru** nebo **Průzkumníka databáze** do **Návrháře relací** vytvoří třídy entit kromě <xref:System.Data.Linq.DataContext> metod, které se používají k provádění aktualizací.

Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] modul runtime vytvoří logiku pro uložení změn z aktualizovatelné třídy entity zpět do databáze. Tato logika je založena na schématu tabulky (definice sloupce a informace o primárním klíči). Pokud toto chování nechcete, můžete nakonfigurovat třídu entity tak, aby používala uložené procedury k provádění vložení, aktualizací a odstranění namísto použití výchozího [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] chování při běhu. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Vytvoření LINQ to SQL třídy, které jsou mapovány na tabulky nebo zobrazení databáze

1. V Průzkumníku **serveru** nebo **databáze** rozbalte položku **tabulky** nebo **zobrazení** a vyhledejte databázovou tabulku nebo zobrazení, které chcete použít ve své aplikaci.

2. Přetáhněte tabulku nebo zobrazení do **návrháře o/R**.

     Vytvoří se Třída entity, která se zobrazí na návrhové ploše. Třída entity obsahuje vlastnosti, které jsou mapovány na sloupce ve vybrané tabulce nebo zobrazení.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Vytvoření zdroje dat objektu a zobrazení dat ve formuláři

Po vytvoření tříd entit pomocí **návrháře o/R** můžete vytvořit objekt zdroje dat a naplnit [okno zdroje dat](add-new-data-sources.md#data-sources-window) pomocí tříd entit.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Vytvoření zdroje dat objektu na základě LINQ to SQL třídy entit

1. V nabídce **sestavení** klikněte na **Sestavit řešení** a sestavte projekt.

2. Chcete-li otevřít okno **zdroje dat** , klikněte v nabídce **data** na možnost **Zobrazit zdroje dat**.

3. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

4. Klikněte na **objekt** na stránce **Zvolte typ zdroje dat** a potom klikněte na tlačítko **Další**.

5. Rozbalte uzly a vyhledejte a vyberte svou třídu.

    > [!NOTE]
    > Pokud třída **zákazníka** není k dispozici, ukončete průvodce, sestavte projekt a spusťte průvodce znovu.

6. Kliknutím na tlačítko **Dokončit** vytvořte zdroj dat a přidejte třídu entity **zákazníka** do okna **zdroje dat** .

7. Přetáhněte položky z okna **zdroje dat** do formuláře.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: vytváření tříd LINQ to SQL (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Model objektu LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Postupy: Vytvoření přidružení (relace) mezi třídami LINQ to SQL (Návrhář relací objektů)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
