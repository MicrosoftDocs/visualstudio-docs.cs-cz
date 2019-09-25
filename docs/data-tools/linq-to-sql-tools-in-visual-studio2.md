---
title: Přehled O/R Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9511f2101c8dbac0ae8a9ba9e08f9a4f22067c3a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252929"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Nástroje LINQ to SQL v sadě Visual Studio

Technologie LINQ to SQL byl první objektově relační mapování technologie vydané společností Microsoft. Dobře funguje v základní scénáře a jsou nadále podporované v sadě Visual Studio, ale už se aktivně vyvíjí. Použití LINQ to SQL při zachování starší verze aplikací, který je již používán, nebo jednoduché aplikace, které používají SQL Server a nevyžadují žádná mapování více tabulek. Obecně platí nové aplikace by měly používat Entity Framework, pokud je nutné použít vrstvu objektově relační Mapovač.

V sadě Visual Studio, je vytvoření tříd LINQ to SQL, které představují tabulky SQL s použitím **Návrhář relací objektů** (**O/R Designer**).

**O/R Designer** má dva různé oblasti na svém povrchu návrhu: v podokně entity na levé straně a metody podokno na pravé straně. V podokně entity je hlavní návrhovou plochu, zobrazující tříd entit, přidružení a hierarchie dědičnosti. Podokno metody je na návrhovou plochu, zobrazující <xref:System.Data.Linq.DataContext> metody, které jsou mapovány na uložené procedury a funkce.

**O/R Designer** poskytuje vizuální návrhová plocha pro vytváření [technologie LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) tříd entit a přidružení (relace), které jsou založeny na objekty v databázi. Jinými slovy **O/R Designer** vytvoří objektový model v aplikaci, která mapuje pro objekty v databázi. Zároveň se vygeneruje silného typu <xref:System.Data.Linq.DataContext> , který odesílá i přijímá data mezi třídami entit a databáze. **O/R Designer** také přiřazuje funkce mapě uložených procedur a funkcí <xref:System.Data.Linq.DataContext> metody pro vrácení dat a naplnění tříd entit. Nakonec **O/R Designer** umožňuje návrh vztahy dědičnosti mezi třídami entit.

## <a name="open-the-or-designer"></a>Otevření Návrháře relací objektů

Chcete-li přidat LINQ do SQL entity modelu do projektu, zvolte **projektu** > **přidat novou položku**a pak vyberte **třídy LINQ to SQL** ze seznamu položek projektu:

