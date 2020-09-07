---
title: Práce s daty v sadě Visual Studio
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
ms.openlocfilehash: 36fc3d3fd0b002c110e9184a6d7b15c9fa367c48
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509832"
---
# <a name="work-with-data-in-visual-studio"></a>Práce s daty v sadě Visual Studio

V aplikaci Visual Studio můžete vytvářet aplikace, které se připojují k datům prakticky z libovolného databázového produktu nebo služby, v libovolném formátu, kdekoli – na místním počítači, v místní síti nebo ve veřejném, privátním nebo hybridním cloudu.

Pro aplikace v jazycích JavaScript, Python, PHP, Ruby nebo C++ se můžete připojit k datům, jako je třeba cokoli jiného, pomocí získání knihoven a psaní kódu. Pro aplikace .NET nabízí Visual Studio nástroje, které můžete použít k prozkoumávání zdrojů dat, vytváření objektových modelů pro ukládání a manipulaci s daty v paměti a k vytvoření vazby dat k uživatelskému rozhraní. Microsoft Azure poskytuje sady SDK pro .NET, Java, Node.js, PHP, Python, Ruby a mobilní aplikace a nástroje v aplikaci Visual Studio pro připojení k Azure Storage.

::: moniker range="vs-2017"
V následujících seznamech je znázorněno několik mnoha databázových a úložných systémů, které lze použít ze sady Visual Studio. Nabídky [Microsoft Azure](https://azure.microsoft.com/) jsou datové služby, které zahrnují všechna zřizování a správu základního úložiště dat. Úlohy **vývoje Azure** v [aplikaci Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) umožňují pracovat s úložišti dat Azure přímo ze sady Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
V následujících seznamech je znázorněno několik mnoha databázových a úložných systémů, které lze použít ze sady Visual Studio. Nabídky [Microsoft Azure](https://azure.microsoft.com/) jsou datové služby, které zahrnují všechna zřizování a správu základního úložiště dat. Úlohy **vývoje Azure** v [aplikaci Visual Studio 2019](https://visualstudio.microsoft.com/downloads) umožňují pracovat s úložišti dat Azure přímo ze sady Visual Studio.
::: moniker-end

![Úlohy vývoje Azure](media/azure-development-workload.png)

Většina ostatních databázových produktů SQL a NoSQL, které jsou tady uvedené, se dají hostovat na místním počítači, v místní síti nebo v Microsoft Azure na virtuálním počítači. Pokud databázi hostovatte na Microsoft Azurem virtuálním počítači, zodpovídáte za správu samotné databáze.

**Microsoft Azure**

- Databáze SQL
- Azure Cosmos DB
- Storage (objekty blob, tabulky, fronty, soubory)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- A další...

**SQL**

- SQL Server 2005-2016 (zahrnuje expresní a LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- A další...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB |
- RavenDB
- VelocityDB
- A další...

::: moniker range="vs-2017"

Mnoho dodavatelů databází a třetích stran podporuje integraci sady Visual Studio pomocí balíčků NuGet. Nabídky můžete prozkoumat v NuGet.org nebo pomocí Správce balíčků NuGet v aplikaci Visual Studio (**nástroje**  >  **Správce balíčků NuGet**  >  **Správa balíčků NuGet pro řešení**). Další databázové produkty jsou integrovány se sadou Visual Studio jako rozšíření. Můžete procházet tyto nabídky v [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo přejít na rozšíření **nástrojů**  >  **a aktualizace** a pak vybrat **online** v levém podokně dialogového okna. Další informace najdete v tématu [kompatibilní databázové systémy pro Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Mnoho dodavatelů databází a třetích stran podporuje integraci sady Visual Studio pomocí balíčků NuGet. Nabídky můžete prozkoumat v NuGet.org nebo pomocí Správce balíčků NuGet v aplikaci Visual Studio (**nástroje**  >  **Správce balíčků NuGet**  >  **Správa balíčků NuGet pro řešení**). Další databázové produkty jsou integrovány se sadou Visual Studio jako rozšíření. Tyto nabídky můžete procházet v [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo pomocí navigace do **rozšíření**pro  >  **správu rozšíření** a pak výběrem možnosti **online** v levém podokně dialogového okna. Další informace najdete v tématu [kompatibilní databázové systémy pro Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Prodloužená podpora SQL Server 2005 skončila 12. dubna 2016. Není zaručeno, že datové nástroje v aplikaci Visual Studio 2015 a novější budou nadále fungovat s SQL Server 2005. Další informace najdete v tématu [oznámení ukončení podpory SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Jazyky .NET

Veškerý přístup k datům .NET, včetně rozhraní .NET Core, je založen na ADO.NET, sadě tříd, které definují rozhraní pro přístup k jakémukoli typu zdroje dat, relačním i nerelačním. Visual Studio obsahuje několik nástrojů a návrhářů, které pracují s ADO.NET, které vám pomůžou se připojit k databázím, manipulovat s daty a prezentovat data uživateli. Dokumentace v této části popisuje, jak tyto nástroje používat. Můžete také programovat přímo proti objektům příkazu ADO.NET. Další informace o přímém volání rozhraní API ADO.NET naleznete v tématu [ADO.NET](/dotnet/framework/data/adonet/index).

Dokumentaci k datům související s ASP.NET najdete v tématu [práce s daty](https://www.asp.net/web-forms/overview/presenting-and-managing-data) na webu ASP.NET. Kurz použití Entity Framework s ASP.NET MVC najdete v článku [Začínáme s Entity Framework 6 Code First pomocí MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Aplikace Univerzální platforma Windows (UWP) v jazyce C# nebo Visual Basic mohou použít Microsoft Azure SDK pro .NET pro přístup k Azure Storage a dalším službám Azure. Třída Windows. Web. HttpClient umožňuje komunikaci s jakoukoli službou RESTful. Další informace najdete v tématu [jak se připojit k serveru HTTP pomocí Windows. Web. http](/previous-versions/windows/apps/dn469430(v=win.10)).

V případě úložiště dat v místním počítači je doporučeným přístupem použití SQLite, který běží ve stejném procesu jako aplikace. Pokud je vyžadována vrstva mapování relačních objektů (ORM), můžete použít Entity Framework. Další informace najdete v tématu [přístup k datům](/windows/uwp/data-access/index) v centru pro vývojáře v systému Windows.

Pokud se připojujete ke službám Azure, nezapomeňte si stáhnout nejnovější [nástroje Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Poskytovatelé dat

Aby databáze byla v ADO.NET spotřební, musí mít vlastního *poskytovatele dat ADO.NET* nebo jinak musí vystavit rozhraní ODBC nebo OLE DB. Společnost Microsoft poskytuje [seznam zprostředkovatelů ADO.NET dat](/dotnet/framework/data/adonet/ado-net-overview) pro produkty SQL Server a také poskytovatele rozhraní ODBC a OLE DB.

### <a name="data-modeling"></a>Modelování dat

V rozhraní .NET máte tři možnosti modelování a manipulace s daty v paměti po jejich načtení ze zdroje dat:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Upřednostňovaná technologie Microsoft ORM. Můžete ji použít k programu s relačními daty jako objekty .NET první třídy. Pro nové aplikace by měla být výchozí možnost první, když je model vyžadován. Vyžaduje vlastní podporu od základního poskytovatele ADO.NET.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Objekt dřívější generace – relační Mapovač. Funguje dobře pro méně složité scénáře, ale už není aktivním vývojem.

[Datové sady](../data-tools/dataset-tools-in-visual-studio.md) Nejstarší ze tří technologií modelování. Je určený hlavně pro rychlý vývoj aplikací nad daty, ve kterých nezpracováváte velké objemy dat nebo provádění složitých dotazů nebo transformací. Objekt DataSet se skládá z objektů DataTable a DataRow, které logicky připomínají objekty databáze SQL mnohem více než objekty .NET. U relativně jednoduchých aplikací založených na zdrojích dat SQL může být v datových sadách stále vhodná volba.

Neexistuje žádný požadavek na používání žádné z těchto technologií. V některých případech, zejména v případě, že je výkon kritický, můžete jednoduše použít objekt DataReader ke čtení z databáze a zkopírovat hodnoty, které potřebujete do objektu kolekce, jako je seznam \<T> .

## <a name="native-c"></a>Nativní C++

Aplikace C++, které se připojují k SQL Server, by měly ve většině případů používat [ovladač Microsoft® ODBC 13,1 pro SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) . Pokud jsou servery propojené, OLE DB nutné a pro použití [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). K ostatním databázím můžete přistupovat přímo pomocí [rozhraní ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) nebo ovladače OLE DB. Rozhraní ODBC je aktuální standardní databázové rozhraní, ale většina databázových systémů poskytuje vlastní funkce, ke kterým nelze získat pøístup prostřednictvím rozhraní ODBC. OLE DB je starší technologie pro přístup k datům modelu COM, která je stále podporovaná, ale nedoporučuje se pro nové aplikace. Další informace najdete v tématu [přístup k datům v Visual C++](/cpp/data/data-access-in-cpp).

Programy c++, které využívají služby REST, můžou používat [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Programy v jazyce C++, které pracují s Microsoft Azure Storage mohou používat [klienta Microsoft Azure Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

&mdash;V aplikaci Visual Studio pro modelování dat není k dispozici vrstva ORM pro C++. [ODB](https://www.codesynthesis.com/products/odb/) je oblíbený Open Source ORM pro C++.

Další informace o připojení k databázím z aplikací C++ naleznete v tématu [Visual Studio Data Tools for c++](../data-tools/visual-studio-data-tools-for-cpp.md). Další informace o starších Visual C++ technologiích pro přístup k datům najdete v tématu [přístup k datům](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[JavaScript v aplikaci Visual Studio](/scripting/javascript/javascript-language-reference) je prvotřídní jazyk pro vytváření aplikací pro různé platformy, aplikací pro UWP, cloudových služeb, webů a webových aplikací. V sadě Visual Studio můžete pomocí Bower, grunt, Gulp, npm a NuGet nainstalovat své oblíbené knihovny JavaScript a databázové produkty. Stáhněte si sady SDK z [webu Azure](https://azure.microsoft.com/)a připojte se k Azure Storage a službám. Edge.js je knihovna, která propojuje server JavaScript (Node.js) na straně serveru s ADO.NET zdroji dat.

## <a name="python"></a>Python

Pokud chcete vytvářet aplikace v Pythonu, nainstalujte [podporu Pythonu v aplikaci Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) . Dokumentace k Azure obsahuje několik kurzů, které se připojují k datům, včetně následujících:

- [Django a SQL Database v Azure](/azure/app-service/app-service-web-get-started-python)
- [Django a MySQL v Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Práce s [objekty blob](/azure/storage/blobs/storage-quickstart-blobs-python), [soubory](/azure/storage/files/storage-python-how-to-use-file-storage), [frontami](/azure/storage/queues/storage-python-how-to-use-queue-storage)a [tabulkami (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)

## <a name="related-topics"></a>Související témata

[Platforma](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Microsoft AI Poskytuje Úvod do inteligentního cloudu Microsoft, včetně Cortana Analytics Suite a podpory Internet věcí.

[Microsoft Azure Storage](/azure/storage/) &mdash; Popisuje Azure Storage a vytváření aplikací pomocí objektů blob, tabulek, front a souborů Azure.

[Azure SQL Database](/azure/sql-database/) &mdash; Popisuje, jak se připojit k Azure SQL Database relační databáze jako služba.

Nástroje pro SQL Server [dat](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Popisuje nástroje, které zjednodušují návrh, průzkum, testování a nasazení aplikací a databází propojených s daty.

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash; Popisuje architekturu ADO.NET a použití tříd ADO.NET ke správě aplikačních dat a interakci se zdroji dat a XML.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; V této části najdete popis postupu vytváření datových aplikací, které vývojářům umožňují programovat v koncepčním modelu místo přímého používání relační databáze.

[WCF Data Services 4,5](/dotnet/framework/data/wcf/index) &mdash; Popisuje, jak používat nástroj [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] k nasazení datových služeb na webu nebo v intranetu, který implementuje [protokol OData (Open Data Protocol)](https://www.odata.org/).

[Data v řešeních](../vsto/data-in-office-solutions.md) &mdash; pro systém Office Obsahuje odkazy na témata, která vysvětlují, jak fungují data v řešeních pro systém Office. To zahrnuje informace o programování orientovaném na schéma, ukládání dat do mezipaměti a přístupu k datům na straně serveru.

[LINQ (jazykově integrovaný dotaz)](/dotnet/csharp/linq/) &mdash; Popisuje možnosti dotazů integrované do C# a Visual Basic a společný model pro dotazování na relačních databázích, dokumentech XML, datových sadách a kolekcích v paměti.

[Nástroje XML v aplikaci Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; Popisuje práci s daty XML, ladění souborů XSLT, funkcí .NET XML a architektury dotazů jazyka XML.

[Dokumenty a data XML](/dotnet/standard/data/xml/index) &mdash; Poskytuje přehled komplexní a integrované sady tříd, které pracují s dokumenty XML a daty v rozhraní .NET.