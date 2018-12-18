---
title: 'Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8ae5fb4b3785bde0e092f68b62a9b030069a52aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942696"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (O/R Designer)

Můžete přidat uložené procedury a funkce **O/R Designer** jako <xref:System.Data.Linq.DataContext> metody. Volání metody a předáním požadovaných parametrů v databázi Spustí uloženou proceduru nebo funkci a vrací data v návratovém typu <xref:System.Data.Linq.DataContext> metody. Podrobné informace o <xref:System.Data.Linq.DataContext> metody, naleznete v tématu [metod DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Uložené procedury můžete použít také výchozí hodnotu přepsat [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] chování za běhu, který provádí vložení, aktualizace a odstranění při uložení změn z tříd entit k databázi. Další informace najdete v tématu [postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Vytvoření metod DataContext

Můžete vytvořit <xref:System.Data.Linq.DataContext> metody přetažením uložené procedury nebo funkce z <strong>Průzkumníku serveru nebo ** Průzkumník databáze</strong> na **O/R Designer**.

> [!NOTE]
> Návratový typ vytvořeného <xref:System.Data.Linq.DataContext> metoda se liší v závislosti na tom, kde vyřaďte uloženou proceduru nebo funkci na **O/R Designer**. Přetažení položek přímo do existující entity třídy vytvoří <xref:System.Data.Linq.DataContext> metoda s návratovým typem třídy entity. Přetažení položek na prázdnou oblast **O/R Designer** vytvoří <xref:System.Data.Linq.DataContext> metodu, která vrací automaticky generovanému typu. Můžete změnit návratový typ <xref:System.Data.Linq.DataContext> metoda po jejím přidáním na **metody** podokně. Zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metoda, vyberte ho a zkontrolujte **návratový typ** vlastnost **vlastnosti** okna. Další informace najdete v tématu [postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Chcete-li vytvořit DataContext metody, které vracejí automaticky vygenerovaných typů

1.  V **Průzkumníka serveru** nebo **Průzkumník databáze**, rozbalte **uložené procedury** uzel databáze, se kterým pracujete.

2.  Vyhledejte požadovanou uložené procedury a přetáhněte ji na prázdnou oblast **O/R Designer**.

     <xref:System.Data.Linq.DataContext> Metoda se vytvoří s automaticky generovanou návratový typ a zobrazí se v **metody** podokně.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Vytvoření metod DataContext, které mají návratový typ třídy entity

1.  V **Průzkumníka serveru** nebo **Průzkumník databáze**, rozbalte **uložené procedury** uzel databáze, se kterým pracujete.

2.  Vyhledejte požadovanou uložené procedury a přetáhněte ji na existující třídu entity v **O/R Designer**.

     <xref:System.Data.Linq.DataContext> Metoda s návratovým typem třídy vybranou entitu a je zahrnut v **metody** podokně.

> [!NOTE]
> Informace o změnu návratového typu stávajících <xref:System.Data.Linq.DataContext> metody, naleznete v tématu [postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Návod: Vytvoření LINQ na třídy SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Úvod do LINQ v JAZYKU Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ v jazyce C#](/dotnet/csharp/linq/linq-in-csharp)