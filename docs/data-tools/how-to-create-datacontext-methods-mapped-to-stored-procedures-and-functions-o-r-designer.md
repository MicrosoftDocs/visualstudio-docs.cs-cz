---
title: Mapování metod DataContext na sprocs a Functions (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4fa392467024a38dc447e6a5077f855d3464103b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648373"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Postupy: vytváření metod DataContext mapovaných na uložené procedury a funkce (Návrhář O/R)

Uložené procedury a funkce můžete přidat do **návrháře o/R** jako metody <xref:System.Data.Linq.DataContext>. Volání metody a předání požadovaných parametrů spustí uloženou proceduru nebo funkci v databázi a vrátí data v návratovém typu metody <xref:System.Data.Linq.DataContext>. Podrobné informace o metodách <xref:System.Data.Linq.DataContext> naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Uložené procedury lze použít také k přepsání výchozího [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] chování při spuštění, které provádí vložení, aktualizace a odstranění, když jsou změny uloženy z tříd entit do databáze. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Vytvoření metod DataContext

Metody <xref:System.Data.Linq.DataContext> můžete vytvořit přetažením uložených procedur nebo funkcí z <strong>Průzkumník serveru nebo * * Průzkumníka databáze</strong> do **Návrháře relací pro/R**.

> [!NOTE]
> Návratový typ vygenerované <xref:System.Data.Linq.DataContext> metody se liší v závislosti na tom, kde jste vyřadíte uloženou proceduru nebo funkci v **Návrháři o/R**. Vyřazení položek přímo na existující třídu entity vytvoří metodu <xref:System.Data.Linq.DataContext> s návratovým typem třídy entity. Vyřazení položek do prázdné oblasti **návrháře o/R** vytvoří metodu <xref:System.Data.Linq.DataContext>, která vrací automaticky generovaný typ. Návratový typ <xref:System.Data.Linq.DataContext> metody lze změnit po jeho přidání do podokna **metody** . Chcete-li zkontrolovat nebo změnit návratový typ metody <xref:System.Data.Linq.DataContext>, vyberte ji a v okně **vlastnosti** Zkontrolujte vlastnost **návratový typ** . Další informace naleznete v tématu [Postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Vytvoření metod DataContext, které vracejí automaticky generované typy

1. V **Průzkumník serveru** nebo **Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze, se kterou pracujete.

2. Vyhledejte požadovanou uloženou proceduru a přetáhněte ji do prázdné oblasti **návrháře o/R**.

     Metoda <xref:System.Data.Linq.DataContext> je vytvořena s automaticky generovaným návratovým typem, který se zobrazí v podokně **metody** .

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Vytvoření metod DataContext, které mají návratový typ třídy entity

1. V **Průzkumník serveru** nebo **Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze, se kterou pracujete.

2. Vyhledejte požadovanou uloženou proceduru a přetáhněte ji do existující třídy entity v **Návrháři o/R**.

     Metoda <xref:System.Data.Linq.DataContext> je vytvořena s návratovým typem vybrané třídy entity a zobrazí se v podokně **metody** .

> [!NOTE]
> Informace o změně návratového typu existujících metod <xref:System.Data.Linq.DataContext> naleznete v tématu [How to: Change a návratový typ metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Návod: vytváření tříd LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Úvod do jazyka LINQ v Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ v jazyce C#](/dotnet/csharp/linq/linq-in-csharp)
