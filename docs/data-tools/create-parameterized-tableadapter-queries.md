---
title: Vytvoření parametrizovaných dotazů TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9d344fdd444a46b3e0434e70850946ef242864b0
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388475"
---
# <a name="create-parameterized-tableadapter-queries"></a>Vytvoření parametrizovaných dotazů TableAdapter

Parametrický dotaz vrací data, která splňuje podmínky klauzuli WHERE v dotazu. Například můžete parametrizovat seznam zákazníků na Zobrazit pouze zákazníkům v určitých město přidáním `WHERE City = @City` na konec příkazu SQL, který vrátí seznam zákazníků.

Vytvoření parametrizovaných dotazů TableAdapter v **Návrhář Dataset**. Můžete také vytvořit v aplikaci Windows se **parametrizovat zdroj dat** příkaz **Data** nabídky. **Parametrizovat zdroj dat** příkaz vytvoří ovládací prvky na formuláři kde vstupní hodnoty parametrů a spusťte dotaz.

> [!NOTE]
> Při vytváření parametrický dotaz, použijte parametr zápis, která je specifická pro databáze, kterou můžete kódovat. Přístup a OleDb zdroje dat použít například otazník "?" k označení parametrů, takže v klauzuli WHERE bude vypadat takto: `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Vytvoření parametrického dotazu TableAdapter

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Vytvoření parametrického dotazu v návrháři datových sad

-   Vytvoření nového TableAdapter, přidáte klauzuli WHERE se požadované parametry do příkazu SQL. Další informace najdete v tématu [vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md).

     -nebo-

-   Přidáte dotaz na existující TableAdapter, přidáte klauzuli WHERE se požadované parametry do příkazu SQL.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Chcete-li vytvořit parametrický dotaz při návrhu formuláře vázané na data

1.  Vyberte ovládací prvek na formuláři, který je již vázán na datovou sadu. Další informace najdete v tématu [ovládací prvky vazby Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  Na **Data** nabídce vyberte možnost **přidat dotaz**.

3.  Dokončení **Tvůrce kritérií vyhledávání** dialogovém okně Přidání klauzuli WHERE se požadované parametry pro příkaz jazyka SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Chcete-li přidat dotaz do existujícího formuláře vázané na data

1.  Otevřete formulář v nástrojích pro **Návrháře formulářů Windows**.

2.  Na **Data** nabídce vyberte možnost **přidat dotaz** nebo **inteligentní značky dat**.

    > [!NOTE]
    > Pokud **přidat dotaz** není k dispozici na **Data** nabídku, vyberte ovládací prvek na formuláři, zobrazí zdroj dat, které chcete přidat Parametrizace do. Například, pokud data ve formuláři se zobrazí <xref:System.Windows.Forms.DataGridView> ovládací prvek, vyberte ji. Pokud formulář pro zobrazení dat v jednotlivých ovládacích prvků, vyberte libovolný ovládací prvek vázaný na data.

3.  V **tabulky zdroje dat vyberte** oblasti, vyberte tabulku, do které chcete přidat parametrizace.

4.  Zadejte název **nový název dotazu** pole, pokud vytváříte nový dotaz.

     -nebo-

     Vybrat dotaz v **existující název dotazu** pole.

5.  V **Text dotazu** zadejte dotaz, který používá parametry.

6.  Vyberte **OK**.

     Ovládací prvek pro vstupní parametr a s **zatížení** tlačítko se přidá na formulář v nástrojích <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.

### <a name="query-for-null-values"></a>Dotaz na hodnoty null

Parametry třídy TableAdapter lze přiřadit hodnoty null, pokud chcete zadat dotaz pro záznamy, které nemají žádnou aktuální hodnotu. Zvažte například následující dotaz, který má `ShippedDate` parametr v jeho `WHERE` klauzule:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Pokud tento dotaz na objektu typu TableAdapter, můžete dotazovat na pro všechny objednávky, které nebyly dodány s následujícím kódem:

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Pokud chcete povolit dotaz tak, aby přijímal hodnoty null:

1.  V **Návrhář Dataset**, vyberte dotaz TableAdapter, které je potřeba přijmout hodnoty null parametrů.

2.  V **vlastnosti** okně **parametry**, pak klikněte na tlačítko se třemi tečkami (**...** ) tlačítko Otevřít **Editor kolekce parametrů**.

3.  Vyberte parametr, který povoluje hodnoty null a nastavte **AllowDbNull** vlastnost `true`.

## <a name="see-also"></a>Viz také:

- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)