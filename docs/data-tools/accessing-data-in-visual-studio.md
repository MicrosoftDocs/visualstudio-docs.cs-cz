---
title: Práce s daty v aplikaci Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c7aa1544f998a88424c0087fadceab63757d23b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272085"
---
# <a name="work-with-data-in-visual-studio"></a>Práce s daty v aplikaci Visual Studio

V sadě Visual Studio můžete vytvářet aplikace, které se připojují k datům v téměř jakoukoli databázový produkt nebo službu, v libovolném formátu, kdekoli – v místním počítači, v místní síti, nebo veřejné, privátní nebo hybridní cloud.

Pro aplikace v jazyce JavaScript, Python, PHP, Ruby nebo C++ můžete připojit k datům stejným způsobem jako cokoli jiného, získání knihovny a psaní kódu. Pro aplikace .NET nabízí Visual Studio nástroje, které můžete použít k prozkoumávání zdrojů dat, vytváření objektových modelů pro ukládání a manipulaci s daty v paměti a k vytvoření vazby dat k uživatelskému rozhraní. Microsoft Azure poskytuje sady SDK pro .NET, Java, Node.js, PHP, Python, Ruby a mobilní aplikace a nástroje v sadě Visual Studio pro připojení k Azure Storage.

::: moniker range="vs-2017"
Následující seznamy shrnují jenom některé z mnoha systémů databáze a úložišť, se dají ze sady Visual Studio. Nabídky [Microsoft Azure](https://azure.microsoft.com/) jsou datové služby, které zahrnují všechna zřizování a správu základního úložiště dat. Úlohy **vývoje Azure** v [aplikaci Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) umožňují pracovat s úložišti dat Azure přímo ze sady Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Následující seznamy shrnují jenom některé z mnoha systémů databáze a úložišť, se dají ze sady Visual Studio. Nabídky [Microsoft Azure](https://azure.microsoft.com/) jsou datové služby, které zahrnují všechna zřizování a správu základního úložiště dat. Úlohy **vývoje Azure** v [aplikaci Visual Studio 2019](https://visualstudio.microsoft.com/downloads) umožňují pracovat s úložišti dat Azure přímo ze sady Visual Studio.
::: moniker-end

![Úloha vývoj pro Azure](media/azure-development-workload.png)

Většinu ostatních SQL a NoSQL databáze produktů, které jsou zde uvedeny, je možné hostovat na místním počítači, v místní síti nebo v Microsoft Azure na virtuálním počítači. Pokud databázi hostovatte na Microsoft Azurem virtuálním počítači, zodpovídáte za správu samotné databáze.

**Microsoft Azure**

- SQL Database
- Databáze Azure Cosmos
- Storage (objekty BLOB, tabulky, fronty, soubory)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- a další...

**SQL**

- SQL Server 2005-2016 (zahrnuje expresní a LocalDB)
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

::: moniker range="vs-2017"

Mnoho dodavatelů databáze a třetí strany nepodporují integraci s Visual Studio pomocí balíčků NuGet. Nabídky můžete prozkoumat v nuget.org nebo pomocí Správce balíčků NuGet v aplikaci Visual Studio (**nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**). Produkty databáze můžete integrovat s aplikací Visual Studio jako rozšíření. Tyto nabídky můžete procházet v [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo pomocí přechodu na **nástroje** > **rozšíření a aktualizace** a následným výběrem možnosti **online** v levém podokně dialogového okna. Další informace najdete v tématu [kompatibilní databázové systémy pro Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Mnoho dodavatelů databáze a třetí strany nepodporují integraci s Visual Studio pomocí balíčků NuGet. Nabídky můžete prozkoumat v nuget.org nebo pomocí Správce balíčků NuGet v aplikaci Visual Studio (**nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**). Produkty databáze můžete integrovat s aplikací Visual Studio jako rozšíření. Tyto nabídky můžete procházet v [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo tak, že přejdete na **rozšíření** > **Spravovat rozšíření** a pak vyberete **online** v levém podokně dialogového okna. Další informace najdete v tématu [kompatibilní databázové systémy pro Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Rozšířená podpora pro SQL Server 2005 skončila 12. dubna 2016. Není zaručeno, že datové nástroje v aplikaci Visual Studio 2015 a novější budou nadále fungovat s SQL Server 2005. Další informace najdete v tématu [oznámení ukončení podpory SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Jazyky rozhraní .NET

Veškerý přístup k datům .NET, včetně rozhraní .NET Core, je založen na ADO.NET, sadě tříd, které definují rozhraní pro přístup k jakémukoli typu zdroje dat, relačním i nerelačním. Visual Studio obsahuje několik nástrojů a návrhářů, které pracují s ADO.NET připojení k databázím, vám usnadní pracuje s daty a prezentovat uživateli. Dokumentace v této části popisuje, jak pomocí těchto nástrojů. Také můžete programovat přímo proti objekty příkazů ADO.NET. Další informace o přímém volání rozhraní API ADO.NET naleznete v tématu [ADO.NET](/dotnet/framework/data/adonet/index).

Dokumentaci k datům související s ASP.NET najdete v tématu [práce s daty](https://www.asp.net/web-forms/overview/presenting-and-managing-data) na webu ASP.NET. Kurz použití Entity Framework s ASP.NET MVC najdete v článku [Začínáme s Entity Framework 6 Code First pomocí MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Aplikace Univerzální platforma Windows (UWP) v C# nebo Visual Basic můžou používat Microsoft Azure SDK pro .NET pro přístup k Azure Storage a dalším službám Azure. Třída Windows.Web.HttpClient umožňuje komunikaci se všemi službami, RESTful. Další informace najdete v tématu [jak se připojit k serveru HTTP pomocí Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Doporučený postup pro ukládání dat v místním počítači, je použít SQLite, která běží ve stejném procesu jako aplikace. Pokud vrstvu objektově relační mapování (ORM) je potřeba, můžete použít Entity Framework. Další informace najdete v tématu [přístup k datům](/windows/uwp/data-access/index) v centru pro vývojáře v systému Windows.

Pokud se připojujete ke službám Azure, nezapomeňte si stáhnout nejnovější [nástroje Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Zprostředkovatelé dat

Aby databáze byla v ADO.NET spotřební, musí mít vlastního *poskytovatele dat ADO.NET* nebo jinak musí vystavit rozhraní ODBC nebo OLE DB. Společnost Microsoft poskytuje [seznam zprostředkovatelů ADO.NET dat](/dotnet/framework/data/adonet/ado-net-overview) pro produkty SQL Server a také poskytovatele rozhraní ODBC a OLE DB.

### <a name="data-modeling"></a>Modelování dat

V rozhraní .NET máte tři možnosti pro modelování a manipulace s daty v paměti, po jejím načtení ze zdroje dat:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Upřednostňovaná technologie Microsoft ORM. Můžete ho programovat proti relačních dat jako první třídy objektů .NET. Pro nové aplikace je třeba výchozí první volbou při je vyžadován model. Vyžaduje vlastní podporu – od podkladového zprostředkovatele ADO.NET.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Objekt dřívější generace – relační Mapovač. Funguje dobře pro méně složité scénáře, ale již není v aktivním vývoji.

[Datové sady](../data-tools/dataset-tools-in-visual-studio.md) Nejstarší ze tří technologií modelování. Je určená primárně pro rychlý vývoj aplikací "formy nad daty", ve kterých nejsou zpracování obrovské objemy dat nebo provádění složitých dotazů nebo transformací. Objekt DataSet se skládá z objektů DataTable a DataRow, které logicky připomínají objekty databáze SQL mnohem více než objekty .NET. U relativně jednoduchých aplikací založených na zdrojích dat SQL může být v datových sadách stále vhodná volba.

Neexistuje žádný požadavek k používání některé z těchto technologií. V některých případech, zejména v případě, že je výkon kritický, můžete jednoduše použít objekt DataReader ke čtení z databáze a zkopírovat hodnoty, které potřebujete do objektu kolekce, jako je například seznam\<T >.

## <a name="native-c"></a>Nativní kód C++

C++aplikace, které se připojují k SQL Server, by měly ve většině případů používat [ovladač Microsoft® ODBC 13,1 pro SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) . Pokud jsou servery propojené, OLE DB nutné a pro použití [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). K ostatním databázím můžete přistupovat přímo pomocí [rozhraní ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) nebo ovladače OLE DB. ODBC je aktuální databáze standard rozhraní, ale většina databázových systémů poskytují vlastní funkce, která není přístupná přes rozhraní ODBC. OLE DB je starou technologií přístupu k datům modelu COM, který je stále podporovány, ale nedoporučuje se u nových aplikací. Další informace najdete v tématu [přístup k datům v C++vizuálu ](/cpp/data/data-access-in-cpp).

C++programy, které využívají služby REST, můžou používat [ C++ sadu REST SDK](https://github.com/Microsoft/cpprestsdk).

C++programy, které pracují se Microsoft Azure Storage můžou používat [klienta Microsoft Azure Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Modelování dat&mdash;Visual Studiu neposkytuje vrstvu ORM pro C++. [ODB](https://www.codesynthesis.com/products/odb/) je oblíbený Open Source ORM pro C++.

Další informace o připojení k databázím z C++ aplikací naleznete v tématu [Visual Studio Data Tools C++for ](../data-tools/visual-studio-data-tools-for-cpp.md). Další informace o starších technologiích C++ vizuálního přístupu k datům najdete v tématu [přístup k datům](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript v aplikaci Visual Studio](/scripting/javascript/javascript-language-reference) je prvotřídní jazyk pro vytváření aplikací pro různé platformy, aplikací pro UWP, cloudových služeb, webů a webových aplikací. V sadě Visual Studio můžete pomocí Bower, grunt, Gulp, npm a NuGet nainstalovat své oblíbené knihovny JavaScript a databázové produkty. Stáhněte si sady SDK z [webu Azure](https://azure.microsoft.com/)a připojte se k Azure Storage a službám. Edge.js je knihovna, která se připojuje ke zdrojům dat ADO.NET JavaScript na straně serveru (Node.js).

## <a name="python"></a>Python

Pokud chcete vytvářet aplikace v Pythonu, nainstalujte [podporu Pythonu v aplikaci Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) . Dokumentace k Azure obsahuje několik kurzů, které se připojují k datům, včetně následujících:

- [Django a SQL Database v Azure](/azure/app-service/app-service-web-get-started-python)
- [Django a MySQL v Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Práce s [objekty blob](/azure/storage/blobs/storage-quickstart-blobs-python), [soubory](/azure/storage/files/storage-python-how-to-use-file-storage), [frontami](/azure/storage/queues/storage-python-how-to-use-queue-storage)a [tabulkami (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)

## <a name="related-topics"></a>Související témata

[Microsoft AI platform](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;poskytuje Úvod do inteligentního cloudu Microsoft, včetně Cortana Analytics Suite a podpory pro Internet věcí.

[Microsoft Azure Storage](/azure/storage/)&mdash;popisuje Azure Storage a vytváření aplikací pomocí objektů blob, tabulek, front a souborů Azure.

[Azure SQL Database](/azure/sql-database/)&mdash;popisuje, jak se připojit k Azure SQL Database, relační databázi jako službu.

[Nástroje SQL Server data tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;popisují nástroje, které zjednodušují návrh, průzkum, testování a nasazování aplikací a databází propojených s daty.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;popisuje architekturu ADO.NET a způsob použití tříd ADO.NET ke správě aplikačních dat a interakci se zdroji dat a XML.

[ADO.NET Entity Framework](/ef/ef6/)&mdash;popisuje, jak vytvářet datové aplikace, které vývojářům umožňují programovat na koncepčním modelu místo přímého navýšení relační databáze.

[WCF Data Services 4,5](/dotnet/framework/data/wcf/index)&mdash;popisuje, jak používat [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] k nasazení datových služeb na webu nebo v intranetu, který implementuje [protokol OData (Open Data Protocol)](https://www.odata.org/).

[Data v řešeních pro office](../vsto/data-in-office-solutions.md)&mdash;obsahují odkazy na témata, která vysvětlují, jak fungují data v řešeních pro systém Office. To zahrnuje informace o programování orientovaném na schéma, ukládání dat do mezipaměti a přístupu k datům na straně serveru.

[LINQ (jazykově integrovaný dotaz)](/dotnet/csharp/linq/)&mdash;popisuje možnosti dotazů integrovaných do C# a Visual Basic a společný model pro dotazování na relačních databázích, dokumentech XML, datových sadách a kolekcích v paměti.

[Nástroje XML v aplikaci Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;probírají práci s daty XML, laděním XSLT, funkcemi .NET XML a architekturou dotazů XML.

[Dokumenty XML a data](/dotnet/standard/data/xml/index)&mdash;poskytují přehled o komplexní a integrované sadě tříd, které pracují s dokumenty XML a daty v rozhraní .NET.
