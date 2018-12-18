---
title: 'Postupy: vytvoření LINQ na třídy SQL namapovaných na tabulky a zobrazení (O R Designer) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 550fc362cf1652df48e029461a4d5fbdc6f04006
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269530"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Postupy: vytvoření LINQ na třídy SQL namapovaných na tabulky a zobrazení (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ na třídy SQL, které jsou mapovány na databázové tabulky a zobrazení se nazývají *tříd entit*. Třída entity se mapuje na záznam, zatímco jednotlivé vlastnosti třídy entity se mapují na jednotlivé sloupce, které tvoří záznam. Vytvoření tříd entit, které jsou založené na databázových tabulek nebo zobrazení přetažením tabulky a zobrazení z **Průzkumníka serveru**/**Průzkumník databáze** na [nástrojů LINQ to SQL v Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Vygeneruje třídy a platí konkrétní [! Technologie LINQ to SQL atributy umožňují [! Technologie LINQ to SQL funkce (datovou komunikaci a možnosti Úpravy <xref:System.Data.Linq.DataContext>). Podrobné informace o [! Třídy LINQ to SQL, najdete v článku [The LINQ to SQL objektový Model](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Je jednoduchý objekt relační Mapovač, protože podporuje pouze relace mapování 1:1. Jinými slovy třídu entity může mít pouze mapování 1:1 relaci s databázové tabulky nebo zobrazení. Komplexní mapování, jako je například mapování třídu entity k několika tabulkám, se nepodporuje. Ale můžete namapovat třídu entity k zobrazení, které spojí více souvisejícími tabulkami.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Vytvoření třídy LINQ to SQL, které jsou mapovány do databáze tabulky a zobrazení
 Přetažení tabulky nebo zobrazení z **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] vytvoří tříd entit kromě <xref:System.Data.Linq.DataContext> metody, které se používají pro Probíhá aktualizace.

 Ve výchozím nastavení [! Technologie LINQ to SQL runtime vytvoří logiku pro uložení změn z třídy aktualizovat entitu zpět do databáze. Tato logika je založená na schéma tabulky (definice sloupců a informacemi o primárním klíči). Pokud nechcete, aby toto chování, můžete nakonfigurovat třídu entity k provedení operace vložení, aktualizace, pomocí uložených procedur a odstraní místo použití výchozí [! Technologie LINQ to SQL chování za běhu. Další informace najdete v tématu [postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>K vytvoření LINQ na třídy SQL, které jsou mapovány do databáze tabulky a zobrazení

1.  V **Server**/**Průzkumník databáze**, rozbalte **tabulky** nebo **zobrazení** a vyhledejte databázové tabulky nebo zobrazení, který má pro použití ve vaší aplikaci.

2.  Přetáhněte tabulku nebo zobrazení do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Třídu entity se vytvoří a zobrazí na návrhové ploše. Třída entity má vlastnosti, které se mapují na sloupce ve vybrané tabulky nebo zobrazení.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Vytvořit objektový zdroj dat a zobrazení dat ve formuláři
 Po vytvoření tříd entit pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], můžete vytvořit objektový zdroj dat a naplnění [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) pomocí tříd entit.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Chcete-li vytvořit zdroj dat objektu, který je založen na LINQ třídy SQL entity

1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení** k sestavení projektu.

2.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

3.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.

4.  Klikněte na tlačítko **objekt** na **zvolte typ zdroje dat** stránce a potom klikněte na tlačítko **Další**.

5.  Rozbalte uzly a vyhledejte a vyberte třídu.

    > [!NOTE]
    > Pokud **zákazníka** třída není k dispozici, zavřete průvodce, sestavte projekt a spusťte průvodce znovu.

6.  Klikněte na tlačítko **Dokončit** vytvořit zdroj dat a přidat **zákazníka** třídu entity **zdroje dat** okna.

7.  Přetáhněte položky z **zdroje dat** okna do formuláře.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: Vytvoření třídy LINQ to SQL (Návrhář O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Metody DataContext (Návrhář relací objektů)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Objektový model LINQ to SQL](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Návod: Přidávání ověřování do tříd entit](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Postupy: Vytvoření přidružení (relace) mezi třídami LINQ to SQL (Návrhář relací objektů)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)