![Třídy LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio vytvoří *dbml* soubor a přidá ji do vašeho řešení. Toto je soubor mapování XML a jeho soubory související kód.

![LINQ na třídy SQL v Průzkumníku řešení](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Když vyberete *dbml* soubor, sada Visual Studio zobrazí **O/R Designer** povrch, který vám umožní vizuálně vytvářet model. Následující obrázek znázorňuje Návrháře po Northwind `Customers` a `Orders` tabulky byl přetažen z **Průzkumníka serveru**. Poznámka: relace mezi tabulkami.

![Technologie LINQ to SQL Návrháře](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R Designer** je jednoduchý objekt relační Mapovač, protože podporuje pouze relace mapování 1:1. Jinými slovy třídu entity může mít pouze mapování 1:1 relaci s databázové tabulky nebo zobrazení. Komplexní mapování, jako je například mapování třídu entity do tabulky připojené k doméně, není podporována. použití rozhraní Entity Framework pro komplexní mapování. Kromě toho Návrhář je generátor kódu jednosměrná. To znamená, že se projeví pouze změny provedené na plochu návrháře do souboru kódu. Ruční změny do souboru kódu se neprojeví v **O/R Designer**. Všechny změny, které můžete provést ručně v souboru kódu jsou přepsány při návrháři se uloží a kód vygenerován znovu. Informace o tom, jak přidat uživatelský kód a jak rozšiřuje třídy generované **návrhářem O/R**, naleznete v [tématu How to: Rozšíří kód vygenerovaný návrhářem](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)O/R.

## <a name="create-and-configure-the-datacontext"></a>Vytvoření a konfigurace DataContext

Po přidání **třídy LINQ to SQL** položky do projektu a otevřete **O/R Designer**, prázdný návrhové ploše představuje prázdný <xref:System.Data.Linq.DataContext> jste připravení nakonfigurovat. <xref:System.Data.Linq.DataContext> má nakonfigurovanou připojení na základě informací poskytnutých první položka, která je přetažena na návrhovou plochu. Proto <xref:System.Data.Linq.DataContext> je nakonfigurován s použitím informací o připojení z první položky na návrhové ploše. Další informace o <xref:System.Data.Linq.DataContext> třídy viz [metod DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Vytvoření tříd entit, která je namapována na databázové tabulky a zobrazení

Můžete vytvořit přetažením databázových tabulek a zobrazení z namapované na tabulky a zobrazení tříd entit **Průzkumníka serveru** nebo **Průzkumník databáze** na **O/R Designer**. Jak je uvedeno v předchozí části <xref:System.Data.Linq.DataContext> má nakonfigurovanou připojení na základě informací poskytnutých první položka, která je přetažena na návrhovou plochu. Pokud je přidána následující položky, který používá jiné připojení do **O/R Designer**, můžete změnit na připojení pro <xref:System.Data.Linq.DataContext>. Další informace najdete v tématu [jak: Vytvoří LINQ to SQL třídy mapované na tabulky a zobrazení (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Vytvoření metod DataContext, které volají uložených procedur a funkcí

Můžete vytvořit <xref:System.Data.Linq.DataContext> metody, které volají (jsou namapovány na) uložené procedury a funkce přetažením z **Průzkumníka serveru** nebo **Průzkumník databáze** na **Návrháře relací objektů** . Uložené procedury a funkce jsou přidány do **O/R Designer** jako metody <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Při přetažení uložených procedur a funkcí z **Průzkumníka serveru** nebo **Průzkumník databáze** na **O/R Designer**, návratový typ vytvořeného <xref:System.Data.Linq.DataContext> Metoda se liší v závislosti na tom, kde je vyřadit položku. Další informace najdete v tématu [metod DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurace DataContext pro uložení dat mezi třídami entit a databází pomocí uložených procedur

Jak bylo uvedeno dříve, můžete vytvořit <xref:System.Data.Linq.DataContext> metody, které volají uložených procedur a funkcí. Kromě toho můžete také přiřadit uložené procedury, které jsou používány pro výchozí LINQ to SQL chování při spuštění, které provádí vkládání, aktualizace a odstraňování. Další informace najdete v tématu [jak: Přiřaďte uložené procedury pro provádění aktualizací, vkládání a odstraňování (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Dědičnost a Návrháře relací objektů

Jako u jiných objektů třídy LINQ to SQL můžete použít dědičnosti a být odvozen od jiných tříd. V databázi vztahy dědičnosti vytvoří několika způsoby. **O/R Designer** podporují koncept dědičnosti jedné tabulky, jak často je implementován v relačních systémech. Další informace najdete v tématu [jak: Nakonfigurujte dědičnost pomocí návrháře](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)O/R.

## <a name="linq-to-sql-queries"></a>Dotazy LINQ to SQL

Tříd entit, které jsou vytvořené **O/R Designer** jsou určeny k použití s [Language-Integrated query (LINQ)](/dotnet/csharp/linq/). Další informace najdete v tématu [jak: Dotaz na informace](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Vygenerovaný kód třídy DataContext a entity rozdělit do různých oborech názvů

**O/R Designer** poskytuje **kontextu Namespace** a **Entity Namespace** vlastnosti <xref:System.Data.Linq.DataContext>. Tyto vlastnosti určují, jaký obor názvů <xref:System.Data.Linq.DataContext> a generování kódu entity třídy do. Ve výchozím nastavení, tyto vlastnosti jsou prázdné a <xref:System.Data.Linq.DataContext> a tříd entit, které jsou vygenerovány do oboru názvů aplikace. Ke generování kódu do oboru názvů, než je obor názvů aplikace, zadejte hodnotu do **kontextu Namespace** a/nebo **Entity Namespace** vlastnosti.

## <a name="reference-content"></a>Odkazování na obsah

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Nejčastější dotazy (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)