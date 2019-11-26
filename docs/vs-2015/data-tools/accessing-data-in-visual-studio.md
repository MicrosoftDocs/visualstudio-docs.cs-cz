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

 Následující seznamy shrnují jenom některé z mnoha systémů databáze a úložišť, se dají ze sady Visual Studio. Nabídky [Microsoft Azure](https://azure.microsoft.com/) jsou datové služby, které zahrnují všechna zřizování a správu základního úložiště dat.  [Nástroje Azure pro Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) jsou volitelnou komponentou, která umožňuje pracovat s úložišti dat Azure přímo ze sady Visual Studio. Většinu ostatních SQL a NoSQL databáze produktů, které jsou zde uvedeny, je možné hostovat na místním počítači, v místní síti nebo v Microsoft Azure na virtuálním počítači. V tomto scénáři jste odpovědní za správu samotná databáze.

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

 Mnoho dodavatelů databáze a třetí strany nepodporují integraci s Visual Studio pomocí balíčků NuGet. Nabídky můžete prozkoumat v nuget.org nebo pomocí Správce balíčků NuGet v aplikaci Visual Studio (**nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**). Produkty databáze můžete integrovat s aplikací Visual Studio jako rozšíření.   Tyto nabídky můžete procházet v galerii sady Visual Studio tak, že přejdete na **nástroje** > **rozšíření a aktualizace** a pak vyberete **online** v levém podokně dialogového okna.  Další informace najdete v tématu [instalace databázových systémů, nástrojů a ukázek](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Rozšířená podpora pro SQL Server 2005 skončila 12. dubna 2016.   Neexistuje žádná záruka, že data tools v sadě Visual Studio 2015 a novější budou fungovat s SQL Server 2005 po tomto datu. Další informace najdete v tématu [oznámení ukončení podpory SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Jazyky rozhraní .NET
 Všechny .NET přístup k datům, včetně v .NET Core, vychází z technologie ADO.NET, sadu tříd, který definuje rozhraní pro přístup k jakýkoli druh zdroje dat, relačních i nerelačních. Visual Studio obsahuje několik nástrojů a návrhářů, které pracují s ADO.NET připojení k databázím, vám usnadní pracuje s daty a prezentovat uživateli. Dokumentace v této části popisuje, jak pomocí těchto nástrojů. Také můžete programovat přímo proti objekty příkazů ADO.NET. Další informace o přímém volání rozhraní API ADO.NET najdete v tématu [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) v knihovně MSDN.

 Dokumentaci k přístupu k datům konkrétně související s ASP.NET najdete v tématu [práce s daty](https://docs.microsoft.com/aspnet/web-forms/overview/presenting-and-managing-data/) na webu ASP.NET. Kurz použití Entity Framework s ASP.NET MVC najdete v článku [Začínáme s Entity Framework 6 Code First pomocí MVC 5](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Univerzální aplikace pro platformu Windows (UPW) v jazyce C# nebo Visual Basic můžete použít Microsoft Azure SDK pro .NET pro přístup k Azure Storage a dalšími službami Azure. Třída Windows.Web.HttpClient umožňuje komunikaci se všemi službami, RESTful. Další informace najdete v tématu [jak se připojit k serveru HTTP pomocí Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Doporučený postup pro ukládání dat v místním počítači, je použít SQLite, která běží ve stejném procesu jako aplikace. Pokud vrstvu objektově relační mapování (ORM) je potřeba, můžete použít Entity Framework. Další informace najdete v tématu [přístup k datům](https://msdn.microsoft.com/windows/uwp/data-access/index) v centru pro vývojáře v systému Windows.

 Pokud se připojujete ke službám Azure, nezapomeňte si stáhnout nejnovější [nástroje Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Zprostředkovatelé dat
 Aby databáze byla v ADO.NET spotřební, musí mít vlastního *poskytovatele dat ADO.NET* nebo jinak musí vystavit rozhraní ODBC nebo OLE DB. Společnost Microsoft poskytuje [seznam zprostředkovatelů ADO.NET dat](https://msdn.microsoft.com/data/dd363565) pro produkty SQL Server a také pro poskytovatele rozhraní ODBC a OLE DB.

#### <a name="data-modeling"></a>Modelování dat
 V rozhraní .NET máte tři možnosti pro modelování a manipulace s daty v paměti, po jejím načtení ze zdroje dat:

 Preferované technologie Microsoft ORM rozhraní Entity Framework. Můžete ho programovat proti relačních dat jako první třídy objektů .NET. Pro nové aplikace je třeba výchozí první volbou při je vyžadován model. Vyžaduje vlastní podporu – od podkladového zprostředkovatele ADO.NET.

 Technologie LINQ to SQL objektově relační Mapovač starší generace. Funguje dobře pro méně složité scénáře, ale již není v aktivním vývoji.

 Datové sady nejstarší tří technologií modelování. Je určená primárně pro rychlý vývoj aplikací "formy nad daty", ve kterých nejsou zpracování obrovské objemy dat nebo provádění složitých dotazů nebo transformací. Objekt datové sady se skládá z objektu DataTable a řádek dat objektů, které logicky mnohem víc než objektů .NET vypadat podobně jako objekty databáze SQL. Pro poměrně jednoduchá aplikace založené na SQL zdroje dat datové sady stále může být dobrou volbou.

 Neexistuje žádný požadavek k používání některé z těchto technologií. V některých případech, zejména v případě, že je výkon kritický, můžete jednoduše použít objekt DataReader ke čtení z databáze a zkopírovat hodnoty, které potřebujete do objektu kolekce, jako je například seznam\<T >.

### <a name="native-c"></a>Nativní kód C++
 C++aplikace, které se připojují k SQL Server by měly používat [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). K ostatním databázím můžete přistupovat přímo pomocí [rozhraní ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) nebo ovladače OLE DB. ODBC je aktuální databáze standard rozhraní, ale většina databázových systémů poskytují vlastní funkce, která není přístupná přes rozhraní ODBC.  OLE DB je starou technologií přístupu k datům modelu COM, který je stále podporovány, ale nedoporučuje se u nových aplikací.  Další informace najdete v tématu [přístup k datům](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++programy, které využívají služby REST, můžou používat [ C++ sadu REST SDK](https://github.com/Microsoft/cpprestsdk).

 C++programy, které pracují se Microsoft Azure Storage můžou používat [klienta Microsoft Azure Storage](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modelování dat
 Visual Studio neposkytuje vrstvu ORM pro jazyk C++.  [ODB](https://www.codesynthesis.com/products/odb/) je oblíbený Open Source ORM pro C++.

 Další informace o starších technologiích C++ vizuálního přístupu k datům najdete v tématu [přístup k datům](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b) .

### <a name="javascript"></a>JavaScript
 [JavaScript v aplikaci Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) je prvotřídní jazyk pro vytváření aplikací pro různé platformy, aplikací pro UWP, cloudových služeb, webů a webových aplikací. Bower, Grunt, Gulp, npm a NuGet v sadě Visual Studio můžete použít k instalaci vašich oblíbených knihoven JavaScriptu a databáze produktů. Stáhněte si sady SDK z [webu Azure](https://azure.microsoft.com/)a připojte se k Azure Storage a službám.  Edge.js je knihovna, která se připojuje ke zdrojům dat ADO.NET JavaScript na straně serveru (Node.js).

### <a name="python"></a>Python
 Pokud chcete vytvářet aplikace CPython nebo Ironpythonu (.NET), nainstalujte [Python Tools for Visual Studio](http://microsoft.github.io/PTVS/) společně s oblíbeným rozhraním Pythonu.  Web Python Tools for Visual Studio obsahuje několik kurzů pro připojení k datům, včetně [Django a SQL Database v Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django a MySQL v](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) Azure a [MongoDB v Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>V tomto oddílu
 [Instalace databázových systémů, nástrojů a ukázek](../data-tools/installing-database-systems-tools-and-samples.md) Tento článek popisuje, jak získat databázové produkty a rozšíření nebo ovladače sady Visual Studio, které je podporují, a kde najít ukázkové databáze pro účely experimentování a učení.

 [Visual Studio Data Tools for .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Popisuje, jak používat okna nástrojů sady Visual Studio pro připojení ke zdrojům dat, vytváření datových sad nebo Entity Framework modelů a navázání dat na ovládací prvky uživatelského rozhraní.

## <a name="related-topics"></a>Související témata
 [Data, zařízení a analýzy](https://msdn.microsoft.com/data-and-devices) Poskytuje Úvod do inteligentního cloudu Microsoft, včetně Cortana Analytics Suite a podpory Internet věcí.

 [Microsoft Azure Storage](/azure/storage/) Popisuje Azure Storage a vytváření aplikací pomocí objektů blob, tabulek, front a souborů Azure.

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) Popisuje, jak se připojit k Azure SQL Database relační databáze jako služba.

 [Nástroje pro SQL Server dat](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Popisuje nástroje, které zjednodušují návrh, průzkum, testování a nasazení aplikací a databází propojených s daty.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) Popisuje architekturu ADO.NET a použití tříd ADO.NET ke správě aplikačních dat a interakci se zdroji dat a XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) V této části najdete popis postupu vytváření datových aplikací, které vývojářům umožňují programovat v koncepčním modelu místo přímého používání relační databáze.

 [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Popisuje, jak použít [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] k nasazení datových služeb na webu nebo v intranetu, který implementuje [protokol OData (Open Data Protocol)](https://go.microsoft.com/fwlink/?LinkID=182204).

 [Data v řešeních pro systém Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Obsahuje odkazy na témata, která vysvětlují, jak fungují data v řešeních pro systém Office. To zahrnuje informace o programování orientovaném na schéma, ukládání dat do mezipaměti a přístupu k datům na straně serveru.

 [LINQ (jazykově integrovaný dotaz)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Popisuje možnosti dotazů integrované do C# a Visual Basic a společný model pro dotazování na relačních databázích, dokumentech XML, datových sadách a kolekcích v paměti.

 [Nástroje XML v aplikaci Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Popisuje práci s daty XML, ladění XSLT, .NET Framework funkcí XML a architektury dotazů XML.

 [Dokumenty a data XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Poskytuje přehled komplexní a integrované sady tříd, které pracují s dokumenty XML a daty v .NET Framework.
