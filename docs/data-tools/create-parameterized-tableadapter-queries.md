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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0926558c4d6e94032e2af2c75189f287da8d4811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642151"
---
# <a name="create-parameterized-tableadapter-queries"></a>Vytvoření parametrizovaných dotazů TableAdapter

Parametrizovaný dotaz vrátí data, která splňují podmínky klauzule WHERE v dotazu. Například můžete parametrizovat seznam zákazníků, aby zobrazoval pouze zákazníky v určitém městu přidáním `WHERE City = @City` na konec příkazu SQL, který vrátí seznam zákazníků.

V **Návrhář datových sad**vytvoříte parametrizované dotazy TableAdapter. Můžete je také vytvořit v aplikaci systému Windows pomocí příkazu **parametrizovat zdroj dat** v nabídce **data** . Příkaz **parametrizovat data source** vytvoří ovládací prvky ve formuláři, kde můžete zadat hodnoty parametrů a spustit dotaz.

> [!NOTE]
> Při sestavování parametrizovaného dotazu použijte zápis parametru, který je specifický pro databázi, se kterou píšete. Například přístup a zdroje dat OleDb používají otazník "?" k označení parametrů, takže klauzule WHERE by vypadala takto: `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Vytvoření parametrizovaného dotazu TableAdapter

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Vytvoření parametrizovaného dotazu v Návrhář datových sad

- Vytvořte nový TableAdapter a přidejte do příkazu SQL klauzuli WHERE s požadovanými parametry. Další informace najdete v tématu [Vytvoření a konfigurace objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

     -nebo-

- Přidejte dotaz do existujícího TableAdapter a přidejte do příkazu SQL klauzuli WHERE s požadovanými parametry.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Vytvoření parametrizovaného dotazu při návrhu formuláře vázaného na data

1. Vyberte ovládací prvek ve formuláři, který je již svázán s datovou sadou. Další informace najdete v tématu [vázání model Windows Forms ovládacích prvků na data v aplikaci Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. V nabídce **data** vyberte **Přidat dotaz**.

3. Dokončete dialogové okno **Tvůrce kritérií vyhledávání** a přidejte do příkazu SQL klauzuli WHERE s požadovanými parametry.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Přidání dotazu do existujícího formuláře vázaného na data

1. Otevřete formulář v **Návrhář formulářů**.

2. V nabídce **data** vyberte **Přidat dotaz** nebo **inteligentní značky dat**.

    > [!NOTE]
    > Pokud v nabídce **data** není k dispozici možnost **Přidat dotaz** , vyberte ovládací prvek ve formuláři, který zobrazuje zdroj dat, do kterého chcete přidat Parametrizace. Pokud například formulář zobrazuje data v ovládacím prvku <xref:System.Windows.Forms.DataGridView>, vyberte ho. Pokud formulář zobrazuje data v jednotlivých ovládacích prvcích, vyberte jakýkoli ovládací prvek vázaný na data.

3. V oblasti **Tabulka Vybrat zdroj dat** vyberte tabulku, do které chcete přidat Parametrizace.

4. Pokud vytváříte nový dotaz, zadejte název do pole **název nového dotazu** .

     -nebo-

     Vyberte dotaz v poli **název existujícího dotazu** .

5. Do **textového pole dotaz** zadejte dotaz, který přebírá parametry.

6. Vyberte **OK**.

     Ovládací prvek pro vstup do tohoto parametru a tlačítko **Load** se přidá do formuláře v ovládacím prvku <xref:System.Windows.Forms.ToolStrip>.

### <a name="query-for-null-values"></a>Dotaz na hodnoty null

Pokud chcete zadat dotaz na záznamy, které nemají aktuální hodnotu, mohou být k parametrům TableAdapter přiřazeny hodnoty null. Zvažte například následující dotaz, který má parametr `ShippedDate` v klauzuli `WHERE`:

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Pokud se jednalo o dotaz na TableAdapter, mohli byste zadat dotaz na všechny objednávky, které nebyly odeslány pomocí následujícího kódu:

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Povolení dotazu pro příjem hodnot null:

1. V **Návrhář datových sad**vyberte dotaz TableAdapter, který musí přijmout hodnoty parametrů s hodnotou null.

2. V okně **vlastnosti** vyberte možnost **parametry**a potom klikněte na tlačítko se třemi tečkami ( **...** ) a otevřete tak **Editor kolekce Parameters**.

3. Vyberte parametr, který povoluje hodnoty null, a nastavte vlastnost **AllowDBNull** na hodnotu `true`.

## <a name="see-also"></a>Viz také:

- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)