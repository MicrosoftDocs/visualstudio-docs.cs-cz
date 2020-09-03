---
title: 'Postupy: Konfigurace dědičnosti pomocí návrháře O-R | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f8c08546fdf96c755b3adb80021ab7269509739
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654707"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Postupy: Konfigurace dědičnosti pomocí Návrháře relací objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozhraní [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) podporuje koncept dědičnosti jedné tabulky, protože je často implementován v relačních systémech. V případě dědičnosti s jednou tabulkou existuje jedna databázová tabulka, která obsahuje pole pro nadřazené informace i podřízené informace. U relačních dat obsahuje sloupec diskriminátor hodnotu, která určuje, do které třídy patří libovolný záznam.

 Představte si třeba tabulku osob, která obsahuje všechny zaměstnané společnosti. Někteří lidé jsou zaměstnanci a někteří lidé jsou manažeři. Tabulka osob obsahuje sloupec s názvem `EmployeeType` 1 pro manažery a hodnotu 2 pro zaměstnance. Toto je sloupec diskriminátor. V tomto scénáři můžete vytvořit podtřídu zaměstnanců a naplnit třídu pouze záznamy, které mají `EmployeeType` hodnotu 2. Můžete také odebrat sloupce, které se nevztahují na jednotlivé třídy.

 Vytvoření objektového modelu, který používá dědičnost (a odpovídá relačním datům) může být poněkud matoucí. Následující postup popisuje kroky požadované pro konfiguraci dědičnosti s návrhářem relací v/R. Následující obecné kroky, aniž by odkazovaly na existující tabulku a sloupce, mohou být obtížné, takže je k dispozici návod, který používá data. Podrobné pokyny pro konfiguraci dědičnosti pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] naleznete v tématu [Návod: vytváření tříd LINQ to SQL pomocí dědičnosti s jednou tabulkou (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

### <a name="to-create-inherited-data-classes"></a>Vytvoření zděděných datových tříd

1. Otevřete přidáním [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] položky **LINQ to SQL třídy** do existujícího projektu Visual Basic nebo C#.

2. Přetáhněte tabulku, kterou chcete použít jako základní třídu, do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

3. Přetáhněte druhou kopii tabulky na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a přejmenujte ji. Toto je odvozená třída nebo podtřída.

4. Klikněte na **Dědičnost** na kartě **Návrhář relací objektů** **panelu nástrojů**a potom klikněte na podtřídu (tabulku, kterou jste přejmenovali), a připojte ji k základní třídě.

    > [!NOTE]
    > Klikněte na položku **Dědičnost** v **sadě nástrojů** a uvolněte tlačítko myši, klikněte na druhou kopii třídy, kterou jste vytvořili v kroku 3, a poté klikněte na první třídu, kterou jste vytvořili v kroku 2. Šipka na čáře dědičnosti bude ukazovat na první třídu.

5. V každé třídě odstraňte všechny vlastnosti objektů, které nechcete zobrazit, a které nejsou použity pro přidružení. Pokud se pokusíte odstranit vlastnosti objektu používané pro přidružení, dojde k chybě: [vlastnost \<property name> nelze odstranit, protože se účastní přidružení \<association name> ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Vzhledem k tomu, že odvozená třída dědí vlastnosti definované v její základní třídě, nelze v každé třídě definovat stejné sloupce. (Sloupce jsou implementovány jako vlastnosti.) Můžete povolit vytváření sloupců v odvozené třídě nastavením modifikátoru dědičnosti u vlastnosti v základní třídě. Další informace naleznete v tématu [Not in Build: přepisování vlastností a metod](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213).

6. Vyberte čáru dědičnosti v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

7. V okně **vlastnosti** nastavte **vlastnost diskriminátor** na název sloupce, který se používá k rozlišení záznamů ve třídách.

8. Nastavte vlastnost **hodnoty diskriminátoru odvozené třídy** na hodnotu v databázi, která označuje záznam jako zděděný typ. (Jedná se o hodnotu, která je uložena ve sloupci diskriminátor a která se používá k určení zděděné třídy.)

9. Nastavte vlastnost **hodnoty diskriminátoru základní třídy** na hodnotu, která označuje záznam jako základní typ. (Jedná se o hodnotu, která je uložena ve sloupci diskriminátor a která se používá k určení základní třídy.)

10. Volitelně můžete také nastavit **výchozí vlastnost dědičnosti** tak, aby určila typ v hierarchii dědičnosti, který se používá při načítání řádků, které neodpovídají žádnému definovanému kódu dědičnosti. Jinými slovy, pokud má záznam hodnotu ve sloupci diskriminátoru, která neodpovídá hodnotě buď v **odvozené třídě** , nebo ve vlastnostech **hodnoty diskriminátoru základní třídy** , záznam se načte do typu, který je určený jako **Výchozí hodnota dědičnosti**.

## <a name="see-also"></a>Viz také
 [LINQ to SQL Tools v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [– Návod: vytváření tříd LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [Pave novinky při vývoji aplikací pro data v aplikaci Visual Studio 2012 s](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [přístupem k datům v aplikaci Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [návodu: vytváření LINQ to SQL tříd pomocí dědičnosti s jednou TABULKOU (o/R designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [, která není v buildu: dědičnost v Visual Basic](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [dědění](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)
