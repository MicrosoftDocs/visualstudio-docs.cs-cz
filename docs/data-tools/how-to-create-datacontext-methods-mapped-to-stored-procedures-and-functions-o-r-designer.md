---
title: Mapování metod DataContext na sprocs a funkce
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 21ea455e6cc29d17f9050e54dd2f8d11033320ac
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742902"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)

Uložené procedury a funkce můžete přidat do **návrháře o/R** jako <xref:System.Data.Linq.DataContext> metody. Volání metody a předání požadovaných parametrů spustí uloženou proceduru nebo funkci v databázi a vrátí data v návratovém typu <xref:System.Data.Linq.DataContext> metody. Podrobné informace o <xref:System.Data.Linq.DataContext> metodách naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Uložené procedury lze použít také k přepsání výchozího chování za [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] běhu, které provádí vložení, aktualizace a odstranění, když jsou změny uloženy z tříd entit do databáze. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Vytvoření metod DataContext

Metody můžete vytvořit <xref:System.Data.Linq.DataContext> přetažením uložených procedur nebo funkcí z <strong>Průzkumník serveru nebo * * Průzkumníka databáze</strong> do **návrháře o/R**.

> [!NOTE]
> Návratový typ vygenerované <xref:System.Data.Linq.DataContext> metody se liší v závislosti na tom, kde vyřadíte uloženou proceduru nebo funkci v **Návrháři o/R**. Vyřazení položek přímo na existující třídu entity vytvoří <xref:System.Data.Linq.DataContext> metodu s návratovým typem třídy entity. Vyřazení položek do prázdné oblasti **návrháře o/R** vytvoří <xref:System.Data.Linq.DataContext> metodu, která vrátí automaticky generovaný typ. Návratový typ metody lze změnit <xref:System.Data.Linq.DataContext> po jeho přidání do podokna **metody** . Chcete-li zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metody, vyberte ji a v okně **vlastnosti** Zkontrolujte vlastnost **návratový typ** . Další informace naleznete v tématu [Postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Vytvoření metod DataContext, které vracejí automaticky generované typy

1. V **Průzkumník serveru** nebo **Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze, se kterou pracujete.

2. Vyhledejte požadovanou uloženou proceduru a přetáhněte ji do prázdné oblasti **návrháře o/R**.

     <xref:System.Data.Linq.DataContext>Metoda je vytvořena s automaticky generovaným návratovým typem, který se zobrazí v podokně **metody** .

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Vytvoření metod DataContext, které mají návratový typ třídy entity

1. V **Průzkumník serveru** nebo **Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze, se kterou pracujete.

2. Vyhledejte požadovanou uloženou proceduru a přetáhněte ji do existující třídy entity v **Návrháři o/R**.

     <xref:System.Data.Linq.DataContext>Metoda je vytvořena s návratovým typem vybrané třídy entity a zobrazí se v podokně **metody** .

> [!NOTE]
> Informace o změně návratového typu existujících <xref:System.Data.Linq.DataContext> metod naleznete v tématu [How to: Change návratový typ metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Návod: vytváření tříd LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Technologie LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Představení technologie LINQ v jazyce Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ v jazyku C#](/dotnet/csharp/linq/linq-in-csharp)
