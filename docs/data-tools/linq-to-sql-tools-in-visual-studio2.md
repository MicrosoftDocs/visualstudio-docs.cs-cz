---
title: Přehled návrháře LINQ to SQL O/R
description: Získejte přehled o LINQ to SQLch nástrojích v aplikaci Visual Studio. Přečtěte si o Návrhář relací objektů (Návrhář O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: af394318d18244fc6e20e517d0ff985ca5e5ad1f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436234"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Nástroje LINQ to SQL v aplikaci Visual Studio

LINQ to SQL byla první technologie mapování relačních objektů, kterou vydala Microsoft. Funguje dobře v základních scénářích a nadále je podporována v sadě Visual Studio, ale už není v aktivním vývoji. Použijte LINQ to SQL při údržbě starší verze aplikace, která ji už používá, nebo v jednoduchých aplikacích, které používají SQL Server a nevyžadují mapování více tabulek. Obecně platí, že nové aplikace by měly používat Entity Framework, když je vyžadována vrstva relačního mapovače objektu.

## <a name="install-the-linq-to-sql-tools"></a>Instalace nástrojů LINQ to SQL

V aplikaci Visual Studio vytvoříte LINQ to SQL třídy, které reprezentují tabulky SQL pomocí **Návrhář relací objektů** ( **O/R Designer** ). Návrhář O/R je uživatelské rozhraní pro úpravy souborů. dbml. Úpravy souborů. dbml s plochou návrháře vyžaduje LINQ to SQL nástroje, které nejsou ve výchozím nastavení nainstalovány jako součást některé z úloh sady Visual Studio.

Chcete-li nainstalovat nástroje LINQ to SQL, spusťte instalační program sady Visual Studio, zvolte možnost **změnit** , pak vyberte kartu **jednotlivé součásti** a poté vyberte možnost **LINQ to SQL nástroje** v kategorii **nástroje kódu** .

## <a name="what-is-the-or-designer"></a>Co je Návrhář O/R

**Návrhář o/R** má dvě odlišné oblasti na své návrhové ploše: podokno entity na levé straně a podokno metody na pravé straně. Podokno entity je hlavní návrhovou plochou, která zobrazuje třídy entit, přidružení a Hierarchie dědičnosti. Podokno metody je návrhová plocha, která zobrazuje <xref:System.Data.Linq.DataContext> metody, které jsou mapovány na uložené procedury a funkce.

**Návrhář o/R** poskytuje vizuální návrhovou plochu pro vytváření [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) tříd entit a přidružení (relace), které jsou založené na objektech v databázi. Jinými slovy **Návrhář o/R** vytvoří objektový model v aplikaci, která je mapována na objekty v databázi. Také generuje silně typované <xref:System.Data.Linq.DataContext> , který odesílá a přijímá data mezi třídami entit a databází. **Návrhář o/R** také poskytuje funkce pro mapování uložených procedur a funkcí na <xref:System.Data.Linq.DataContext> metody pro vracení dat a naplnění tříd entit. Nakonec **Návrhář o/R** poskytuje možnost navrhovat vztahy dědičnosti mezi třídami entit.

## <a name="open-the-or-designer"></a>Otevření návrháře pro/R

Chcete-li přidat model entity LINQ to SQL do projektu, zvolte možnost **projekt**  >  **Přidat novou položku** a poté vyberte položku **LINQ to SQL třídy** ze seznamu položek projektu:

![Třídy LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio vytvoří soubor *. dbml* a přidá ho do vašeho řešení. Toto je soubor mapování XML a jeho související soubory kódu.

![Třídy LINQ to SQL v Průzkumník řešení](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Když vyberete soubor *. dbml* , Visual Studio zobrazí plochu **Návrháře O/R** , která vám umožní vizuálně vytvořit model. Následující ilustrace znázorňuje návrháře po `Customers` `Orders` přetažení tabulky Northwind z **Průzkumník serveru**. Poznamenejte si vztah mezi tabulkami.

![Návrhář LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **Návrhář o/R** je jednoduché relační mapování objektů, protože podporuje jenom 1:1 vztahů s mapováním. Jinými slovy, Třída entity může mít pouze vztah 1:1 mapování s databázovou tabulkou nebo zobrazením. Komplexní mapování, jako je například mapování třídy entity na propojenou tabulku, není podporováno. pro komplexní mapování použijte Entity Framework. Kromě toho je Návrhář jednosměrný generátor kódu. To znamená, že v souboru kódu se projeví pouze změny, které provedete v návrhové ploše. Ruční změny v souboru kódu se neprojeví v **Návrháři o/R**. Všechny změny, které provedete ručně v souboru kódu, jsou při uložení návrháře přepsány a kód je znovu vygenerován. Informace o tom, jak přidat uživatelský kód a roztáhnout třídy vygenerované v **/r návrháři** , naleznete v tématu [How to: Extending Code Generate-to/r Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Vytvoření a konfigurace kontextu DataContext

Po přidání položky **LINQ to SQL třídy** do projektu a otevření **návrháře o/R** , prázdná návrhová plocha představuje prázdný <xref:System.Data.Linq.DataContext> připravený ke konfiguraci. <xref:System.Data.Linq.DataContext>je nakonfigurován s informacemi o připojení, které jsou k dispozici v první položce, která je přetažena na návrhovou plochu. Proto <xref:System.Data.Linq.DataContext> je nakonfigurován pomocí informací o připojení z první položky vynechané na návrhové ploše. Další informace o <xref:System.Data.Linq.DataContext> třídě naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Vytváření tříd entit, které jsou mapovány na tabulky a zobrazení databáze

Třídy entit mapované na tabulky a zobrazení můžete vytvořit přetažením databázových tabulek a zobrazení z **Průzkumník serveru** nebo z **Průzkumníka databáze** do **návrháře pro/R**. Jak je uvedeno v předchozí části, <xref:System.Data.Linq.DataContext> je nakonfigurován s informacemi o připojení, které jsou k dispozici v první položce, která je přetažena na návrhovou plochu. Pokud je následující položka, která používá jiné připojení, přidána do **návrháře o/R** , můžete změnit připojení pro <xref:System.Data.Linq.DataContext> . Další informace naleznete v tématu [How to: Create LINQ to SQL Classes mapované na tabulky a zobrazení (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Vytvoření metod DataContext, které volají uložené procedury a funkce

Můžete vytvořit <xref:System.Data.Linq.DataContext> metody, které volají (jsou namapovány na) uložené procedury a funkce přetažením z **Průzkumník serveru** nebo **Průzkumníka databáze** do **návrháře o/R**. Uložené procedury a funkce jsou přidány do **návrháře o/R** jako metody <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> Když přetáhnete uložené procedury a funkce z **Průzkumník serveru** nebo **Průzkumníka databáze** do **návrháře o/R** , návratový typ vygenerované <xref:System.Data.Linq.DataContext> metody se liší v závislosti na tom, kde položku vyřadíte. Další informace naleznete v tématu [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurace DataContext pro použití uložených procedur k uložení dat mezi třídami entit a databází

Jak bylo uvedeno dříve, můžete vytvořit <xref:System.Data.Linq.DataContext> metody, které volají uložené procedury a funkce. Kromě toho můžete také přiřadit uložené procedury, které jsou používány pro výchozí LINQ to SQL chování při spuštění, které provádí vkládání, aktualizace a odstraňování. Další informace naleznete v tématu [Postupy: přiřazení uložených procedur pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Dědičnost a O/R Designer

Stejně jako jiné objekty mohou LINQ to SQL třídy používat dědičnost a být odvozeny od jiných tříd. V databázi jsou vztahy dědičnosti vytvářeny několika způsoby. **Návrhář o/R** podporuje koncept dědičnosti s jednou tabulkou, protože je často implementován v relačních systémech. Další informace naleznete v tématu [How to: Configure dědičnost pomocí návrháře o/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL dotazy

Třídy entit vytvořené v **/R Designer** jsou navržené pro použití s [dotazem integrovaným na jazyk (LINQ)](/dotnet/csharp/linq/). Další informace naleznete v tématu [How to: Query for Information](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oddělit generovaný kód třídy DataContext a entity do různých oborů názvů

**Návrhář o/R** poskytuje **obor názvů kontextu** a vlastnosti **oboru názvů entit** v <xref:System.Data.Linq.DataContext> . Tyto vlastnosti určují, do kterého oboru názvů se <xref:System.Data.Linq.DataContext> kód třídy a tříd entit generuje. Ve výchozím nastavení jsou tyto vlastnosti prázdné a <xref:System.Data.Linq.DataContext> třídy entit a jsou generovány do oboru názvů aplikace. Chcete-li vygenerovat kód do jiného oboru názvů, než je obor názvů aplikace, zadejte hodnotu do pole **obor názvů kontextu** a/nebo vlastnosti **oboru názvů entit** .

## <a name="reference-content"></a>Vytváření odkazů na obsah

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Viz také

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Nejčastější dotazy (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
