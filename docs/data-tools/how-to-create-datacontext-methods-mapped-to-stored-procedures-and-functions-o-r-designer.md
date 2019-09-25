---
title: Mapování metod DataContext na sprocs a Functions (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4c3769634bfbeb98fcc31e5c074177d950248292
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252910"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)

Uložené procedury a funkce můžete přidat do **návrháře o/R** jako <xref:System.Data.Linq.DataContext> metody. Volání metody a předání požadovaných parametrů spustí uloženou proceduru nebo funkci v databázi a vrátí data v návratovém typu <xref:System.Data.Linq.DataContext> metody. Podrobné informace o <xref:System.Data.Linq.DataContext> metodách naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Uložené procedury lze použít také k přepsání výchozího [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] chování za běhu, které provádí vložení, aktualizace a odstranění, když jsou změny uloženy z tříd entit do databáze. Další informace najdete v tématu [jak: Přiřaďte uložené procedury pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Vytvoření metod DataContext

Metody můžete vytvořit <xref:System.Data.Linq.DataContext> přetažením uložených procedur nebo funkcí z <strong>Průzkumník serveru nebo * * Průzkumníka databáze</strong> do **návrháře o/R**.

> [!NOTE]
> Návratový typ vygenerované <xref:System.Data.Linq.DataContext> metody se liší v závislosti na tom, kde vyřadíte uloženou proceduru nebo funkci v **Návrháři o/R**. Vyřazení položek přímo na existující třídu entity vytvoří <xref:System.Data.Linq.DataContext> metodu s návratovým typem třídy entity. Vyřazení položek do prázdné oblasti **návrháře o/R** vytvoří <xref:System.Data.Linq.DataContext> metodu, která vrátí automaticky generovaný typ. Návratový typ <xref:System.Data.Linq.DataContext> metody lze změnit po jeho přidání do podokna **metody** . Chcete-li zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metody, vyberte ji a v okně **vlastnosti** Zkontrolujte vlastnost **návratový typ** . Další informace najdete v tématu [jak: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Vytvoření metod DataContext, které vracejí automaticky generované typy

1. V **Průzkumník serveru** nebo **Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze, se kterou pracujete.

2. Vyhledejte požadovanou uloženou proceduru a přetáhněte ji do prázdné oblasti **návrháře o/R**.

     Metoda je vytvořena s automaticky generovaným návratovým typem, který se zobrazí v podokně **metody.** <xref:System.Data.Linq.DataContext>

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Vytvoření metod DataContext, které mají návratový typ třídy entity

1. V **Průzkumník serveru** nebo **Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze, se kterou pracujete.

2. Vyhledejte požadovanou uloženou proceduru a přetáhněte ji do existující třídy entity v **Návrháři o/R**.

     Metoda je vytvořena s návratovým typem vybrané třídy entity a zobrazí se v podokně metody. <xref:System.Data.Linq.DataContext>

> [!NOTE]
> Informace o změně návratového typu existujících <xref:System.Data.Linq.DataContext> metod naleznete v tématu [How to: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Návod: Vytváření tříd LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Úvod do jazyka LINQ v Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ v jazyce C#](/dotnet/csharp/linq/linq-in-csharp)
