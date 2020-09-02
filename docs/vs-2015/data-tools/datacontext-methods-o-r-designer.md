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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657390"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (Návrhář relací objektů)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId:///T: System. data. Linq. DataContext? qualifyHint = false&autoupgrade = true) [LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)metody <xref:System.Data.Linq.DataContext> třídy, která spouští uložené procedury a funkce v databázi.

 <xref:System.Data.Linq.DataContext>Třída je [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třída, která funguje jako trubka mezi SQL Server databáze a [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídami entit mapovanými na tuto databázi. <xref:System.Data.Linq.DataContext>Třída obsahuje informace o připojovacím řetězci a metody pro připojení k databázi a manipulaci s daty v databázi. Ve výchozím nastavení <xref:System.Data.Linq.DataContext> Třída obsahuje několik metod, které lze volat, například <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodu, která odesílá aktualizovaná data z [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] tříd do databáze. Můžete také vytvořit další <xref:System.Data.Linq.DataContext> metody, které jsou mapovány na uložené procedury a funkce. Jinými slovy, volání těchto vlastních metod spustí uloženou proceduru nebo funkci v databázi, <xref:System.Data.Linq.DataContext> na kterou je metoda namapována. Můžete přidat nové metody do <xref:System.Data.Linq.DataContext> třídy stejně, jako byste přidali metody pro rozšiřování libovolné třídy. V diskusích o <xref:System.Data.Linq.DataContext> metodách v kontextu, se však jedná o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> metody, které jsou mapovány na uložené procedury a funkce, které jsou popsány.

## <a name="methods-pane"></a>Podokno metody
 <xref:System.Data.Linq.DataContext> metody, které jsou mapovány na uložené procedury a funkce, jsou zobrazeny v podokně metody v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Podokno metody je podokno podél strany podokna **entity** (hlavní návrhová plocha). Podokno metody obsahuje seznam všech <xref:System.Data.Linq.DataContext> metod, které jste vytvořili pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Ve výchozím nastavení je podokno metody prázdné. Přetažením uložených procedur nebo funkcí z **Průzkumník serveru** / **Průzkumníku databáze** do nástroje [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] vytvořte <xref:System.Data.Linq.DataContext> metody a naplňte podokno metody. Další informace naleznete v tématu [How to: Create DataContext Methods namapované na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otevřete a zavřete podokno metody kliknutím pravým tlačítkem myši na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a potom kliknutím na **Skrýt podokno metody** nebo **Zobrazit podokno metody**nebo pomocí klávesové zkratky CTRL + 1.

## <a name="two-types-of-datacontext-methods"></a>Dva typy metod DataContext
 Metody DataContext jsou metody, které jsou mapovány na uložené procedury a funkce v databázi. Metody DataContext lze vytvořit a přidat v podokně metody v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Existují dva různé typy metod, <xref:System.Data.Linq.DataContext> které vracejí jednu nebo více sad výsledků, a ty, které nedělají:

- <xref:System.Data.Linq.DataContext> metody, které vracejí jednu nebo více sad výsledků dotazu:

     Vytvořte tento druh <xref:System.Data.Linq.DataContext> metody, pokud vaše aplikace potřebuje pouze spouštět uložené procedury a funkce v databázi a vracet výsledky. Další informace naleznete v tématu [How to: Create DataContext Methods namapované na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. data. Linq. ISingleResult \<T> a <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext> metody, které nevracejí sady výsledků dotazu: například vložení, aktualizace a odstranění pro konkrétní třídu entity.

     Vytvořte tento druh <xref:System.Data.Linq.DataContext> metody v případě, že aplikace musí spustit uložené procedury namísto použití výchozího [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] chování pro ukládání upravených dat mezi třídou entity a databází. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Návratové typy metod DataContext
 Při přetahování uložených procedur a funkcí z **Průzkumník serveru** / **Průzkumníku databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , se návratový typ vygenerované <xref:System.Data.Linq.DataContext> metody liší v závislosti na tom, kde položku vyřadíte. Vyřazení položek přímo na existující třídu entity vytvoří <xref:System.Data.Linq.DataContext> metodu s návratovým typem třídy entity; vyřazení položek do prázdné oblasti [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (v obou podoknech) vytvoří <xref:System.Data.Linq.DataContext> metodu, která vrátí automaticky generovaný typ. Automaticky generovaný typ, který je vytvořen, má název, který se shoduje s uloženou procedurou nebo názvem funkce a vlastnostmi, které jsou mapovány na pole vracené uloženou procedurou nebo funkcí.

> [!NOTE]
> Návratový typ metody lze změnit <xref:System.Data.Linq.DataContext> poté, co ji přidáte do podokna metody. Chcete-li zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metody, vyberte ji a v okně **vlastnosti** Zkontrolujte vlastnost **návratový typ** . Další informace naleznete v tématu [Postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Objekty, které přetáhnete z databáze na plochu návrháře O/R, budou pojmenovány automaticky, a to na základě názvu objektů v databázi. Pokud přetáhnete stejný objekt více než jednou, připojí se k konci nového názvu číslo, které rozlišuje názvy. Pokud názvy objektů databáze obsahují mezery nebo znaky nejsou podporovány v Visual Basic nebo C#, je místo nebo neplatný znak nahrazen podtržítkem.

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [uložené procedury postupy](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) [: vytváření metod DataContext mapovaných na uložené procedury a funkce (O/r Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/r návrháře)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [Návod: přizpůsobení chování operace INSERT, Update a DELETE pro třídy entit](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [Návod: vytváření tříd LINQ to SQL (Návrhář o-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
