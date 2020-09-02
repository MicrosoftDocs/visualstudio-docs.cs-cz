---
title: Vytvoření parametrizovaných dotazů TableAdapter
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 560587e70365a485c3391a0623b959f88d417698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671058"
---
# <a name="create-parameterized-tableadapter-queries"></a>Vytvoření parametrizovaných dotazů TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Parametrizovaný dotaz vrátí data, která splňují podmínky klauzule WHERE v dotazu. Například můžete parametrizovat seznam zákazníků, aby zobrazoval pouze zákazníky v určitém městě přidáním `WHERE City = @City` na konec příkazu SQL, který vrátí seznam zákazníků.

V Návrhář datových sad vytvoříte parametrizované dotazy TableAdapter. Můžete je také vytvořit v aplikaci systému Windows pomocí příkazu **parametrizovat zdroj dat** v nabídce **data** . Příkaz **parametrizovat data source** vytvoří ovládací prvky ve formuláři, kde můžete zadat hodnoty parametrů a spustit dotaz.

> [!NOTE]
> Při sestavování parametrizovaného dotazu použijte zápis parametru, který je specifický pro databázi, se kterou píšete. Například přístup a zdroje dat OleDb používají otazník "?" k označení parametrů, takže klauzule WHERE by vypadala takto: `WHERE City = ?` .

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici, kterou používáte. Chcete-li změnit nastavení, přejděte do nabídky **nástroje** a vyberte **Nastavení importu a exportu**. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-parameterized-tableadapter-query"></a>Vytvoření parametrizovaného dotazu TableAdapter

- Vytvořte nový TableAdapter a přidejte do příkazu SQL klauzuli WHERE s požadovanými parametry. Další informace najdete v tématu [Vytvoření a konfigurace objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

     -nebo-

- Přidejte dotaz do existujícího TableAdapter a přidejte do příkazu SQL klauzuli WHERE s požadovanými parametry.

### <a name="create-a-parameterized-query-while-designing-a-data-bound-form"></a>Vytvoření parametrizovaného dotazu při návrhu formuláře vázaného na data

1. Vyberte ovládací prvek ve formuláři, který je již svázán s datovou sadou. Další informace najdete v tématu [vázání model Windows Forms ovládacích prvků na data v aplikaci Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. V nabídce **data** vyberte**Přidat dotaz**.

3. Dokončete dialogové okno **Tvůrce kritérií vyhledávání** a přidejte do příkazu SQL klauzuli WHERE s požadovanými parametry.

### <a name="add-a-query-to-an-existing-data-bound-form"></a>Přidat dotaz do existujícího formuláře vázaného na data

1. Otevřete formulář v **Návrhář formulářů**.

2. V nabídce **data** vyberte **Přidat dotaz** nebo **inteligentní značky dat**.

   > [!NOTE]
   > Pokud v nabídce **data** není k dispozici možnost **Přidat dotaz** , vyberte ovládací prvek ve formuláři, který zobrazuje zdroj dat, do kterého chcete přidat Parametrizace. Pokud například formulář zobrazuje data v <xref:System.Windows.Forms.DataGridView> ovládacím prvku, vyberte ho. Pokud formulář zobrazuje data v jednotlivých ovládacích prvcích, vyberte jakýkoli ovládací prvek vázaný na data.

3. V oblasti **Tabulka Vybrat zdroj dat** vyberte tablethat, do kterého chcete přidat Parametrizace.

4. Pokud vytváříte nový dotaz, zadejte název do pole **název nového dotazu** .

    -nebo-

    Vyberte dotaz v poli **název existujícího dotazu** .

5. Do **textového pole dotaz** zadejte dotaz, který přebírá parametry.

6. Vyberte **OK**.

    Ovládací prvek pro zadání parametru a tlačítko **Load** se přidá do formuláře v <xref:System.Windows.Forms.ToolStrip> ovládacím prvku.

   Pokud chcete zadat dotaz na záznamy, které nemají aktuální hodnotu, mohou být k parametrům TableAdapter přiřazeny hodnoty null. Zvažte například následující dotaz, který má `ShippedDate` parametr v `WHERE` klauzuli WHERE:

   ```sql
   SELECT CustomerID, OrderDate, ShippedDate
   FROM Orders
   WHERE (ShippedDate = @ShippedDate) OR
   (ShippedDate IS NULL)
   ```

Pokud se jednalo o dotaz na TableAdapter, mohli byste zadat dotaz na všechny objednávky, které nebyly odeslány pomocí následujícího kódu:

   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]

### <a name="enable-a-query-to-accept-null-values"></a>Povolení dotazu pro příjem hodnot null

1. V **Návrhář datových sad**vyberte dotaz TableAdapter, který musí přijmout hodnoty parametrů s hodnotou null.

2. V okně **vlastnosti** vyberte **parametry**. Potom stisknutím tlačítka se třemi tečkami (**...**) otevřete **Editor kolekce Parameters**.

3. Vyberte parametr, který povoluje hodnoty null, a nastavte vlastnost **AllowDBNull** na hodnotu `true` .

## <a name="see-also"></a>Viz také

- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)