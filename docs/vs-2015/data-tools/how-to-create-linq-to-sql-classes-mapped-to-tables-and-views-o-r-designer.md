---
title: 'Postupy: vytváření tříd LINQ to SQL mapovaných na tabulky a zobrazení (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665929"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Postupy: Vytvoření tříd LINQ to SQL namapovaných na tabulky a zobrazení (Návrhář relací objektů)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL třídy, které jsou mapovány k tabulkám a zobrazením databáze, se nazývají *třídy entit*. Třída entity se mapuje na záznam, zatímco jednotlivé vlastnosti třídy entity jsou mapovány na jednotlivé sloupce, které tvoří záznam. Vytvořte třídy entit založené na databázových tabulkách nebo zobrazeních přetažením tabulek nebo zobrazení z **Průzkumník serveru** / **Průzkumník databáze** do [nástrojů LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Vygeneruje třídy a použije konkrétní [! LINQ to SQL atributů, které se mají povolit [! Funkce LINQ to SQL (funkce pro komunikaci a úpravy dat <xref:System.Data.Linq.DataContext> ). Podrobné informace o produktu [! LINQ to SQL třídy naleznete v [modelu LINQ to SQL objektů](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Je jednoduché relační mapování objektů, protože podporuje pouze 1:1 vztahů. Jinými slovy, Třída entity může mít pouze vztah 1:1 mapování s databázovou tabulkou nebo zobrazením. Komplexní mapování, jako je například mapování třídy entity na více tabulek, není podporováno. Třídu entity však lze namapovat na zobrazení, které spojuje více souvisejících tabulek.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Vytvořit LINQ to SQL třídy, které jsou mapovány na tabulky nebo zobrazení databáze
 **Server Explorer** / **Database Explorer** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Kromě <xref:System.Data.Linq.DataContext> metod, které se používají k provádění aktualizací, můžete přetahovat tabulky a zobrazení z Průzkumník serveru Průzkumníku databáze na třídy vytváření entit.

 Ve výchozím nastavení [! LINQ to SQL runtime vytvoří logiku pro uložení změn z aktualizovatelné třídy entity zpátky do databáze. Tato logika je založena na schématu tabulky (definice sloupce a informace o primárním klíči). Pokud toto chování nechcete, můžete pro třídu entity nakonfigurovat použití uložených procedur k provádění vložení, aktualizací a odstranění namísto použití výchozího nastavení [! LINQ to SQL chování modulu runtime. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Vytvoření LINQ to SQL třídy, které jsou mapovány na tabulky nebo zobrazení databáze

1. V **Server** / **Průzkumníku Server Database**rozbalte **tabulky** nebo **zobrazení** a vyhledejte databázovou tabulku nebo zobrazení, které chcete použít v aplikaci.

2. Přetáhněte tabulku nebo zobrazení na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

     Vytvoří se Třída entity, která se zobrazí na návrhové ploše. Třída entity obsahuje vlastnosti, které jsou mapovány na sloupce ve vybrané tabulce nebo zobrazení.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Vytvoření zdroje dat objektu a zobrazení dat ve formuláři
 Po vytvoření tříd entit pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] můžete vytvořit objekt zdroje dat a naplnit [okno zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) pomocí tříd entit.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Vytvoření zdroje dat objektu na základě LINQ to SQL třídy entit

1. V nabídce **sestavení** klikněte na **Sestavit řešení** a sestavte projekt.

2. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

3. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

4. Klikněte na **objekt** na stránce **Zvolte typ zdroje dat** a potom klikněte na tlačítko **Další**.

5. Rozbalte uzly a vyhledejte a vyberte svou třídu.

    > [!NOTE]
    > Pokud třída **zákazníka** není k dispozici, ukončete průvodce, sestavte projekt a spusťte průvodce znovu.

6. Kliknutím na tlačítko **Dokončit** vytvořte zdroj dat a přidejte třídu entity **zákazníka** do okna **zdroje dat** .

7. Přetáhněte položky z okna **zdroje dat** do formuláře.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: vytváření tříd LINQ to SQL (Návrhář O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Metody DataContext (Návrhář relací objektů)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Objektový model LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Návod: Přidání ověřování do tříd entit](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Postupy: Vytvoření přidružení (relace) mezi třídami LINQ to SQL (Návrhář relací objektů)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)