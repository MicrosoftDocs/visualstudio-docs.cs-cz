---
title: Přístup k datům
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 158bc4c2fc7734957c7d3e946390ab1339a322ba
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299432"
---
# <a name="accessing-data-in-visual-studio"></a>Přístup k datům v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio můžete vytvářet aplikace, které se připojují k datům v téměř jakoukoli databázový produkt nebo službu, v libovolném formátu, kdekoli – v místním počítači, v místní síti, nebo veřejné, privátní nebo hybridní cloud.

 Pro aplikace v jazyce JavaScript, Python, PHP, Ruby nebo C++ můžete připojit k datům stejným způsobem jako cokoli jiného, získání knihovny a psaní kódu. Pro aplikace .NET Visual Studio poskytuje nástroje, které vám umožní prozkoumat zdroje dat, vytvářet modely objektů k ukládání a manipulaci s daty v paměti a vytvoření vazby dat na uživatelské rozhraní.     Microsoft Azure poskytuje sady SDK pro .NET, Java, Node.js, PHP, Python, Ruby a mobilní aplikace a nástroje v sadě Visual Studio pro připojení k Azure Storage.

 Následující seznamy shrnují jenom některé z mnoha systémů databáze a úložišť, se dají ze sady Visual Studio. [Microsoft Azure](https://azure.microsoft.com/) nabídky jsou datové služby, které zahrnují zřizování a správu podkladové úložiště.  [Nástroje Azure pro Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) je volitelná součást, která umožňuje pracovat s úložišti dat Azure přímo ze sady Visual Studio. Většinu ostatních SQL a NoSQL databáze produktů, které jsou zde uvedeny, je možné hostovat na místním počítači, v místní síti nebo v Microsoft Azure na virtuálním počítači. V tomto scénáři jste odpovědní za správu samotná databáze.

 **Microsoft Azure**

||||
|-|-|-|
|SQL Database|DocumentDB|Storage (objekty BLOB, tabulky, fronty, soubory)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

 a další...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016, včetně Express LocalDB|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 a další...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabáze|OrientDB|RavenDB|
|VelocityDB|||

 a další...

 Mnoho dodavatelů databáze a třetí strany nepodporují integraci s Visual Studio pomocí balíčků NuGet. Můžete prozkoumat nabídky na nuget.org nebo prostřednictvím aplikaci Správce balíčků NuGet v sadě Visual Studio (**nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet Balíčky pro řešení**). Produkty databáze můžete integrovat s aplikací Visual Studio jako rozšíření.   Tyto nabídky v Galerii Visual Studio můžete procházet tak, že přejdete do **nástroje** > **rozšíření a aktualizace** a následným výběrem **Online** vlevo podokně dialogového okna.  Další informace najdete v tématu [instalace systémů databází, nástroje a ukázky](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Rozšířená podpora pro SQL Server 2005 skončila 12. dubna 2016.   Neexistuje žádná záruka, že data tools v sadě Visual Studio 2015 a novější budou fungovat s SQL Server 2005 po tomto datu. Další informace najdete v tématu [oznámení ukončení podpory pro SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Jazyky rozhraní .NET
 Všechny .NET přístup k datům, včetně v .NET Core, vychází z technologie ADO.NET, sadu tříd, který definuje rozhraní pro přístup k jakýkoli druh zdroje dat, relačních i nerelačních. Visual Studio obsahuje několik nástrojů a návrhářů, které pracují s ADO.NET připojení k databázím, vám usnadní pracuje s daty a prezentovat uživateli. Dokumentace v této části popisuje, jak pomocí těchto nástrojů. Také můžete programovat přímo proti objekty příkazů ADO.NET. Další informace o přímé volání rozhraní API technologie ADO.NET naleznete v tématu [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) v knihovně MSDN.

 Dokumentace k přístupu k datům výslovně související s technologií ASP.NET, naleznete v tématu [práce s daty](https://docs.microsoft.com/aspnet/web-forms/overview/presenting-and-managing-data/) na webu ASP.NET. Kurz týkající se používá nástroj Entity Framework s architekturou ASP.NET MVC, naleznete v tématu [Začínáme s Entity Framework 6 Code First pomocí MVC 5](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Univerzální aplikace pro platformu Windows (UPW) v jazyce C# nebo Visual Basic můžete použít Microsoft Azure SDK pro .NET pro přístup k Azure Storage a dalšími službami Azure. Třída Windows.Web.HttpClient umožňuje komunikaci se všemi službami, RESTful. Další informace najdete v tématu [jak se připojit k serveru HTTP pomocí Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Doporučený postup pro ukládání dat v místním počítači, je použít SQLite, která běží ve stejném procesu jako aplikace. Pokud vrstvu objektově relační mapování (ORM) je potřeba, můžete použít Entity Framework. Další informace najdete v tématu [přístup k datům](https://msdn.microsoft.com/windows/uwp/data-access/index) v Centru pro vývojáře Windows.

 Pokud se připojujete ke službám Azure, je nutné stáhnout nejnovější [sady Azure SDK tools](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Zprostředkovatelé dat
 Aby databáze mohla být použitelné v ADO.NET, musí mít vlastní *zprostředkovatele dat ADO.NET* nebo jinak musí vystavit rozhraní ODBC nebo Oledb. Společnost Microsoft poskytuje [seznam zprostředkovatele dat ADO.NET](https://msdn.microsoft.com/data/dd363565) pro produkty SQL Server, jakož i rozhraní ODBC a OLE DB poskytovatele.

#### <a name="data-modeling"></a>Modelování dat
 V rozhraní .NET máte tři možnosti pro modelování a manipulace s daty v paměti, po jejím načtení ze zdroje dat:

 Preferované technologie Microsoft ORM rozhraní Entity Framework. Můžete ho programovat proti relačních dat jako první třídy objektů .NET. Pro nové aplikace je třeba výchozí první volbou při je vyžadován model. Vyžaduje vlastní podporu – od podkladového zprostředkovatele ADO.NET.

 Technologie LINQ to SQL objektově relační Mapovač starší generace. Funguje dobře pro méně složité scénáře, ale již není v aktivním vývoji.

 Datové sady nejstarší tří technologií modelování. Je určená primárně pro rychlý vývoj aplikací "formy nad daty", ve kterých nejsou zpracování obrovské objemy dat nebo provádění složitých dotazů nebo transformací. Objekt datové sady se skládá z objektu DataTable a řádek dat objektů, které logicky mnohem víc než objektů .NET vypadat podobně jako objekty databáze SQL. Pro poměrně jednoduchá aplikace založené na SQL zdroje dat datové sady stále může být dobrou volbou.

 Neexistuje žádný požadavek k používání některé z těchto technologií. V některých případech, zejména v případě, že je nejdůležitější, výkon jednoduše vám pomůže objektu DataReader čtení z databáze a zkopírujte hodnoty, které je třeba do objektu kolekce, jako je například seznam\<T >.

### <a name="native-c"></a>Nativní kód C++
 Používejte aplikací v jazyce C++, které se připojují k systému SQL Server [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Ostatní databáze přístupné prostřednictvím [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) nebo přímo ovladače OLE DB. ODBC je aktuální databáze standard rozhraní, ale většina databázových systémů poskytují vlastní funkce, která není přístupná přes rozhraní ODBC.  OLE DB je starou technologií přístupu k datům modelu COM, který je stále podporovány, ale nedoporučuje se u nových aplikací.  Další informace najdete v tématu [přístup k datům](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 Můžete použít programy v jazyce C++, které využívají služby REST [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

 Programy v jazyce C++, které fungují s Microsoft Azure Storage můžete použít [Microsoft Azure Storage Client](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modelování dat
 Visual Studio neposkytuje vrstvu ORM pro jazyk C++.  [TYPU](https://www.codesynthesis.com/products/odb/) je oblíbený open source ORM pro jazyk C++.

 Další informace o starší verze technologií přístupu k datům Visual C++, naleznete v tématu [přístup k datům](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [JavaScript v sadě Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) je prvotřídní jazyk pro vytváření aplikací pro různé platformy, aplikací pro UWP, cloudové služby, weby a webové aplikace. Bower, Grunt, Gulp, npm a NuGet v sadě Visual Studio můžete použít k instalaci vašich oblíbených knihoven JavaScriptu a databáze produktů. Připojení k úložišti Azure a službám stažením sady SDK z [web Azure](https://azure.microsoft.com/).  Edge.js je knihovna, která se připojuje ke zdrojům dat ADO.NET JavaScript na straně serveru (Node.js).

### <a name="python"></a>Python
 Nainstalujte [Python Tools for Visual Studio](http://microsoft.github.io/PTVS/) spolu s vaší oblíbené platformě Python k vytvoření aplikací CPython, IronPython (.NET).  Nástroje Pythonu pro Visual Studio web má několik kurzy o připojení k datům, včetně [Django a SQL Database v Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django a MySQL v Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) a [Bottle a MongoDB v Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>V tomto oddílu
 [Instalace systémů databází, nástroje a ukázky](../data-tools/installing-database-systems-tools-and-samples.md) pojednává o tom, jak získat databáze produkty a rozšíření sady Visual Studio nebo ovladače, které je podporují a kde najít ukázkové databáze pro služby experimentování ve službě a výukové účely.

 [Visual Studio data tools pro .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) popisuje způsob použití okna nástrojů sady Visual Studio k připojení ke zdrojům dat, vytvoření datových sad a modelů Entity Framework a data svázat ovládací prvky uživatelského rozhraní.

## <a name="related-topics"></a>Související témata
 [Data, zařízení a Analytics](https://msdn.microsoft.com/data-and-devices) obsahuje úvod k inteligentnímu cloudu Microsoft, včetně sady Cortana Analytics Suite a podpory pro Internet věcí.

 [Microsoft Azure Storage](/azure/storage/) popisuje Azure Storage a jak vytvářet aplikace pomocí Azure BLOB, tabulky, fronty a soubory.

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) popisuje, jak se připojit ke službě Azure SQL Database, relační databáze jako služba.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) popisuje nástroje, které usnadňují návrh, průzkum, testování a nasazení aplikace připojené ke data a databáze.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) popisuje architekturu ADO.NET a jak spravovat data aplikací a využívat zdroje dat a XML pomocí třídy rozhraní ADO.NET.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) popisuje způsob vytváření datových aplikací, které umožňují vývojářům programovat proti Koncepční model místo přímo na relační databázi.

 [4.5 služby WCF Data](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) popisuje způsob použití [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] pro nasazení datových služeb na webu nebo intranetu, které implementují [Open Data Protocol (OData)](https://go.microsoft.com/fwlink/?LinkID=182204).

 [Data v řešeních pro systém Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) obsahuje odkazy na témata, která popisují, jak fungují data v řešeních pro systém Office. To zahrnuje informace o programování orientovaném na schéma, ukládání dat do mezipaměti a přístupu k datům na straně serveru.

 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) popisuje do integrované možnosti dotazu C# a Visual Basic a společný model pro dotazování na relačních databází, dokumenty XML, datové sady a kolekce v paměti.

 [Nástroje XML v sadě Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Tento článek popisuje práci s funkcí rozhraní .NET Framework XML dat, ladění XSLT, XML a architektura dotaz XML.

 [Dokumenty a Data XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) přehled komplexního a integrovaného sadu tříd, které pracují s dokumenty XML a data v rozhraní .NET Framework.
