---
title: 'Postupy: rozšíření kód vygenerovaný návrháře O-R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9da4dca31043104c58122c2eed7aa55ae44ef07e
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089786"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Postupy: rozšíření kód vygenerovaný Návrhář relací objektů
Kód vygenerovaný **Návrhář relací objektů** znovu vygeneruje při změně tříd entit a dalších objektů na plochu návrháře. Z důvodu této nové vygenerování kódu se kód, který přidáte do generovaný kód přepíše obvykle při návrháře znovu generuje kód. **Návrhář relací objektů** poskytuje možnost pro vygenerování souborů třídu, ve které můžete přidat kód, který není přepsán. Příkladem přidání vlastního kódu pro kód vygenerovaný **Návrhář relací objektů** je přidání ověření dat pro LINQ na třídy SQL (entita). Další informace najdete v tématu [postupy: přidávání ověření do tříd entit](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Přidejte kód pro třídu entity

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Vytvoření konkrétní třídu a přidejte kód pro třídu entity

1.  Otevřít nebo vytvořit nové technologie LINQ to SQL třídy souboru (**dbml** souboru) v **Návrhář relací objektů**. (Dvakrát klikněte **dbml** souboru v **Průzkumníku řešení** nebo **Průzkumník databáze**.)

2.  V **Návrhář relací objektů**, klikněte pravým tlačítkem na třídu, pro který chcete přidat ověřování a potom klikněte na **kód zobrazení**.

     Otevře se Editor kódu s konkrétní třídu pro třídu vybrané entity.

3.  Přidání kódu v deklaraci částečné třídy pro třídu entity.

## <a name="add-code-to-a-datacontext"></a>Přidání kódu do DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Vytvoření konkrétní třídu a přidejte do DataContext kód

1.  Otevřít nebo vytvořit nové technologie LINQ to SQL třídy souboru (**dbml** souboru) v **Návrhář relací objektů**. (Dvakrát klikněte **dbml** souboru v **Průzkumníku řešení** nebo **Průzkumník databáze**.)

2.  V **Návrhář relací objektů**, klikněte pravým tlačítkem myši na prázdnou oblast na návrháře a pak klikněte na tlačítko **kód zobrazení**.

     Editor kódu otevře s konkrétní třídu pro DataContext.

3.  Přidejte do deklarací částečné třídy DataContext vašeho kódu.

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: Vytvoření LINQ na SQL třídy (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)