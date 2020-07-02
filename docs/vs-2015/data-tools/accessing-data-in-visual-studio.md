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
ms.openlocfilehash: 78d950b777d866835ef516c4910180b21de295e9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544999"
---
# <a name="accessing-data-in-visual-studio"></a>Přístup k datům v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete vytvářet aplikace, které se připojují k datům prakticky z libovolného databázového produktu nebo služby, v libovolném formátu, kdekoli – na místním počítači, v místní síti nebo ve veřejném, privátním nebo hybridním cloudu.

 Pro aplikace v jazycích JavaScript, Python, PHP, Ruby nebo C++ se můžete připojit k datům, jako je třeba cokoli jiného, pomocí získání knihoven a psaní kódu. Pro aplikace .NET nabízí Visual Studio nástroje, které můžete použít k prozkoumávání zdrojů dat, vytváření objektových modelů pro ukládání a manipulaci s daty v paměti a k vytvoření vazby dat k uživatelskému rozhraní.     Microsoft Azure poskytuje sady SDK pro .NET, Java, Node.js, PHP, Python, Ruby a mobilní aplikace a nástroje v aplikaci Visual Studio pro připojení k Azure Storage.

 V následujících seznamech je znázorněno několik mnoha databázových a úložných systémů, které lze použít ze sady Visual Studio. Nabídky [Microsoft Azure](https://azure.microsoft.com/) jsou datové služby, které zahrnují všechna zřizování a správu základního úložiště dat.  [Nástroje Azure pro Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) jsou volitelnou komponentou, která umožňuje pracovat s úložišti dat Azure přímo ze sady Visual Studio. Většina ostatních databázových produktů SQL a NoSQL, které jsou tady uvedené, se dají hostovat na místním počítači, v místní síti nebo v Microsoft Azure na virtuálním počítači. V tomto scénáři zodpovídáte za správu samotné databáze.

 **Microsoft Azure**

- Databáze SQL

- DocumentDB

– Storage (objekty blob, tabulky, fronty, soubory)

- SQL Data Warehouse

- SQL Server Stretch Database

- StorSimple

 A další...

 **SQL**

- SQL Server 2005 – 2016, včetně expresních a LocalDB
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite

 A další...

 **NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB
- RavenDB
- VelocityDB

 A další...

 Mnoho dodavatelů databází a třetích stran podporuje integraci sady Visual Studio pomocí balíčků NuGet. Nabídky můžete prozkoumat v NuGet.org nebo pomocí Správce balíčků NuGet v aplikaci Visual Studio (**nástroje**  >  **Správce balíčků NuGet**  >  **Správa balíčků NuGet pro řešení**). Další databázové produkty jsou integrovány se sadou Visual Studio jako rozšíření.   Tyto nabídky můžete procházet v galerii sady Visual Studio tak, že přejdete na **Tools**  >  **rozšíření a aktualizace** nástrojů a pak v levém podokně dialogového okna vyberete **online** .  Další informace najdete v tématu [instalace databázových systémů, nástrojů a ukázek](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Prodloužená podpora SQL Server 2005 skončila 12. dubna 2016.   Není zaručeno, že datové nástroje v aplikaci Visual Studio 2015 a novější budou po tomto datu nadále fungovat s SQL Server 2005. Další informace najdete v tématu [oznámení ukončení podpory SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Jazyky .NET
 Veškerý přístup k datům .NET, včetně rozhraní .NET Core, je založen na ADO.NET, sadě tříd, které definují rozhraní pro přístup k jakémukoli typu zdroje dat, relačním i nerelačním. Visual Studio obsahuje několik nástrojů a návrhářů, které pracují s ADO.NET, které vám pomůžou se připojit k databázím, manipulovat s daty a prezentovat data uživateli. Dokumentace v této části popisuje, jak tyto nástroje používat. Můžete také programovat přímo proti objektům příkazu ADO.NET. Další informace o přímém volání rozhraní API ADO.NET najdete v tématu [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) v knihovně MSDN.

 Dokumentaci k přístupu k datům konkrétně související s ASP.NET najdete v tématu [práce s daty](/aspnet/web-forms/overview/presenting-and-managing-data/) na webu ASP.NET. Kurz použití Entity Framework s ASP.NET MVC najdete v článku [Začínáme s Entity Framework 6 Code First pomocí MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Aplikace Univerzální platforma Windows (UWP) v jazyce C# nebo Visual Basic mohou použít Microsoft Azure SDK pro .NET pro přístup k Azure Storage a dalším službám Azure. Třída Windows. Web. HttpClient umožňuje komunikaci s jakoukoli službou RESTful. Další informace najdete v tématu [jak se připojit k serveru HTTP pomocí Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 V případě úložiště dat v místním počítači je doporučeným přístupem použití SQLite, který běží ve stejném procesu jako aplikace. Pokud je vyžadována vrstva mapování relačních objektů (ORM), můžete použít Entity Framework. Další informace najdete v tématu [přístup k datům](https://msdn.microsoft.com/windows/uwp/data-access/index) v centru pro vývojáře v systému Windows.

 Pokud se připojujete ke službám Azure, nezapomeňte si stáhnout nejnovější [nástroje Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Poskytovatelé dat
 Aby databáze byla v ADO.NET spotřební, musí mít vlastního *poskytovatele dat ADO.NET* nebo jinak musí vystavit rozhraní ODBC nebo OLE DB. Společnost Microsoft poskytuje [seznam zprostředkovatelů ADO.NET dat](https://msdn.microsoft.com/data/dd363565) pro produkty SQL Server a také pro poskytovatele rozhraní ODBC a OLE DB.

#### <a name="data-modeling"></a>Modelování dat
 V rozhraní .NET máte tři možnosti modelování a manipulace s daty v paměti po jejich načtení ze zdroje dat:

 Entity Framework upřednostňovanou technologii Microsoft ORM. Můžete ji použít k programu s relačními daty jako objekty .NET první třídy. Pro nové aplikace by měla být výchozí možnost první, když je model vyžadován. Vyžaduje vlastní podporu od základního poskytovatele ADO.NET.

 LINQ to SQL objekt dřívější generace – relační Mapovač. Funguje dobře pro méně složité scénáře, ale už není aktivním vývojem.

 Datový nastaví nejstarší ze tří technologií modelování. Je určený hlavně pro rychlý vývoj aplikací nad daty, ve kterých nezpracováváte velké objemy dat nebo provádění složitých dotazů nebo transformací. Objekt DataSet se skládá z objektů DataTable a DataRow, které logicky připomínají objekty databáze SQL mnohem více než objekty .NET. U relativně jednoduchých aplikací založených na zdrojích dat SQL může být v datových sadách stále vhodná volba.

 Neexistuje žádný požadavek na používání žádné z těchto technologií. V některých případech, zejména v případě, že je výkon kritický, můžete jednoduše použít objekt DataReader ke čtení z databáze a zkopírovat hodnoty, které potřebujete do objektu kolekce, jako je seznam \<T> .

### <a name="native-c"></a>Nativní C++
 Aplikace C++, které se připojují k SQL Server by měly používat [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). K ostatním databázím můžete přistupovat přímo pomocí [rozhraní ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) nebo ovladače OLE DB. Rozhraní ODBC je aktuální standardní databázové rozhraní, ale většina databázových systémů poskytuje vlastní funkce, ke kterým nelze získat pøístup prostřednictvím rozhraní ODBC.  OLE DB je starší technologie pro přístup k datům modelu COM, která je stále podporovaná, ale nedoporučuje se pro nové aplikace.  Další informace najdete v tématu [přístup k datům](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 Programy c++, které využívají služby REST, můžou používat [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

 Programy v jazyce C++, které pracují s Microsoft Azure Storage mohou používat [klienta Microsoft Azure Storage](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modelování dat
 Visual Studio neposkytuje vrstvu ORM pro C++.  [ODB](https://www.codesynthesis.com/products/odb/) je oblíbený Open Source ORM pro C++.

 Další informace o starších Visual C++ technologiích pro přístup k datům najdete v tématu [přístup k datům](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b) .

### <a name="javascript"></a>JavaScript
 [JavaScript v aplikaci Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) je prvotřídní jazyk pro vytváření aplikací pro různé platformy, aplikací pro UWP, cloudových služeb, webů a webových aplikací. V sadě Visual Studio můžete pomocí Bower, grunt, Gulp, npm a NuGet nainstalovat své oblíbené knihovny JavaScript a databázové produkty. Stáhněte si sady SDK z [webu Azure](https://azure.microsoft.com/)a připojte se k Azure Storage a službám.  Edge.js je knihovna, která propojuje server JavaScript (Node.js) na straně serveru s ADO.NET zdroji dat.

### <a name="python"></a>Python
 Pokud chcete vytvářet aplikace CPython nebo Ironpythonu (.NET), nainstalujte [Python Tools for Visual Studio](http://microsoft.github.io/PTVS/) společně s oblíbeným rozhraním Pythonu.  Web Python Tools for Visual Studio obsahuje několik kurzů pro připojení k datům, včetně [Django a SQL Database v Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django a MySQL v](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) Azure a [MongoDB v Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>V této části
 [Instalace databázových systémů, nástrojů a ukázek](../data-tools/installing-database-systems-tools-and-samples.md) Tento článek popisuje, jak získat databázové produkty a rozšíření nebo ovladače sady Visual Studio, které je podporují, a kde najít ukázkové databáze pro účely experimentování a učení.

 [Visual Studio Data Tools for .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Popisuje, jak používat okna nástrojů sady Visual Studio pro připojení ke zdrojům dat, vytváření datových sad nebo Entity Framework modelů a navázání dat na ovládací prvky uživatelského rozhraní.

## <a name="related-topics"></a>Související témata
 [Data, zařízení a analýzy](https://msdn.microsoft.com/data-and-devices) Poskytuje Úvod do inteligentního cloudu Microsoft, včetně Cortana Analytics Suite a podpory Internet věcí.

 [Microsoft Azure Storage](/azure/storage/) Popisuje Azure Storage a vytváření aplikací pomocí objektů blob, tabulek, front a souborů Azure.

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) Popisuje, jak se připojit k Azure SQL Database relační databáze jako služba.

 [Nástroje pro SQL Server dat](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Popisuje nástroje, které zjednodušují návrh, průzkum, testování a nasazení aplikací a databází propojených s daty.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) Popisuje architekturu ADO.NET a použití tříd ADO.NET ke správě aplikačních dat a interakci se zdroji dat a XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) V této části najdete popis postupu vytváření datových aplikací, které vývojářům umožňují programovat v koncepčním modelu místo přímého používání relační databáze.

 [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Popisuje, jak používat nástroj [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] k nasazení datových služeb na webu nebo v intranetu, který implementuje [protokol OData (Open Data Protocol)](https://www.odata.org/).

 [Data v řešeních pro systém Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Obsahuje odkazy na témata, která vysvětlují, jak fungují data v řešeních pro systém Office. To zahrnuje informace o programování orientovaném na schéma, ukládání dat do mezipaměti a přístupu k datům na straně serveru.

 [LINQ (jazykově integrovaný dotaz)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Popisuje možnosti dotazů integrované do C# a Visual Basic a společný model pro dotazování na relačních databázích, dokumentech XML, datových sadách a kolekcích v paměti.

 [Nástroje XML v aplikaci Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Popisuje práci s daty XML, ladění XSLT, .NET Framework funkcí XML a architektury dotazů XML.

 [Dokumenty a data XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Poskytuje přehled komplexní a integrované sady tříd, které pracují s dokumenty XML a daty v .NET Framework.
