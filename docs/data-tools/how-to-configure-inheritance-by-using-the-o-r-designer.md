---
title: 'Postupy: Konfigurace dědičnosti pomocí návrháře O-R'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e31e5e78d5c72167f9d1c1eaab974155a4c369f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282238"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Postupy: Konfigurace dědičnosti pomocí Návrháře relací objektů
**Návrhář relací objektů** (**O/R Designer**) podporuje koncept dědičnosti s jednou tabulkou, protože je často implementován v relačních systémech. V případě dědičnosti s jednou tabulkou existuje jedna databázová tabulka, která obsahuje pole pro nadřazené informace i podřízené informace. U relačních dat obsahuje sloupec diskriminátor hodnotu, která určuje, do které třídy patří libovolný záznam.

Představte si třeba `Persons` tabulku, která obsahuje každého zaměstnaného společností. Někteří lidé jsou zaměstnanci a někteří lidé jsou manažeři. `Persons`Tabulka obsahuje sloupec s názvem `EmployeeType` , který má hodnotu 1 pro manažery a hodnotu 2 pro zaměstnance. Toto je sloupec diskriminátor. V tomto scénáři můžete vytvořit podtřídu zaměstnanců a naplnit třídu pouze záznamy, které mají `EmployeeType` hodnotu 2. Můžete také odebrat sloupce, které se nevztahují na jednotlivé třídy.

Vytvoření objektového modelu, který používá dědičnost (a odpovídá relačním datům) může být poněkud matoucí. Následující postup popisuje kroky požadované pro konfiguraci dědičnosti s **návrhářem relací v/R**. Následující obecné kroky, aniž by odkazovaly na existující tabulku a sloupce, mohou být obtížné, takže je k dispozici návod, který používá data. Podrobné pokyny pro konfiguraci dědičnosti pomocí **Návrháře O/r**naleznete v tématu [návod: vytváření LINQ to SQLch tříd pomocí dědičnosti s jednou tabulkou (O/r Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Vytvoření zděděných datových tříd

1. Otevřete **návrháře o/R** přidáním položky **LINQ to SQL třídy** do existujícího projektu Visual Basic nebo C#.

2. Přetáhněte tabulku, kterou chcete použít jako základní třídu, do **návrháře o/R**.

3. Přetáhněte druhou kopii tabulky do **návrháře o/R** a přejmenujte ji. Toto je odvozená třída nebo podtřída.

4. Klikněte na **Dědičnost** na kartě **Návrhář relací objektů** **panelu nástrojů**a potom klikněte na podtřídu (tabulku, kterou jste přejmenovali), a připojte ji k základní třídě.

    > [!NOTE]
    > Klikněte na položku **Dědičnost** v **sadě nástrojů** a uvolněte tlačítko myši, klikněte na druhou kopii třídy, kterou jste vytvořili v kroku 3, a poté klikněte na první třídu, kterou jste vytvořili v kroku 2. Šipka na čáře dědičnosti odkazuje na první třídu.

5. V každé třídě odstraňte všechny vlastnosti objektů, které nechcete zobrazit, a které nejsou použity pro přidružení. Pokud se pokusíte odstranit vlastnosti objektu používané pro přidružení, dojde k chybě: [vlastnost \<property name> nelze odstranit, \<association name> protože se účastní přidružení ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Vzhledem k tomu, že odvozená třída dědí vlastnosti definované v její základní třídě, nelze v každé třídě definovat stejné sloupce. (Sloupce jsou implementovány jako vlastnosti.) Můžete povolit vytváření sloupců v odvozené třídě nastavením modifikátoru dědičnosti u vlastnosti v základní třídě. Další informace najdete v tématu [základy dědičnosti (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. Vyberte čáru dědičnosti v **Návrháři o/R**.

7. V okně **vlastnosti** nastavte **vlastnost diskriminátor** na název sloupce, který rozlišuje záznamy ve třídách.

8. Nastavte vlastnost **hodnoty diskriminátoru odvozené třídy** na hodnotu v databázi, která označuje záznam jako zděděný typ. (Jedná se o hodnotu, která je uložena ve sloupci diskriminátor a slouží k určení zděděné třídy.)

9. Nastavte vlastnost **hodnoty diskriminátoru základní třídy** na hodnotu, která označuje záznam jako základní typ. (Jedná se o hodnotu, která je uložena ve sloupci diskriminátor a slouží k určení základní třídy.)

10. Volitelně můžete také nastavit **výchozí vlastnost dědičnosti** tak, aby určila typ v hierarchii dědičnosti, který se používá při načítání řádků, které neodpovídají žádnému definovanému kódu dědičnosti. Jinými slovy, pokud má záznam hodnotu ve sloupci diskriminátor, která neodpovídá hodnotě buď v **odvozené třídě** , nebo ve vlastnostech **hodnoty diskriminátoru základní třídy** , záznam se načte do typu určeného jako **výchozí nastavení dědičnosti**.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: vytváření tříd LINQ to SQL (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Technologie LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Návod: vytváření tříd LINQ to SQL pomocí dědičnosti s jednou tabulkou (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Základy dědičnosti (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Dědičnost](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
