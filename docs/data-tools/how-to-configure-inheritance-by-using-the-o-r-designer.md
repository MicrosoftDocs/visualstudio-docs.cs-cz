---
title: 'Postupy: konfigurace pomocí návrháře O R dědičnosti'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bb0be89627f5e7e95d7d45ebfb938bca3e4a982b
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089261"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Postupy: Konfigurace dědičnosti pomocí Návrhář relací objektů
**Návrhář relací objektů** (**Návrhář relací objektů**) podporuje koncept dědění jedné tabulky, jak často jsou implementované v relačním systémech. V jedné tabulce dědičnosti je jedné databáze tabulku, která obsahuje pole pro informace nadřazené a podřízené informace. Pomocí relačních dat sloupce diskriminátoru obsahuje hodnotu, která určuje, které třídy žádné záznam patří.

Představte si třeba `Persons` tabulku, která obsahuje všechny zaměstnaní společnosti. Někteří uživatelé mají zaměstnanci a někteří uživatelé mají správci. `Persons` Tabulka obsahuje sloupec s názvem `EmployeeType` s hodnotou 1 pro správce a hodnota 2 pro zaměstnance; Toto je sloupce diskriminátoru. V tomto scénáři můžete vytvořit podtřídou třídy zaměstnanci a naplnit třída se pouze záznamy, které mají `EmployeeType` hodnota 2. Rovněž můžete odebrat sloupce, které se nevztahují z každé ze třídy.

Vytváření objektový model, který používá dědičnosti (a odpovídá na relační data) může být poněkud matoucí. Následující postup popisuje kroky potřebné pro konfiguraci dědičnosti s **Návrhář relací objektů**. Následující obecné kroky bez odkazující na existující tabulky a sloupce může být obtížné, takže poskytuje návod, který používá data. Pro podrobné podrobné pokyny pro konfiguraci dědičnosti, pomocí **Návrhář relací objektů**, najdete v části [návod: vytváření technologie LINQ to SQL třídy pomocí jedné tabulky dědičnosti (Návrhář relací objektů)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>K vytvoření zděděné datových tříd

1.  Otevřete **Návrhář relací objektů** přidáním **třídy LINQ to SQL** položky do existujícího projektu Visual Basic a C#.

2.  Přetáhněte tabulku, kterou chcete použít jako základní třída na **Návrhář relací objektů**.

3.  Přetáhněte druhé kopie v tabulce na **Návrhář relací objektů** a přejmenujte ji. Je to odvozené třídy nebo podtřídy.

4.  Klikněte na tlačítko **dědičnosti** v **Návrhář relací objektů** kartě **sada nástrojů**a pak klikněte na tlačítko podtřídy (tabulky, můžete přejmenovat) a připojte ho k základní třídy.

    > [!NOTE]
    >  Klikněte **dědičnosti** položky v **sada nástrojů** a uvolnění tlačítka myši, klikněte na druhé kopie třídy, které jste vytvořili v kroku 3 a pak klikněte na první třídy, které jste vytvořili v kroku 2. Šipka na řádku dědičnosti odkazuje na první třídy.

5.  V každé třídě odstraňte všechny vlastnosti objektu, které nechcete zobrazit a které nejsou používány k přidružení. Obdržíte chybu, pokud se pokusíte odstranit vlastnosti objektu se používá pro přidružení: [vlastnost \<název vlastnosti > nelze odstranit, protože se účastní přidružení \<název přidružení >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    >  Protože odvozené třídy dědí vlastnosti definované ve své základní třídy, nemůže být stejné sloupce definovaný ve každá třída. (Sloupce jsou implementované jako vlastnosti). Vytváření sloupců v odvozené třídě můžete povolit tak modifikátor dědičnosti na vlastnost v základní třídě. Další informace najdete v tématu [základní informace o dědičnosti (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6.  Vyberte řádek dědičnosti ve **Návrhář relací objektů**.

7.  V **vlastnosti** nastavte **diskriminátoru vlastnost** na název sloupce, který slouží k rozlišení záznamy v tříd.

8.  Nastavte **odvozené třídy diskriminátoru hodnota** vlastnost na hodnotu v databázi, která označí jako zděděné typu záznamu. (Toto je hodnota, který je uložen ve sloupci diskriminátoru a slouží k určení zděděné třídy.)

9. Nastavte **hodnota diskriminátoru základní třídy** vlastnost na hodnotu, která označí jako základní typ záznamu. (To je hodnota, která je uložená ve sloupci diskriminátoru a slouží k určení základní třídy.)

10. Volitelně můžete také nastavit **dědičnosti výchozí** vlastnosti k určení typu v hierarchii dědičnosti, která se používá při načítání řádků, které neodpovídají žádné definované dědičnosti kódu. Jinými slovy, pokud má záznam hodnotu v jeho sloupce diskriminátoru který neodpovídá hodnotě buď **odvozené třídy diskriminátoru hodnotu** nebo **hodnota diskriminátoru základní třídy** vlastnosti, záznamu načte do typ určený jako **dědičnosti výchozí**.

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: Vytvoření LINQ na SQL třídy (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Návod: Vytvoření LINQ na třídy SQL pomocí jedné tabulky dědičnosti (Návrhář relací objektů)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Základní informace o dědičnosti (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Dědičnost](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)