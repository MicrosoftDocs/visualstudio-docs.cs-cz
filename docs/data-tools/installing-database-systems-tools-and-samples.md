---
title: Kompatibilita databáze
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfc3b6c3adc5c51cbbc4bc7d91338fd3595ec372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586403"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Kompatibilní databázové systémy pro Visual Studio

Pro vývoj aplikace připojené k datům v aplikaci Visual Studio obvykle nainstalujete databázový systém do místního vývojového počítače a pak nasadíte aplikaci a databázi do provozního prostředí, až budou připravené. Visual Studio nainstaluje na svém počítači SQL Server Express LocalDB jako součást úlohy **úložiště a zpracování dat** . Tato instance LocalDB je užitečná k rychlému a snadnému vývoji aplikací propojených s daty.

Aby byl databázový systém přístupný z aplikací .NET a viditelný v oknech Visual Studio Data Tools, musí mít poskytovatele dat ADO.NET. Poskytovatel musí specificky podporovat Entity Framework, pokud plánujete používat modely entit (Entity Data Model) v aplikaci .NET. Mnoho poskytovatelů je nabízeno prostřednictvím Správce balíčků NuGet nebo prostřednictvím Visual Studio Marketplace.

Pokud používáte rozhraní API služby Azure Storage, nainstalujte emulátory úložiště Azure do místního počítače během vývoje, abyste se vyhnuli poplatkům, dokud nebudete připraveni na nasazení do produkčního prostředí. Další informace najdete v tématu [použití emulátoru Azure Storage pro vývoj a testování](/azure/storage/common/storage-use-emulator).

Následující seznam obsahuje některé z oblíbených databázových systémů, které lze použít v projektech sady Visual Studio. Seznam není vyčerpávající. Seznam dodavatelů třetích stran, kteří nabízejí poskytovatele dat ADO.NET, kteří umožňují rozsáhlou integraci s nástroji sady Visual Studio, najdete v tématu [poskytovatelé dat ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server je nabídka databáze Microsoft nejdůležitější. SQL Server 2016 přináší převratný výkon, pokročilé zabezpečení a bohatou a integrovanou tvorbu sestav a analýz. Dodává se v různých edicích, které jsou navržené pro různá použití: z vysoce škálovatelné a vysoce výkonné obchodní analýzy, která se používá v jednom počítači. SQL Server Express je plně vybavená edice SQL Server, která je přizpůsobená pro redistribuci a vkládání.  LocalDB je zjednodušená edice SQL Server Express, která nevyžaduje žádnou konfiguraci a neběží v procesu vaší aplikace. Na [stránce pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)můžete stáhnout jeden nebo oba produkty. Mnohé příklady SQL v této části používají SQL Server LocalDB. SQL Server Management Studio (SSMS) je samostatná aplikace pro správu databází, která má více funkcí, než je k dispozici v sadě Visual Studio Průzkumník objektů systému SQL Server. Z předchozího odkazu můžete získat SSMS.

## <a name="oracle"></a>Oracle

Můžete si stáhnout placené nebo bezplatné edice databáze Oracle ze stránky [technologie Oracle pro síť](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) . Pro podporu Entity Framework a objekty TableAdapter v době návrhu budete potřebovat [nástroje Oracle Developer Tools for Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Ostatní oficiální produkty Oracle, včetně okamžitého klienta Oracle, jsou k dispozici prostřednictvím Správce balíčků NuGet. Ukázková schémata Oracle si můžete stáhnout podle pokynů v [online dokumentaci k Oracle](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL je oblíbený Open Source databázový systém, který se široce používá v podnicích a webech. Soubory ke stažení pro MySQL, MySQL pro Visual Studio a související produkty jsou k dispozici v [MySQL ve Windows](https://www.mysql.com/why-mysql/windows/). Třetí strany nabízejí různá rozšíření aplikace Visual Studio a samostatné aplikace pro správu pro MySQL. Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje**  >  **Správce balíčků NuGet**  >  **Správa balíčků NuGet pro řešení**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL je bezplatný Open Source objekt relační databázový systém. Pokud ho chcete nainstalovat ve Windows, můžete si ho stáhnout ze [stránky pro stažení PostgreSQL](https://www.postgresql.org/download/windows/). Můžete také vytvořit PostgreSQL ze zdrojového kódu. Základní systém PostgreSQL obsahuje rozhraní jazyka C. Mnohé třetí strany poskytují balíčky NuGet pro použití PostgreSQL z aplikací .NET. Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje**  >  **Správce balíčků NuGet**  >  **Správa balíčků NuGet pro řešení**). Nejoblíbenější balíček je možná [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite je vložený modul SQL Database, který běží ve vlastním procesu aplikace. Můžete si ho stáhnout ze [stránky pro stažení SQLite](https://www.sqlite.org/download.html). K dispozici je také řada balíčků NuGet třetích stran pro SQLite. Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje**  >  **Správce balíčků NuGet**  >  **Správa balíčků NuGet pro řešení**).

## <a name="firebird"></a>Firebird

Firebird je open source systém SQL Database. Můžete si ho stáhnout ze [stránky pro stažení Firebird](http://firebirdsql.org/en/downloads/). Poskytovatel dat ADO.NET je k dispozici prostřednictvím Správce balíčků NuGet.

## <a name="see-also"></a>Viz také

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Jak určit verzi a edici SQL Server a jejích komponent](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
