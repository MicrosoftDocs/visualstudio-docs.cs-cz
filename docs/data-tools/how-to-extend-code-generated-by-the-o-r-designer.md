---
title: 'Postupy: rozšiřování kódu generovaného návrhářem O-R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e89410d224adf0980e51c691dbf581655cc2ff3e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648349"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Postupy: rozšiřování kódu generovaného návrhářem O/R
Kód generovaný **návrhářem O/R** se znovu vygeneruje při změnách tříd entit a dalších objektů na návrhové ploše. Z důvodu tohoto opětovného generování kódu je kód, který přidáte do generovaného kódu, obvykle přepsán, když Návrhář znovu vygeneruje kód. **Návrhář o/R** poskytuje možnost generovat soubory částečné třídy, ve kterých můžete přidat kód, který není přepsán. Jedním z příkladů Přidání vlastního kódu do kódu generovaného **návrhářem o/R** je přidání ověření dat do tříd LINQ to SQL (entita). Další informace najdete v tématu [Postup: Přidání ověřování do tříd entit](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Přidat kód do třídy entity

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Chcete-li vytvořit částečnou třídu a přidat kód do třídy entity

1. Otevřete nebo vytvořte nový soubor LINQ to SQLch tříd (soubor **. dbml** ) v **Návrháři o/R**. (Dvakrát klikněte na soubor **. dbml** v **Průzkumník řešení** nebo v **Průzkumníku databáze**.)

2. V **Návrháři o/R**klikněte pravým tlačítkem na třídu, pro kterou chcete přidat ověřování, a pak klikněte na **Zobrazit kód**.

     Otevře se Editor kódu s částečnou třídou pro vybranou třídu entity.

3. Přidejte svůj kód v deklaraci částečné třídy pro třídu entity.

## <a name="add-code-to-a-datacontext"></a>Přidání kódu do kontextu DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Chcete-li vytvořit částečnou třídu a přidat kód do kontextu DataContext

1. Otevřete nebo vytvořte nový soubor LINQ to SQLch tříd (soubor **. dbml** ) v **Návrháři o/R**. (Dvakrát klikněte na soubor **. dbml** v **Průzkumník řešení** nebo v **Průzkumníku databáze**.)

2. V **Návrháři o/R**klikněte pravým tlačítkem myši na prázdnou oblast návrháře a pak klikněte na **Zobrazit kód**.

     Editor kódu se otevře s částečnou třídou pro DataContext.

3. Přidejte svůj kód v deklaraci částečné třídy pro DataContext.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: vytváření tříd LINQ to SQL (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)