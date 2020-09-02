---
title: Nástroje LINQ to SQL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651520"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Nástroje LINQ to SQL v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL byla první technologie mapování relačních objektů, kterou vydala Microsoft. Funguje dobře v základních scénářích a nadále je podporována v sadě Visual Studio, ale nadále není v aktivním vývoji. Použijte LINQ to SQL při údržbě starší verze aplikace, která ji již používá, nebo v jednoduchých aplikacích, které používají SQL Server a nevyžadují mapování více tabulek. Obecně platí, že nové aplikace by měly používat Entity Framework, když je vyžadována vrstva relačního mapovače objektu.

 V aplikaci Visual Studio vytvoříte LINQ to SQL třídy, které reprezentují tabulky SQL pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Má dvě odlišné oblasti na své návrhové ploše: podokno entity na levé straně a podokno metody na pravé straně. Podokno entity je hlavní návrhovou plochou, která zobrazuje třídy entit, přidružení a Hierarchie dědičnosti. Podokno metody je návrhová plocha, která zobrazuje <xref:System.Data.Linq.DataContext> metody, které jsou mapovány na uložené procedury a funkce.

 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) Poskytuje vizuální návrhovou plochu pro vytváření [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) tříd entit a přidružení (relace), které jsou založené na objektech v databázi. Jinými slovy, se [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] používá k vytvoření objektového modelu v aplikaci, která je mapována na objekty v databázi. Také generuje silný typ <xref:System.Data.Linq.DataContext> , který slouží k posílání a přijímání dat mezi třídami entit a databází. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Poskytuje také funkce pro mapování uložených procedur a funkcí na <xref:System.Data.Linq.DataContext> metody pro vracení dat a naplnění tříd entit. Nakonec [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] poskytuje možnost navrhovat vztahy dědičnosti mezi třídami entit.

