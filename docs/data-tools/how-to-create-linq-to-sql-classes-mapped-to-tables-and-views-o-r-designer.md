---
title: Mapování tříd LINQ to SQL na tabulky nebo zobrazení (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b0e3103c1b4faa62ff82dafe8ba4aa0ef9193f06
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586494"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Postupy: vytváření tříd LINQ to SQL mapovaných na tabulky a zobrazení (O/R Designer)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] třídy, které jsou mapovány k tabulkám a zobrazením databáze, se nazývají *třídy entit*. Třída entity se mapuje na záznam, zatímco jednotlivé vlastnosti třídy entity jsou mapovány na jednotlivé sloupce, které tvoří záznam. Vytvořte třídy entit založené na databázových tabulkách nebo zobrazeních přetažením tabulek nebo zobrazení z **Průzkumník serveru** nebo **Průzkumníka databáze** do [nástrojů LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **Návrhář o/R** generuje třídy a použije konkrétní atributy [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] k povolení funkcí [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] (funkce pro komunikaci a úpravy dat <xref:System.Data.Linq.DataContext>). Podrobné informace o třídách [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] naleznete v [modelu LINQ to SQL objektů](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> **O/R Designer** je jednoduchý objekt relační Mapovač, protože podporuje pouze relace mapování 1:1. Jinými slovy třídu entity může mít pouze mapování 1:1 relaci s databázové tabulky nebo zobrazení. Komplexní mapování, jako je například mapování třídy entity na více tabulek, není podporováno. Třídu entity však lze namapovat na zobrazení, které spojuje více souvisejících tabulek.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Vytvořit LINQ to SQL třídy, které jsou mapovány na tabulky nebo zobrazení databáze

Přetahování tabulek nebo zobrazení z **Průzkumník serveru** nebo **Průzkumníka databáze** do **Návrháře relací** vytvoří třídy entit kromě <xref:System.Data.Linq.DataContext> metod, které se používají k provádění aktualizací.

Ve výchozím nastavení vytvoří modul runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] logiku pro uložení změn z aktualizovatelné třídy entity zpět do databáze. Tato logika je založena na schématu tabulky (definice sloupce a informace o primárním klíči). Pokud toto chování nechcete, můžete nakonfigurovat třídu entity, aby používala uložené procedury k provádění vložení, aktualizací a odstranění namísto použití výchozího [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]ho chování za běhu. Další informace najdete v tématu [postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Vytvoření LINQ to SQL třídy, které jsou mapovány na tabulky nebo zobrazení databáze

1. V Průzkumníku **serveru** nebo **databáze**rozbalte položku **tabulky** nebo **zobrazení** a vyhledejte databázovou tabulku nebo zobrazení, které chcete použít ve své aplikaci.

2. Přetáhněte tabulku nebo zobrazení do **návrháře o/R**.

     Vytvoří se Třída entity, která se zobrazí na návrhové ploše. Třída entity obsahuje vlastnosti, které jsou mapovány na sloupce ve vybrané tabulce nebo zobrazení.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Vytvoření zdroje dat objektu a zobrazení dat ve formuláři

Po vytvoření tříd entit pomocí **návrháře o/R**můžete vytvořit objekt zdroje dat a naplnit [okno zdroje dat](add-new-data-sources.md#data-sources-window) pomocí tříd entit.

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

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: vytváření tříd LINQ to SQL (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Model objektu LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Postupy: Vytvoření přidružení (relace) mezi třídami LINQ to SQL (Návrhář relací objektů)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
