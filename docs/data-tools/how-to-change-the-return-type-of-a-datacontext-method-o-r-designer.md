---
title: Změna návratového typu metody DataContext (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 304cd62e83ae2e256e40cdbb8f046b637cbd8d58
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648384"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Postupy: Změna návratového typu metody DataContext (O/R Designer)
Návratový typ metody <xref:System.Data.Linq.DataContext> (vytvořený na základě uložené procedury nebo funkce) se liší v závislosti na tom, kde jste vyřadíte uloženou proceduru nebo funkci v **Návrháři o/R**. Pokud přetáhnete položku přímo na existující třídu entity, vytvoří se <xref:System.Data.Linq.DataContext> metoda, která má návratový typ třídy entity (Pokud schéma dat vrácených uloženou procedurou nebo funkcí odpovídá tvaru třídy entity). Pokud přetáhnete položku do prázdné oblasti **návrháře o/R**, vytvoří se <xref:System.Data.Linq.DataContext> metoda, která vrací automaticky generovaný typ. Můžete změnit návratový typ metody <xref:System.Data.Linq.DataContext> poté, co ji přidáte do podokna metody. Chcete-li zkontrolovat nebo změnit návratový typ metody <xref:System.Data.Linq.DataContext>, vyberte ji a klikněte na vlastnost **návratový typ** v okně **vlastnosti** .

> [!NOTE]
> Nemůžete vrátit <xref:System.Data.Linq.DataContext> metody, které mají návratový typ nastaven na třídu entity pro vrácení automaticky generovaného typu pomocí okna **vlastnosti** . Chcete-li vrátit metodu <xref:System.Data.Linq.DataContext> pro vrácení automaticky generovaného typu, je nutné znovu přetáhnout původní databázový objekt do **návrháře o/R** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Změna návratového typu metody DataContext z automaticky generovaného typu na třídu entity

1. V podokně metody vyberte metodu <xref:System.Data.Linq.DataContext>.

2. V okně **vlastnosti** vyberte **návratový typ** a pak vyberte dostupnou třídu entity v seznamu **návratový typ** . Pokud požadovaná Třída entity není v seznamu, přidejte ji do nebo ji vytvořte v **Návrháři o/R** a přidejte ji do seznamu.

3. Uložte soubor *. dbml* .

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Změna návratového typu metody DataContext z třídy entity zpět na automaticky generovaný typ

1. V podokně **metody** vyberte metodu <xref:System.Data.Linq.DataContext> a odstraňte ji.

2. Přetáhněte databázový objekt z **Průzkumník serveru** nebo **Průzkumníka databáze** do prázdné oblasti **návrháře o/R**.

3. Uložte soubor *. dbml* .

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)