---
title: Vytvoření parametrizovaných dotazů TableAdapter | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56e14d66275bd961829fc09e06f7d5e99dbcc2c4
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218896"
---
# <a name="create-parameterized-tableadapter-queries"></a>Vytvoření parametrizovaných dotazů TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Parametrický dotaz vrací data, která splňuje podmínky klauzuli WHERE v dotazu. Například můžete parametrizovat seznam zákazníků na Zobrazit pouze zákazníkům v určitých město přidáním `WHERE City = @City` na konec příkazu SQL, který vrátí seznam zákazníků.  
  
 Vytvoření parametrizovaných dotazů TableAdapter v [Návrhář Dataset](../data-tools/creating-and-editing-typed-datasets.md). Můžete také vytvořit v aplikaci Windows se **parametrizovat zdroj dat** příkaz **Data** nabídky. **Parametrizovat zdroj dat** příkaz vytvoří ovládací prvky na formuláři kde vstupní hodnoty parametrů a spusťte dotaz.  
  
> [!NOTE]
>  Při vytváření parametrický dotaz, použijte parametr zápis, která je specifická pro databáze, kterou můžete kódovat. Přístup a OleDb zdroje dat použít například otazník "?" k označení parametrů, takže v klauzuli WHERE bude vypadat takto: `WHERE City = ?`.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici, kterou používáte. Chcete-li změnit nastavení, přejděte **nástroje** nabídky a vybereme **nastavení importu a exportu**. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-parameterized-tableadapter-query"></a>Vytvoření parametrického dotazu TableAdapter  
  
#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Vytvoření parametrického dotazu v návrháři datových sad  
  
-   Vytvoření nového TableAdapter, přidáte klauzuli WHERE se požadované parametry do příkazu SQL. Další informace najdete v tématu [vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
     -nebo-  
  
-   Přidáte dotaz na existující TableAdapter, přidáte klauzuli WHERE se požadované parametry do příkazu SQL. Další informace najdete v tématu [postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Chcete-li vytvořit parametrický dotaz při návrhu formuláře vázané na data  
  
1.  Vyberte ovládací prvek na formuláři, který je již vázán na datovou sadu. Další informace najdete v tématu [ovládací prvky vazby Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  Na **Data** nabídce vyberte možnost**přidat dotaz**.  
  
3.  Dokončení **Tvůrce kritérií vyhledávání** dialogovém okně Přidání klauzuli WHERE se požadované parametry pro příkaz jazyka SQL.  
  
### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Chcete-li přidat dotaz do existujícího formuláře vázané na data  
  
1. Otevřete formulář v nástrojích pro **Návrháře formulářů Windows**.  
  
2. Na **Data** nabídce vyberte možnost **přidat dotaz** nebo **inteligentní značky dat**.  
  
   > [!NOTE]
   > Pokud **přidat dotaz** není k dispozici na **Data** nabídku, vyberte ovládací prvek na formuláři, zobrazí zdroj dat, které chcete přidat Parametrizace do. Například, pokud data ve formuláři se zobrazí <xref:System.Windows.Forms.DataGridView> ovládací prvek, vyberte ji. Pokud formulář pro zobrazení dat v jednotlivých ovládacích prvků, vyberte libovolný ovládací prvek vázaný na data.  
  
3. V **tabulky zdroje dat vyberte** oblasti, vyberte tablethat, kterou chcete přidat Parametrizace do.  
  
4. Zadejte název **nový název dotazu** pole, pokud vytváříte nový dotaz.  
  
    -nebo-  
  
    Vybrat dotaz v **existující název dotazu** pole.  
  
5. V **Text dotazu** zadejte dotaz, který používá parametry.  
  
6. Vyberte **OK**.  
  
    Ovládací prvek pro vstupní parametr a s **zatížení** tlačítko se přidá na formulář v nástrojích <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.  
  
   Parametry třídy TableAdapter lze přiřadit hodnoty null, pokud chcete zadat dotaz pro záznamy, které nemají žádnou aktuální hodnotu. Zvažte například následující dotaz, který má `ShippedDate` parametr v jeho `WHERE` klauzule:  
  
   `SELECT CustomerID, OrderDate, ShippedDate`  
  
   `FROM Orders`  
  
   `WHERE (ShippedDate = @ShippedDate) OR`  
  
   `(ShippedDate IS NULL)`  
  
   Pokud tento dotaz na objektu typu TableAdapter, můžete dotazovat na pro všechny objednávky, které nebyly dodány s následujícím kódem:  
  
   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]  
  
#### <a name="to-enable-a-query-to-accept-null-values"></a>Chcete-li povolit dotaz tak, aby přijímal hodnoty null  
  
1.  V **Návrhář Dataset**, vyberte dotaz TableAdapter, které je potřeba přijmout hodnoty null parametrů.  
  
2.  V **vlastnosti** okně **parametry**. Stiskněte klávesu se třemi tečkami (**...** ) tlačítko Otevřít **Editor kolekce parametrů**.  
  
3.  Vyberte parametr, který povoluje hodnoty null a nastavte **AllowDbNull** vlastnost `true`.  
  
## <a name="see-also"></a>Viz také  
 [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