## <a name="opening-the-or-designer"></a>Otevření návrháře O/R
 Chcete-li do projektu přidat model entity LINQ to SQL, zvolte **projekt &#124; přidat novou položku** a poté v seznamu položek projektu zvolte možnost  **třídy LINQ to SQL** :

 ![Třídy LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "Třídy LINQ to SQL raddata")

 Visual Studio vytvoří soubor. dbml a přidá ho do vašeho řešení. Toto je soubor mapování XML a jeho související soubory kódu.

 ![Třídy LINQ to SQL v Průzkumník řešení](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL třídy v Průzkumník řešení")

 Když vyberete soubor. dbml, Visual Studio zobrazí plochu návrháře O/R, která vám umožní vizuálně vytvořit model. Následující ilustrace znázorňuje návrháře po přetažení tabulek zákazníků a objednávek Northwind z Průzkumník serveru. Poznamenejte si vztah mezi tabulkami.

 ![Návrhář LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "Návrhář LINQ to SQL raddata")

> [!IMPORTANT]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Je jednoduché relační mapování objektů, protože podporuje pouze 1:1 vztahů. Jinými slovy, Třída entity může mít pouze vztah 1:1 mapování s databázovou tabulkou nebo zobrazením. Komplexní mapování, jako je například mapování třídy entity na propojenou tabulku, není podporováno. pro komplexní mapování použijte Entity Framework. Kromě toho je Návrhář jednosměrný generátor kódu. To znamená, že v souboru kódu se projeví pouze změny, které provedete v návrhové ploše. Ruční změny v souboru kódu se neprojeví v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Všechny změny, které provedete ručně v souboru kódu, jsou při uložení návrháře přepsány a kód je znovu vygenerován. Informace o tom, jak přidat uživatelský kód a jak rozšiřuje třídy vygenerované pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , naleznete v tématu [How to: Extending Code Generate-/R Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Vytvoření a konfigurace kontextu DataContext
 Po přidání položky **LINQ to SQL třídy** do projektu a otevření [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , prázdná návrhová plocha představuje prázdný <xref:System.Data.Linq.DataContext> připravený ke konfiguraci. <xref:System.Data.Linq.DataContext>je nakonfigurován s informacemi o připojení, které jsou k dispozici v první položce, která je přetažena na návrhovou plochu. Proto <xref:System.Data.Linq.DataContext> je nakonfigurován pomocí informací o připojení z první položky vynechané na návrhové ploše. Další informace o <xref:System.Data.Linq.DataContext> třídě naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Vytváření tříd entit, které jsou mapovány k tabulkám a zobrazením databáze
 Třídy entit mapované na tabulky a zobrazení můžete vytvořit přetažením databázových tabulek a zobrazení z **Průzkumník serveru** / **Průzkumníku databáze** do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Jak je uvedeno v předchozí části, <xref:System.Data.Linq.DataContext> je nakonfigurován s informacemi o připojení, které jsou k dispozici v první položce, která je přetažena na návrhovou plochu. Pokud je do nástroje přidána následující položka, která používá jiné připojení [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , můžete změnit připojení pro <xref:System.Data.Linq.DataContext> . Další informace naleznete v tématu [How to: Create LINQ to SQL Classes mapované na tabulky a zobrazení (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Vytváření metod DataContext, které volají uložené procedury a funkce
 Můžete vytvořit <xref:System.Data.Linq.DataContext> metody, které volají (jsou mapovány na) uložené procedury a funkce přetažením z **Průzkumník serveru** / **Průzkumníku databáze** do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Uložené procedury a funkce jsou přidány do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] metody as v <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> Při přetahování uložených procedur a funkcí z **Průzkumník serveru** / **Průzkumníku databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , se návratový typ vygenerované <xref:System.Data.Linq.DataContext> metody liší v závislosti na tom, kde položku vyřadíte. Další informace naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurace kontextu DataContext pro použití uložených procedur k uložení dat mezi třídami entit a databází
 Jak bylo uvedeno dříve, můžete vytvořit <xref:System.Data.Linq.DataContext> metody, které volají uložené procedury a funkce. Kromě toho můžete také přiřadit uložené procedury, které lze použít pro výchozí [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] chování modulu runtime, které provádí vložení, aktualizace a odstranění. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Dědičnost a O/R Designer
 Stejně jako jiné objekty [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] mohou třídy použít dědičnost a být odvozeny od jiných tříd. V databázi jsou vztahy dědičnosti vytvářeny několika způsoby. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Podporuje koncepci dědičnosti jedné tabulky, protože je často implementována v relačních systémech. Další informace naleznete v tématu [How to: Configure dědičnost pomocí návrháře o/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Dotazy LINQ to SQL
 Třídy entit vytvořené pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jsou určeny pro použití s [LINQ (dotazem integrovaným na jazyce)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Další informace naleznete v tématu [How to: Query for Information](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oddělení generovaného kódu třídy DataContext a entity do různých oborů názvů
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Poskytuje **obor názvů kontextu** a vlastnosti **oboru názvů entit** v <xref:System.Data.Linq.DataContext> . Tyto vlastnosti určují, do kterého oboru názvů se <xref:System.Data.Linq.DataContext> kód třídy a tříd entit generuje. Ve výchozím nastavení jsou tyto vlastnosti prázdné a <xref:System.Data.Linq.DataContext> třídy entit a jsou generovány do oboru názvů aplikace. Chcete-li vygenerovat kód do jiného oboru názvů, než je obor názvů aplikace, zadejte hodnotu do pole **obor názvů kontextu** a/nebo vlastnosti **oboru názvů entit** .

## <a name="in-this-section"></a>V této části
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) Vysvětluje <xref:System.Data.Linq.DataContext> , jaké metody jsou a jak je vytvořit.

 [Dědičnost datových tříd (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md) Popisuje koncept dědičnosti jedné tabulky a způsobu jeho implementace v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Postupy: vytváření tříd LINQ to SQL mapovaných na tabulky a zobrazení (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) Popisuje, jak vytvořit třídy entit, které jsou mapovány na tabulky a zobrazení v databázi.

 [Postupy: vytvoření přidružení (relace) mezi třídami LINQ to SQL (Návrhář O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) Popisuje, jak vytvořit relaci mezi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] třídami entit.

 [Postupy: vytváření metod DataContext mapovaných na uložené procedury a funkce (Návrhář O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Popisuje, jak vytvořit <xref:System.Data.Linq.DataContext> metody, které spouštějí uložené procedury nebo funkce při jejich volání.

 [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (Návrhář O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) Popisuje, jak nakonfigurovat <xref:System.Data.Linq.DataContext> pro použití uložených procedur při ukládání dat z tříd entit zpět do databáze.

 [Postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Popisuje, jak nastavit návratový typ <xref:System.Data.Linq.DataContext> metody tak, aby byl typem třídy entity nebo automaticky generovaným typem vytvořeným návrhářem pro/R.

 [Postupy: Přidání ověřování do tříd entit](../data-tools/how-to-add-validation-to-entity-classes.md) Popisuje, jak generovat částečné metody, které umožňují přidání kódu při změnách vlastností a aktualizacích tříd entit.

 [Postupy: zapnutí a vypnutí funkce plural (o/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) Popisuje, jak zapnout a vypnout automatické přejmenování tříd, které jsou přidány do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Postupy: Konfigurace dědičnosti pomocí návrháře o/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Popisuje, jak konfigurovat třídy entit pomocí dědičnosti s jednou tabulkou s [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Postupy: rozšiřování kódu generovaného návrhářem O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) Popisuje, jak a kde přidat kód, který nebude přepsán, pokud změny objektů v Návrháři O/R znovu vygenerují kód.

 [Návod: vytváření tříd LINQ to SQL pomocí dědičnosti s jednou tabulkou (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) Poskytuje podrobné pokyny pro konfiguraci tříd entit pomocí dědičnosti jedné tabulky s [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Návod: přizpůsobení chování při vložení, aktualizaci a odstranění tříd entit](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) Poskytuje podrobné pokyny pro konfiguraci a <xref:System.Data.Linq.DataContext> použití uložených procedur při ukládání dat z tříd entit zpět do databáze.

## <a name="reference-content"></a>Referenční obsah
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools pro .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) – [Nejčastější dotazy](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [přístupu k datům v aplikaci Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
