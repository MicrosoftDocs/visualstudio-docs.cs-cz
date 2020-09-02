---
title: 'Postupy: vytváření metod DataContext mapovaných na uložené procedury a funkce (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665981"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uložené procedury a funkce lze přidat do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> metody as. Volání metody a předání požadovaných parametrů spustí uloženou proceduru nebo funkci v databázi a vrátí data v návratovém typu <xref:System.Data.Linq.DataContext> metody. Podrobné informace o <xref:System.Data.Linq.DataContext> metodách naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Uložené procedury lze také použít k přepsání výchozího [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] chování modulu runtime, které provádí vložení, aktualizace a odstranění, když jsou změny uloženy z tříd entit do databáze. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>Vytváření metod DataContext
 Metody můžete vytvořit <xref:System.Data.Linq.DataContext> přetažením uložených procedur nebo funkcí z **Průzkumníka Průzkumník serveru/databáze** do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

> [!NOTE]
> Návratový typ vygenerované <xref:System.Data.Linq.DataContext> metody se liší v závislosti na tom, kam jste vyřadíte uloženou proceduru nebo funkci na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Vyřazení položek přímo na existující třídu entity vytvoří <xref:System.Data.Linq.DataContext> metodu s návratovým typem třídy entity. Vyřazení položek do prázdné oblasti objektu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] vytvoří <xref:System.Data.Linq.DataContext> metodu, která vrátí automaticky generovaný typ. Návratový typ metody lze změnit <xref:System.Data.Linq.DataContext> po jeho přidání do podokna metody. Chcete-li zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metody, vyberte ji a v okně **vlastnosti** Zkontrolujte vlastnost **návratový typ** . Další informace naleznete v tématu [Postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Vytvoření metod DataContext, které vracejí automaticky generované typy

1. V **Průzkumník serveru** / **Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze, se kterou pracujete.

2. Vyhledejte požadovanou uloženou proceduru a přetáhněte ji do prázdné oblasti [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

     <xref:System.Data.Linq.DataContext>Metoda je vytvořena s automaticky generovaným návratovým typem, který se zobrazí v podokně **metody** .

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Vytvoření metod DataContext, které mají návratový typ třídy entity

1. V **Průzkumník serveru** / **Průzkumníku databáze**rozbalte uzel **uložené procedury** databáze, se kterou pracujete.

2. Vyhledejte požadovanou uloženou proceduru a přetáhněte ji do existující třídy entity v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

     <xref:System.Data.Linq.DataContext>Metoda je vytvořena s návratovým typem vybrané třídy entity a zobrazí se v podokně **metody** .

> [!NOTE]
> Informace o změně návratového typu existujících <xref:System.Data.Linq.DataContext> metod naleznete v tématu [How to: Change návratový typ metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [metodách DataContext pro Visual Studio (o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [: vytváření LINQ to SQLch tříd (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Úvod do LINQ v Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [Postupy: zápis dotazů LINQ v jazyce C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
