---
title: Metody DataContext (O-R Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9d7e0eee35e0f1e62247865bd539aab8d21349d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657390"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (Návrhář relací objektů)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId:///T: System. data. Linq. DataContext? qualifyHint = false & autoupgrade = true) [LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)metody třídy <xref:System.Data.Linq.DataContext>, které spouštějí uložené procedury a funkce v rámci databáze.

 Třída <xref:System.Data.Linq.DataContext> je [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třída, která funguje jako trubka mezi SQL Server databází a třídami [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] entit mapovanými na tuto databázi. Třída <xref:System.Data.Linq.DataContext> obsahuje informace o připojovacím řetězci a metody pro připojení k databázi a manipulaci s daty v databázi. Ve výchozím nastavení třída <xref:System.Data.Linq.DataContext> obsahuje několik metod, které lze volat, například metodu <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, která odesílá aktualizovaná data z třídy [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] do databáze. Můžete také vytvořit další <xref:System.Data.Linq.DataContext> metody, které jsou mapovány na uložené procedury a funkce. Jinými slovy, volání těchto vlastních metod spustí uloženou proceduru nebo funkci v databázi, na kterou je namapována metoda <xref:System.Data.Linq.DataContext>. Můžete přidat nové metody do <xref:System.Data.Linq.DataContext> třídy stejně, jako byste přidali metody pro rozšiřování libovolné třídy. V diskusích o metodách <xref:System.Data.Linq.DataContext> v kontextu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] je však <xref:System.Data.Linq.DataContext> metodami, které jsou mapovány na uložené procedury a funkce, které jsou popsány.

## <a name="methods-pane"></a>Podokno metody
 <xref:System.Data.Linq.DataContext> metody, které se mapují k uloženým procedurám a funkcím, se zobrazí v podokně metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Podokno metody je podokno podél strany podokna **entity** (hlavní návrhová plocha). Podokno metody obsahuje seznam všech <xref:System.Data.Linq.DataContext> metod, které jste vytvořili pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Ve výchozím nastavení je podokno metody prázdné. Přetažením uložených procedur nebo funkcí z **Průzkumník serveru** /**průzkumníku databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] vytvoříte <xref:System.Data.Linq.DataContext> metody a naplníte podokno metody. Další informace naleznete v tématu [How to: Create DataContext Methods namapované na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otevřete a zavřete podokno metody kliknutím pravým tlačítkem myši na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a následným kliknutím na **Skrýt podokno metody** nebo **Zobrazit podokno metody**nebo pomocí klávesové zkratky CTRL + 1.

## <a name="two-types-of-datacontext-methods"></a>Dva typy metod DataContext
 Metody DataContext jsou metody, které jsou mapovány na uložené procedury a funkce v databázi. Metody DataContext lze vytvořit a přidat v podokně metody [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Existují dva různé typy <xref:System.Data.Linq.DataContext> metod; ty, které vracejí jednu nebo více sad výsledků, a ty, které nezahrnují:

- <xref:System.Data.Linq.DataContext> metody, které vracejí jednu nebo více sad výsledků dotazu:

     Vytvořte tento druh metody <xref:System.Data.Linq.DataContext>, když vaše aplikace stačí spustit uložené procedury a funkce v databázi a vracet výsledky. Další informace naleznete v tématu [How to: Create DataContext Methods namapované na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. data. Linq. ISingleResult \<T > a <xref:System.Data.Linq.IMultipleResults>.

- <xref:System.Data.Linq.DataContext> metody, které nevracejí sady výsledků dotazu: například vložení, aktualizace a odstranění pro konkrétní třídu entity.

     Vytvořte tento druh metody <xref:System.Data.Linq.DataContext>, pokud má aplikace spouštět uložené procedury místo použití výchozího [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] chování pro ukládání upravených dat mezi třídou entity a databází. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Návratové typy metod DataContext
 Při přetažení uložených procedur a funkcí z **Průzkumník serveru** /**průzkumníku databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] se návratový typ vygenerované <xref:System.Data.Linq.DataContext> liší v závislosti na tom, kde položku vyřadíte. Vyřazení položek přímo na existující třídu entity vytvoří metodu <xref:System.Data.Linq.DataContext> s návratovým typem třídy entity; vyřazení položek do prázdné oblasti [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (v obou podoknech) vytvoří metodu <xref:System.Data.Linq.DataContext>, která vrátí automaticky generovaný typ. Automaticky generovaný typ, který je vytvořen, má název, který se shoduje s uloženou procedurou nebo názvem funkce a vlastnostmi, které jsou mapovány na pole vracené uloženou procedurou nebo funkcí.

> [!NOTE]
> Můžete změnit návratový typ metody <xref:System.Data.Linq.DataContext> poté, co ji přidáte do podokna metody. Chcete-li zkontrolovat nebo změnit návratový typ metody <xref:System.Data.Linq.DataContext>, vyberte ji a v okně **vlastnosti** Zkontrolujte vlastnost **návratový typ** . Další informace naleznete v tématu [Postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Objekty, které přetáhnete z databáze na plochu návrháře O/R, budou pojmenovány automaticky, a to na základě názvu objektů v databázi. Pokud přetáhnete stejný objekt více než jednou, připojí se k konci nového názvu číslo, které rozlišuje názvy. Pokud názvy objektů databáze obsahují mezery nebo znaky nejsou podporovány v Visual Basic nebo C#, je místo nebo neplatný znak nahrazen podtržítkem.

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [uložené procedury](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) postupy [: vytváření metod DataContext mapovaných na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání, a odstraní návod (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [: přizpůsobení chování vložení, aktualizace a odstranění tříd entit](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [návod: vytváření tříd LINQ to SQL (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
