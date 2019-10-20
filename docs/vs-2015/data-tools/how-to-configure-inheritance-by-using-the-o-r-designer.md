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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654707"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Postupy: Konfigurace dědičnosti pomocí návrháře O/R
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) podporuje koncept dědičnosti s jednou tabulkou, protože je často implementován v relačních systémech. V případě dědičnosti s jednou tabulkou existuje jedna databázová tabulka, která obsahuje pole pro nadřazené informace i podřízené informace. U relačních dat obsahuje sloupec diskriminátor hodnotu, která určuje, do které třídy patří libovolný záznam.

 Představte si třeba tabulku osob, která obsahuje všechny zaměstnané společnosti. Někteří lidé jsou zaměstnanci a někteří lidé jsou manažeři. Tabulka osob obsahuje sloupec s názvem `EmployeeType`, který má hodnotu 1 pro manažery a hodnotu 2 pro zaměstnance. Toto je sloupec diskriminátoru. V tomto scénáři můžete vytvořit podtřídu zaměstnanců a naplnit třídu pouze záznamy, které mají hodnotu `EmployeeType` 2. Můžete také odebrat sloupce, které se nevztahují na jednotlivé třídy.

 Vytvoření objektového modelu, který používá dědičnost (a odpovídá relačním datům) může být poněkud matoucí. Následující postup popisuje kroky požadované pro konfiguraci dědičnosti s návrhářem relací v/R. Následující obecné kroky, aniž by odkazovaly na existující tabulku a sloupce, mohou být obtížné, takže je k dispozici návod, který používá data. Podrobné pokyny pro konfiguraci dědičnosti pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] naleznete v tématu [Návod: vytváření LINQ to SQL tříd pomocí dědičnosti s jednou tabulkou (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

### <a name="to-create-inherited-data-classes"></a>Vytvoření zděděných datových tříd

1. Otevřete [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] přidáním položky **LINQ to SQL třídy** do existující Visual Basic nebo C# projektu.

2. Přetáhněte tabulku, kterou chcete použít, jako základní třídu na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

3. Přetáhněte druhou kopii tabulky na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a přejmenujte ji. Toto je odvozená třída nebo podtřída.

4. Klikněte na **Dědičnost** na kartě **Návrhář relací objektů** **panelu nástrojů**a potom klikněte na podtřídu (tabulku, kterou jste přejmenovali), a připojte ji k základní třídě.

    > [!NOTE]
    > Klikněte na položku **Dědičnost** v **sadě nástrojů** a uvolněte tlačítko myši, klikněte na druhou kopii třídy, kterou jste vytvořili v kroku 3, a poté klikněte na první třídu, kterou jste vytvořili v kroku 2. Šipka na čáře dědičnosti bude ukazovat na první třídu.

5. V každé třídě odstraňte všechny vlastnosti objektů, které nechcete zobrazit, a které nejsou použity pro přidružení. Pokud se pokusíte odstranit vlastnosti objektu používané pro přidružení, dojde k chybě. [vlastnost \<property název > nelze odstranit, protože se účastní \<association název přidružení >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Vzhledem k tomu, že odvozená třída dědí vlastnosti definované v její základní třídě, nelze v každé třídě definovat stejné sloupce. (Sloupce jsou implementovány jako vlastnosti.) Můžete povolit vytváření sloupců v odvozené třídě nastavením modifikátoru dědičnosti u vlastnosti v základní třídě. Další informace naleznete v tématu [Not in Build: přepisování vlastností a metod](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213).

6. Vyberte čáru dědičnosti v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

7. V okně **vlastnosti** nastavte **vlastnost diskriminátor** na název sloupce, který se používá k rozlišení záznamů ve třídách.

8. Nastavte vlastnost **hodnoty diskriminátoru odvozené třídy** na hodnotu v databázi, která označuje záznam jako zděděný typ. (Jedná se o hodnotu, která je uložena ve sloupci diskriminátor a která se používá k určení zděděné třídy.)

9. Nastavte vlastnost **hodnoty diskriminátoru základní třídy** na hodnotu, která označuje záznam jako základní typ. (Jedná se o hodnotu, která je uložena ve sloupci diskriminátor a která se používá k určení základní třídy.)

10. Volitelně můžete také nastavit **výchozí vlastnost dědičnosti** tak, aby určila typ v hierarchii dědičnosti, který se používá při načítání řádků, které neodpovídají žádnému definovanému kódu dědičnosti. Jinými slovy, pokud má záznam hodnotu ve sloupci diskriminátoru, která neodpovídá hodnotě buď v **odvozené třídě** , nebo ve vlastnostech **hodnoty diskriminátoru základní třídy** , záznam se načte do typu určeného jako  **Dědičnost – výchozí**

## <a name="see-also"></a>Viz také
 [LINQ to SQL Tools v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [– Návod: vytváření tříd LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [Pave novinky pro vývoj aplikací pro data v aplikaci Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [přístup k datům v aplikaci Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [ Návod: vytváření tříd LINQ to SQL pomocí dědění s jednou tabulkou (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [, které nejsou v sestavení: dědičnost v Visual Basic](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [dědění](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)
