---
title: Nástroje LINQ to SQL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7c8a9d35f0f435ccbe336f366346f1ccb89c6072
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067470"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Nástroje LINQ to SQL v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Technologie LINQ to SQL byl první objektově relační mapování technologie vydané společností Microsoft. Dobře funguje v základní scénáře a jsou nadále podporované v sadě Visual Studio, ale už se aktivně vyvíjí. Použití LINQ to SQL při zachování starší verze aplikací, který je již používán, nebo jednoduché aplikace, které používají SQL Server a nevyžadují žádná mapování více tabulek. Obecně platí nové aplikace by měly používat Entity Framework, pokud je nutné použít vrstvu objektově relační Mapovač.

 V sadě Visual Studio, je vytvoření tříd LINQ to SQL, které představují tabulky SQL s použitím [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Má dva různé oblasti na svém povrchu návrhu: v podokně entity na levé straně a metody podokno na pravé straně. V podokně entity je hlavní návrhovou plochu, zobrazující tříd entit, přidružení a hierarchie dědičnosti. Podokno metody je na návrhovou plochu, zobrazující <xref:System.Data.Linq.DataContext> metody, které jsou mapovány na uložené procedury a funkce.

 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Poskytuje vizuální návrhová plocha pro vytváření [technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) tříd entit a přidružení (relace), které jsou založeny na objekty v databázi. Jinými slovy [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] slouží k vytvoření objektového modelu v aplikaci, která mapuje pro objekty v databázi. Zároveň se vygeneruje silného typu <xref:System.Data.Linq.DataContext> , který slouží k odesílání a přijímání dat mezi třídami entit a databáze. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Také přiřazuje funkce mapě uložených procedur a funkcí <xref:System.Data.Linq.DataContext> metody pro vrácení dat a naplnění tříd entit. Nakonec [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] umožňuje návrh vztahy dědičnosti mezi třídami entit.

## <a name="opening-the-or-designer"></a>Otevření Návrháře relací objektů
 Chcete-li přidat LINQ do SQL entity modelu do projektu, zvolte **projektu &#124; přidat novou položku** a klikněte na tlačítko **třídy LINQ to SQL** ze seznamu položek projektu:

 ![Třídy LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata třídy LINQ to SQL")

 Visual Studio vytvoří soubor .dbml a přidá ji do vašeho řešení. Toto je soubor mapování XML a jeho soubory související kód.

 ![Třídy technologie LINQ to SQL v Průzkumníku řešení](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata technologie LINQ to SQL třídy v Průzkumníku řešení")

 Při výběru souboru .dbml, zobrazí Visual Studio na plochu návrháře relací objektů, umožňující vizuální vytváření modelu. Následující obrázek znázorňuje Návrháře po tabulky Northwind zákazníci a objednávky byl přetažen z Průzkumníka serveru. Poznámka: relace mezi tabulkami.

 ![Technologie LINQ to SQL Návrhář](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Návrháře")

> [!IMPORTANT]
>  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Je jednoduchý objekt relační Mapovač, protože podporuje pouze relace mapování 1:1. Jinými slovy třídu entity může mít pouze mapování 1:1 relaci s databázové tabulky nebo zobrazení. Komplexní mapování, jako je například mapování třídu entity do tabulky připojené k doméně, není podporována. použití rozhraní Entity Framework pro komplexní mapování. Kromě toho Návrhář je generátor kódu jednosměrná. To znamená, že se projeví pouze změny provedené na plochu návrháře do souboru kódu. Ruční změny do souboru kódu se neprojeví v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Všechny změny, které můžete provést ručně v souboru kódu jsou přepsány při návrháři se uloží a kód vygenerován znovu. Informace o tom, jak přidat uživatelský kód a rozšíření třídy generované [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], naleznete v tématu [postupy: rozšíření kód generovaný návrhářem relací objektů](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Vytváření a konfiguraci DataContext
 Po přidání **třídy LINQ to SQL** položky do projektu a otevřete [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], prázdný návrhové ploše představuje prázdný <xref:System.Data.Linq.DataContext> jste připravení nakonfigurovat. <xref:System.Data.Linq.DataContext> má nakonfigurovanou připojení na základě informací poskytnutých první položka, která je přetažena na návrhovou plochu... Proto <xref:System.Data.Linq.DataContext> je nakonfigurován s použitím informací o připojení z první položky na návrhové ploše. Další informace o <xref:System.Data.Linq.DataContext> třídy viz [metod DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Vytvoření tříd entit, která je namapována na databázové tabulky a zobrazení
 Můžete vytvořit přetažením databázových tabulek a zobrazení z namapované na tabulky a zobrazení tříd entit **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Jak je uvedeno v předchozí části <xref:System.Data.Linq.DataContext> má nakonfigurovanou připojení na základě informací poskytnutých první položka, která je přetažena na návrhovou plochu. Pokud je přidána následující položky, který používá jiné připojení do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], můžete změnit na připojení pro <xref:System.Data.Linq.DataContext>. Další informace najdete v tématu [postupy: vytvoření třídy LINQ to SQL namapovaných na tabulky a zobrazení (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Vytvoření metod DataContext, které volají uložených procedur a funkcí
 Můžete vytvořit <xref:System.Data.Linq.DataContext> metody, které volají (jsou namapovány na) uložené procedury a funkce přetažením z **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Uložené procedury a funkce jsou přidány do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jako metody <xref:System.Data.Linq.DataContext>.

> [!NOTE]
>  Při přetažení uložených procedur a funkcí z **Průzkumníka serveru**/**Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], návratový typ vytvořeného <xref:System.Data.Linq.DataContext> metoda se liší v závislosti na tom, kde je vyřadit položku. Další informace najdete v tématu [metod DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurace DataContext pro uložení dat mezi třídami entit a databází pomocí uložených procedur
 Jak bylo uvedeno dříve, můžete vytvořit <xref:System.Data.Linq.DataContext> metody, které volají uložených procedur a funkcí. Kromě toho můžete také přiřadit uložené procedury, které lze použít pro výchozí [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] chování za běhu, který provádí vložení, aktualizace a odstranění. Další informace najdete v tématu [postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Dědičnost a Návrháře relací objektů
 Jiné objekty, jako jsou [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] dědičnost lze použít třídy a být odvozen od jiných tříd. V databázi vztahy dědičnosti vytvoří několika způsoby. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Podporují koncept dědičnosti jedné tabulky, jak často je implementován v relačních systémech. Další informace najdete v tématu [postupy: Konfigurace dědičnosti pomocí Návrháře relací objektů](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Dotazy LINQ to SQL
 Tříd entit, které jsou vytvořené [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jsou určeny k použití s [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Další informace najdete v tématu [postupy: dotaz na informace o](http://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oddělení generované DataContext a kód třídy Entity do různých oborech názvů
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Poskytuje **kontextu Namespace** a **Entity Namespace** vlastnosti <xref:System.Data.Linq.DataContext>. Tyto vlastnosti určují, jaký obor názvů <xref:System.Data.Linq.DataContext> a generování kódu entity třídy do. Ve výchozím nastavení, tyto vlastnosti jsou prázdné a <xref:System.Data.Linq.DataContext> a tříd entit, které jsou vygenerovány do oboru názvů aplikace. Ke generování kódu do oboru názvů, než je obor názvů aplikace, zadejte hodnotu do **kontextu Namespace** a/nebo **Entity Namespace** vlastnosti.

## <a name="in-this-section"></a>V tomto oddílu
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) vysvětluje co <xref:System.Data.Linq.DataContext> metody jsou a postupy jejich vytvoření.

 [Data třídy dědičnosti (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md) popisuje koncept dědičnosti jedné tabulky a jak je implementován v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Postupy: vytvoření LINQ na třídy SQL namapovaných na tabulky a zobrazení (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) popisuje postup vytvoření tříd entit, které jsou mapovány na tabulky a zobrazení v databázi.

 [Postupy: vytvoření přidružení (vztah) mezi třídy LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) popisuje, jak vytvořit relaci mezi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] tříd entit.

 [Postupy: Vytvoření metod DataContext namapovaných na uložené procedury a funkce (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) popisuje, jak vytvořit <xref:System.Data.Linq.DataContext> metody, které běží uloženými procedurami nebo funkcemi, pokud jsou volány.

 [Postupy: přiřazení uložených procedur za účelem aktualizace, vložení a odstranění (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) popisuje postup konfigurace <xref:System.Data.Linq.DataContext> při ukládání dat z entity pouze pomocí uložených procedur třídy zpět do databáze.

 [Postupy: Změna návratového typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) popisuje, jak nastavit návratový typ <xref:System.Data.Linq.DataContext> metoda typu třídu entity nebo automaticky generovaný typ, který vytvořil Návrháře relací objektů.

 [Postupy: přidávání ověřování do tříd entit](../data-tools/how-to-add-validation-to-entity-classes.md) popisuje, jak generovat částečné metody, které umožňují přidání kódu během změny vlastností a aktualizace entity třídy.

 [Postupy: zapnutí a vypnutí (O/R Designer) pluralizace](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) popisuje, jak zapnout a vypnout automatické přejmenování tříd, které jsou přidány do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Postupy: Konfigurace dědičnosti pomocí Návrháře relací objektů](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) popisuje postup konfigurace dědičnosti jedné tabulky s použitím tříd entit [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Postupy: rozšíření kód generovaný návrhářem relací objektů](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) popisuje, jak a kde přidat kód, který se přepíše při změny objektů na O/R Designer znovu vygenerovat kód.

 [Návod: Vytvoření LINQ na třídy SQL děděním pomocí jedné tabulky (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) poskytuje podrobné pokyny ke konfiguraci dědičnosti jedné tabulky s použitím tříd entit [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Návod: Přizpůsobení vložit, aktualizovat a odstraňovat chování tříd entit](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) poskytuje podrobné pokyny ke konfiguraci <xref:System.Data.Linq.DataContext> při ukládání dat z entity pouze pomocí uložených procedur třídy zpět do databáze.

## <a name="reference-content"></a>Odkazování na obsah
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Viz také
 [Visual Studio data tools pro .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [– nejčastější dotazy](http://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [technologie LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
