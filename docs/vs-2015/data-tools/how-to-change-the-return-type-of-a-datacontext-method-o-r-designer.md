---
title: 'Postupy: Změna návratového typu metody DataContext (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 351a2f53d8ad8c5f29821d905c292cd988390869
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658843"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Postupy: Změna návratového typu metody DataContext (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návratový typ metody <xref:System.Data.Linq.DataContext> (vytvořený na základě uložené procedury nebo funkce) se liší v závislosti na tom, kam jste vyřadíte uloženou proceduru nebo funkci v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Pokud přetáhnete položku přímo na existující třídu entity, vytvoří se <xref:System.Data.Linq.DataContext> metoda, která má návratový typ třídy entity (Pokud schéma dat vrácených uloženou procedurou nebo funkcí odpovídá tvaru třídy entity). Pokud položku vyřadíte do prázdné oblasti [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], vytvoří se <xref:System.Data.Linq.DataContext> metoda, která vrací automaticky generovaný typ. Můžete změnit návratový typ metody <xref:System.Data.Linq.DataContext> poté, co ji přidáte do podokna metody. Chcete-li zkontrolovat nebo změnit návratový typ metody <xref:System.Data.Linq.DataContext>, vyberte ji a klikněte na vlastnost **návratový typ** v okně **vlastnosti** .

> [!NOTE]
> Nemůžete vrátit <xref:System.Data.Linq.DataContext> metody, které mají návratový typ nastaven na třídu entity pro vrácení automaticky generovaného typu pomocí okna **vlastnosti** . Chcete-li vrátit metodu <xref:System.Data.Linq.DataContext> pro vrácení automaticky generovaného typu, je nutné znovu přetáhnout původní databázový objekt do návrháře O/R.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Změna návratového typu metody DataContext z automaticky generovaného typu na třídu entity

1. V podokně metody vyberte metodu <xref:System.Data.Linq.DataContext>.

2. V okně **vlastnosti** vyberte **návratový typ** a pak vyberte dostupnou třídu entity v seznamu **návratový typ** . Pokud požadovaná Třída entity není v seznamu, přidejte ji do nebo ji vytvořte v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a přidejte ji do seznamu.

3. Uložte soubor. dbml.

### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Změna návratového typu metody DataContext z třídy entity zpět na automaticky generovaný typ

1. V podokně metody vyberte metodu <xref:System.Data.Linq.DataContext> a odstraňte ji.

2. Přetáhněte databázový objekt z **Průzkumník serveru** /**Průzkumníku databáze** do prázdné oblasti návrháře o/R.

3. Uložte soubor. dbml.

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [metody DataContext (o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [Postupy: vytváření metod DataContext mapovaných na uložené procedury a funkce (Návrhář o/r)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
