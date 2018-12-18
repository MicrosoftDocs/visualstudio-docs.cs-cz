---
title: Přístup k datům a nástroje
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e31eeaf3061968cfa916d2ec5a0d0e522b9f6ebb
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159526"
---
# <a name="access-data-in-visual-studio"></a>Přístup k datům v sadě Visual Studio

V sadě Visual Studio můžete vytvářet aplikace, které se připojují k datům v téměř jakoukoli databázový produkt nebo službu, v libovolném formátu, kdekoli – v místním počítači, v místní síti, nebo veřejné, privátní nebo hybridní cloud.

Pro aplikace v jazyce JavaScript, Python, PHP, Ruby nebo C++ můžete připojit k datům stejným způsobem jako cokoli jiného, získání knihovny a psaní kódu. Pro aplikace .NET Visual Studio poskytuje nástroje, které vám umožní prozkoumat zdroje dat, vytvářet modely objektů k ukládání a manipulaci s daty v paměti a vytvoření vazby dat na uživatelské rozhraní. Microsoft Azure poskytuje sady SDK pro .NET, Java, Node.js, PHP, Python, Ruby a mobilní aplikace a nástroje v sadě Visual Studio pro připojení k Azure Storage.

Následující seznamy shrnují jenom některé z mnoha systémů databáze a úložišť, se dají ze sady Visual Studio. [Microsoft Azure](https://azure.microsoft.com/) nabídky jsou datové služby, které zahrnují zřizování a správu podkladové úložiště. **Vývoj pro Azure** úlohy v [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) umožňuje pracovat s úložišti dat Azure přímo ze sady Visual Studio.

![Úloha vývoj pro Azure](media/azure-development-workload.png)

Většinu ostatních SQL a NoSQL databáze produktů, které jsou zde uvedeny, je možné hostovat na místním počítači, v místní síti nebo v Microsoft Azure na virtuálním počítači. Pokud hostujete databáze ve virtuálním počítači Microsoft Azure, jste zodpovědného za správu samotná databáze.

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- Storage (objekty BLOB, tabulky, fronty, soubory)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- a další...

**SQL**

- SQL Server 2005 – 2016 (včetně Express a LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- a další...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabáze
- OrientDB |
- RavenDB
- VelocityDB
- a další...

Mnoho dodavatelů databáze a třetí strany nepodporují integraci s Visual Studio pomocí balíčků NuGet. Můžete prozkoumat nabídky na nuget.org nebo prostřednictvím aplikaci Správce balíčků NuGet v sadě Visual Studio (**nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet Balíčky pro řešení**). Produkty databáze můžete integrovat s aplikací Visual Studio jako rozšíření. Tyto nabídky v aplikaci Visual Studio Marketplace můžete procházet tak, že přejdete do **nástroje**, **rozšíření a aktualizace** a následným výběrem **Online** v levém podokně Dialogové okno. Další informace najdete v tématu [kompatibilní databázové systémy pro sadu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Rozšířená podpora pro SQL Server 2005 skončila 12. dubna 2016. Neexistuje žádná záruka, že data tools v sadě Visual Studio 2015 a novější budou fungovat s SQL Server 2005 po tomto datu. Další informace najdete v tématu [oznámení ukončení podpory pro SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Jazyky rozhraní .NET

Všechny .NET přístup k datům, včetně v .NET Core, vychází z technologie ADO.NET, sadu tříd, který definuje rozhraní pro přístup k jakýkoli druh zdroje dat, relačních i nerelačních. Visual Studio obsahuje několik nástrojů a návrhářů, které pracují s ADO.NET připojení k databázím, vám usnadní pracuje s daty a prezentovat uživateli. Dokumentace v této části popisuje, jak pomocí těchto nástrojů. Také můžete programovat přímo proti objekty příkazů ADO.NET. Další informace o přímé volání rozhraní API technologie ADO.NET naleznete v tématu [ADO.NET](/dotnet/framework/data/adonet/index).

Dokumentace k přístupu k datům související s technologií ASP.NET, naleznete v tématu [práce s daty](https://www.asp.net/web-forms/overview/presenting-and-managing-data) na webu ASP.NET. Kurz týkající se používá nástroj Entity Framework s architekturou ASP.NET MVC, naleznete v tématu [Začínáme s Entity Framework 6 Code First pomocí MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Univerzální aplikace pro platformu Windows (UPW) v jazyce C# nebo Visual Basic můžete použít Microsoft Azure SDK pro .NET pro přístup k Azure Storage a dalšími službami Azure. Třída Windows.Web.HttpClient umožňuje komunikaci se všemi službami, RESTful. Další informace najdete v tématu [jak se připojit k serveru HTTP pomocí Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Doporučený postup pro ukládání dat v místním počítači, je použít SQLite, která běží ve stejném procesu jako aplikace. Pokud vrstvu objektově relační mapování (ORM) je potřeba, můžete použít Entity Framework. Další informace najdete v tématu [přístup k datům](/windows/uwp/data-access/index) v Centru pro vývojáře Windows.

Pokud se připojujete ke službám Azure, je nutné stáhnout nejnovější [sady Azure SDK tools](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Zprostředkovatelé dat

Aby databáze mohla být použitelné v ADO.NET, musí mít vlastní *zprostředkovatele dat ADO.NET* nebo jinak musí vystavit rozhraní ODBC nebo Oledb. Společnost Microsoft poskytuje [seznam zprostředkovatele dat ADO.NET](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) pro produkty SQL Server, jakož i rozhraní ODBC a OLE DB poskytovatele.

### <a name="data-modeling"></a>Modelování dat

V rozhraní .NET máte tři možnosti pro modelování a manipulace s daty v paměti, po jejím načtení ze zdroje dat:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) preferované technologie Microsoft ORM. Můžete ho programovat proti relačních dat jako první třídy objektů .NET. Pro nové aplikace je třeba výchozí první volbou při je vyžadován model. Vyžaduje vlastní podporu – od podkladového zprostředkovatele ADO.NET.

[Technologie LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) objektově relační Mapovač starší generace. Funguje dobře pro méně složité scénáře, ale již není v aktivním vývoji.

[Datové sady](../data-tools/dataset-tools-in-visual-studio.md) nejstarší tří technologií modelování. Je určená primárně pro rychlý vývoj aplikací "formy nad daty", ve kterých nejsou zpracování obrovské objemy dat nebo provádění složitých dotazů nebo transformací. Objekt datové sady se skládá z objektu DataTable a řádek dat objektů, které logicky mnohem víc než objektů .NET vypadat podobně jako objekty databáze SQL. Pro poměrně jednoduchá aplikace založené na SQL zdroje dat datové sady stále může být dobrou volbou.

Neexistuje žádný požadavek k používání některé z těchto technologií. V některých případech, zejména v případě, že je nejdůležitější, výkon jednoduše vám pomůže objektu DataReader čtení z databáze a zkopírujte hodnoty, které je třeba do objektu kolekce, jako je například seznam\<T >.

## <a name="native-c"></a>Nativní kód C++

Používejte aplikací v jazyce C++, které se připojují k systému SQL Server [Microsoft® ODBC Driver 13.1 pro SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) ve většině případů. Pokud jsou propojené servery, je nezbytné OLE DB a k tomu použijete [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Ostatní databáze přístupné prostřednictvím [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) nebo přímo ovladače OLE DB. ODBC je aktuální databáze standard rozhraní, ale většina databázových systémů poskytují vlastní funkce, která není přístupná přes rozhraní ODBC. OLE DB je starou technologií přístupu k datům modelu COM, který je stále podporovány, ale nedoporučuje se u nových aplikací. Další informace najdete v tématu [přístup k datům v jazyce Visual C++](/cpp/data/data-access-in-cpp).

Můžete použít programy v jazyce C++, které využívají služby REST [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Programy v jazyce C++, které fungují s Microsoft Azure Storage můžete použít [Microsoft Azure Storage Client](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Modelování dat&mdash;sady Visual Studio neposkytuje vrstvu ORM pro jazyk C++. [TYPU](https://www.codesynthesis.com/products/odb/) je oblíbený open source ORM pro jazyk C++.

Další informace o připojení k databázím z aplikací v jazyce C++, naleznete v tématu [sady Visual Studio data tools pro C++](../data-tools/visual-studio-data-tools-for-cpp.md). Další informace o starší verze technologií přístupu k datům Visual C++, naleznete v tématu [přístup k datům](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript v sadě Visual Studio](/scripting/javascript/javascript-language-reference) je prvotřídní jazyk pro vytváření aplikací pro různé platformy, aplikací pro UWP, cloudové služby, weby a webové aplikace. Bower, Grunt, Gulp, npm a NuGet v sadě Visual Studio můžete použít k instalaci vašich oblíbených knihoven JavaScriptu a databáze produktů. Připojení k úložišti Azure a službám stažením sady SDK z [web Azure](https://azure.microsoft.com/). Edge.js je knihovna, která se připojuje ke zdrojům dat ADO.NET JavaScript na straně serveru (Node.js).

## <a name="python"></a>Python

Nainstalujte [podpora Pythonu v sadě Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) k vytvoření aplikací v Pythonu. Dokumentace k Azure má několik kurzy o připojení k datům, včetně následujících:

- [Django a SQL Database v Azure](/azure/app-service/app-service-web-get-started-python)
- [Django a MySQL v Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Práce s [objekty BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), [soubory](/azure/storage/files/storage-python-how-to-use-file-storage), [fronty](/azure/storage/queues/storage-python-how-to-use-queue-storage), a [tabulky (Cosmo databáze)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Související témata

[Platforma Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;obsahuje úvod k inteligentnímu cloudu Microsoft, včetně sady Cortana Analytics Suite a podpory pro Internet věcí.

[Microsoft Azure Storage](/azure/storage/)&mdash;popisuje Azure Storage a jak vytvářet aplikace pomocí Azure BLOB, tabulky, fronty a soubory.

[Azure SQL Database](/azure/sql-database/)&mdash;popisuje, jak se připojit ke službě Azure SQL Database, relační databáze jako služba.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;popisuje nástroje, které usnadňují návrh, průzkum, testování a nasazení aplikace připojené ke data a databáze.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;popisuje architekturu ADO.NET a jak spravovat data aplikací a využívat zdroje dat a XML pomocí třídy rozhraní ADO.NET.

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;popisuje způsob vytváření datových aplikací, které umožňují vývojářům programovat proti Koncepční model místo přímo na relační databázi.

[4.5 služby WCF Data](/dotnet/framework/data/wcf/index)&mdash;popisuje způsob použití [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] pro nasazení datových služeb na webu nebo intranetu, které implementují [Open Data Protocol (OData)](https://www.odata.org/).

[Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)&mdash;obsahuje odkazy na témata, která popisují, jak fungují data v řešeních pro systém Office. To zahrnuje informace o programování orientovaném na schéma, ukládání dat do mezipaměti a přístupu k datům na straně serveru.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;popisuje možnosti dotazu, integrované do jazyka C# a Visual Basic a společný model pro dotazování na relačních databází, dokumenty XML, datové sady a kolekce v paměti.

[Nástroje XML v sadě Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;Tento článek popisuje práci s funkcí rozhraní .NET Framework XML dat, ladění XSLT, XML a architektura dotaz XML.

[Dokumenty a Data XML](/dotnet/standard/data/xml/index)&mdash;přehled komplexního a integrovaného sadu tříd, které pracují s dokumenty XML a data v rozhraní .NET Framework.
