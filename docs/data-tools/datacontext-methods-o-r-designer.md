---
title: Metody DataContext (Návrhář O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 95d84442b4aba74dbc44b7aacc97d0a965162150
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924964"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (O/R Designer)

<xref:System.Data.Linq.DataContext> metody (v kontextu [LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) jsou metody <xref:System.Data.Linq.DataContext> třídu, která spuštění uložených procedur a funkcí v databázi.

<xref:System.Data.Linq.DataContext> Třída je [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] třídu, která funguje jako přenos mezi databází systému SQL Server a [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] tříd entit namapována na tuto databázi. <xref:System.Data.Linq.DataContext> Třída obsahuje metody pro připojení k databázi a manipulace s daty v databázi a informace o připojovacím řetězci. Ve výchozím nastavení <xref:System.Data.Linq.DataContext> třída obsahuje několik metod, které bude možné volat, například <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodu, která odešle aktualizovaná data z [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] třídy do databáze. Můžete také vytvořit další <xref:System.Data.Linq.DataContext> metody, které se mapují na uložené procedury a funkce. Jinými slovy, volání těchto metod vlastní Spustí uloženou proceduru nebo funkci v databázi do kterého <xref:System.Data.Linq.DataContext> metoda mapována. Můžete přidat nové metody <xref:System.Data.Linq.DataContext> třídy stejně, jako byste přidali metody rozšíření libovolné třídy. Nicméně v diskuzích k žádostem o <xref:System.Data.Linq.DataContext> metody v kontextu **O/R Designer**, je <xref:System.Data.Linq.DataContext> metody, které se mapují na uložené procedury a funkce, které byly diskutovány.

## <a name="methods-pane"></a>Podokno metody

<xref:System.Data.Linq.DataContext> metody, které se mapují na uložené procedury a funkce jsou zobrazeny v **metody** podokně **O/R Designer**. **Metody** podokně je po straně podokna **entity** podokně (hlavní návrhová plocha). **Metody** podokno obsahuje seznam všech <xref:System.Data.Linq.DataContext> metody, které jste vytvořili pomocí **O/R Designer**. Ve výchozím nastavení **metody** podokně je prázdný, přetáhněte uložené procedury nebo funkce z **Průzkumníka serveru** nebo **Průzkumník databáze** na **Návrháře relací objektů**  vytvořit <xref:System.Data.Linq.DataContext> metody a naplňte jimi **metody** podokně. Další informace najdete v tématu [jak: metod vytvoření DataContext namapovaných na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otevření a zavření podokno metody kliknutím pravým tlačítkem myši **O/R Designer** a pak levým na **skrýt podokno metody** nebo **zobrazit podokno metody**, nebo použijte klávesovou zkratku  **CTRL**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Dva typy metod DataContext

Metody DataContext jsou tyto metody, které se mapují na uložené procedury a funkce v databázi. Můžete vytvořit a přidat jednu metodu DataContext na **metody** podokně **O/R Designer**. Existují dva odlišné typy <xref:System.Data.Linq.DataContext> metody; ty, které vrátí jeden nebo více sad výsledků dotazu a ty, které nejsou:

- <xref:System.Data.Linq.DataContext> metody, které vrací jeden nebo více sad výsledků dotazu:

   Vytvořit tento druh <xref:System.Data.Linq.DataContext> metodu, když vaše aplikace potřebuje pouze pro spouštění uložených procedur a funkcí v databázi a výsledky jsou vráceny. Další informace najdete v tématu [jak: metod vytvoření DataContext namapovaných na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, a <xref:System.Data.Linq.IMultipleResults>.

- <xref:System.Data.Linq.DataContext> metody, které nevracejí sad výsledků dotazu: například vloží aktualizace a odstraní pro konkrétní entitu třídu.

   Vytvořit tento druh <xref:System.Data.Linq.DataContext> metodu, pokud má vaše aplikace pro spuštění uložené procedury místo použití výchozí [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] chování při ukládání změněných dat mezi třídu entity a databází. Další informace najdete v tématu [postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Návratové typy metod DataContext

Při přetažení uložených procedur a funkcí z **Průzkumníka serveru** nebo **Průzkumník databáze** na **O/R Designer**, návratový typ vytvořeného <xref:System.Data.Linq.DataContext> Metoda se liší v závislosti na tom, kde je vyřadit položku. Přetažení položek přímo do existující entity třídy vytvoří <xref:System.Data.Linq.DataContext> metoda s návratovým typem třídy entity; přetažení položek na prázdnou oblast **O/R Designer** (v obou podokno) vytvoří <xref:System.Data.Linq.DataContext> – metoda který vrací automaticky generovanému typu. Automaticky generovaný typ má název, který odpovídá uloženou proceduru nebo název funkce a vlastnosti, které mapují na pole vrácené uloženou proceduru nebo funkci.

> [!NOTE]
> Můžete změnit návratový typ <xref:System.Data.Linq.DataContext> metoda po přidání do podokna metody. Zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metoda, vyberte ho a zkontrolujte **návratový typ** vlastnost **vlastnosti** okna. Další informace najdete v tématu [postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Objekty, které můžete přetáhnout z databáze na plochu návrháře relací objektů jsou pojmenovány automaticky na základě názvu objekty v databázi. Pokud přetáhnete na stejný objekt více než jednou, číslo se přidá na konec nový název, který odlišuje názvy. Pokud názvy databázových objektů obsahují mezery nebo znaky nepodporované v jazyce Visual Basic nebo C#, se nahradí mezery nebo neplatné znaky podtržítkem.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Uložené procedury](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (Návrhář relací objektů)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Návod: Přizpůsobení chování tříd entit při vložení, aktualizaci a odstranění](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Návod: Vytvoření LINQ na třídy SQL (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)