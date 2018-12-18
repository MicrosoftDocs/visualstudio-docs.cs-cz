---
title: 'Postupy: Změna návratový typ metody DataContext (Návrhář O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089354"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Postupy: Změna návratový typ metody DataContext (Návrhář relací objektů)
Návratový typ <xref:System.Data.Linq.DataContext> (vytvořili podle uložená procedura nebo funkce) se liší v závislosti na tom, kde vyřadit uložená procedura nebo funkce v **Návrhář relací objektů**. Pokud je vyřadit položku přímo do existující třídy entity, <xref:System.Data.Linq.DataContext> metodu, která má návratový typ třídy entita se vytvoří (Pokud je schéma dat vrácených uložená procedura nebo funkce odpovídá tvaru třídy entity). Pokud je položka vyřadit na prázdnou oblast **Návrhář relací objektů**, <xref:System.Data.Linq.DataContext> metoda, která vrátí typ automaticky generované se vytvoří. Můžete změnit návratový typ <xref:System.Data.Linq.DataContext> metoda po přidání do podokna metody. Zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metoda, vyberte ho a klikněte na tlačítko **návratového typu** vlastnost **vlastnosti** okno.

> [!NOTE]
>  Nelze vrátit <xref:System.Data.Linq.DataContext> metody, které mají návratový typ. nastaveny pro třídu entity, aby návratový typ automaticky vygenerované pomocí **vlastnosti** okno. Vrátit zpátky <xref:System.Data.Linq.DataContext> metoda vrátí typ automaticky generovaný musí přetáhněte původní objekt databáze do **Návrhář relací objektů** znovu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Chcete-li změnit návratový typ metody DataContext z typu automaticky vygenerované třídy entity

1.  Vyberte <xref:System.Data.Linq.DataContext> metoda v podokně metody.

2.  Vyberte **návratového typu** v **vlastnosti** okna a potom vyberte dostupné entity třídy v **návratového typu** seznamu. Pokud třídy požadované entita není v seznamu, přidejte ho do nebo vytvořte ho **Návrhář relací objektů** ho přidejte do seznamu.

3.  Uložit *dbml* souboru.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Chcete-li změnit návratový typ metody DataContext z třídy entity zpět na automaticky generovaný typ

1.  Vyberte <xref:System.Data.Linq.DataContext> metoda v **metody** podokně a jej odstraňte.

2.  Přetáhněte objekt databáze z **Průzkumníka serveru** nebo **Průzkumník databáze** na prázdnou oblast **Návrhář relací objektů**.

3.  Uložit *dbml* souboru.

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (Návrhář relací objektů)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: vytvoření metody DataContext namapované na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)