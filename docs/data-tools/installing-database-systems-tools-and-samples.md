---
title: Kompatibilitu databáze
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586403"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Kompatibilní databázové systémy pro sadu Visual Studio

K vývoji aplikace připojená data v sadě Visual Studio, obvykle instalace databáze systému na svém místním vývojovém počítači a pak nasadit aplikace a databáze do produkčního prostředí Jakmile jsou připravené. Visual Studio nainstaluje SQL Server Express LocalDB na svém počítači jako součást **ukládání a zpracování dat** pracovního vytížení. Tuto instanci LocalDB je užitečné pro vývoj aplikací připojených dat snadno a rychle.

Pro systém databáze byla přístupná z aplikací .NET a mají být zobrazeny v okna nástroje sady Visual Studio data musí mít poskytovatele dat ADO.NET. Zprostředkovatel musí specificky podporují Entity Framework, pokud budete chtít použít datových modelech Entity v aplikaci .NET. Pomocí Správce balíčků NuGet nebo Visual Studio Marketplace nabízí mnoho poskytovatelů.

Pokud používáte rozhraní API služby Azure storage, nainstalujte emulátory úložiště Azure na svém místním počítači během vývoje. aby nemuseli platit případné poplatky, dokud nebudete připraveni k nasazení do produkčního prostředí. Další informace najdete v tématu [použití emulátoru úložiště Azure pro vývoj a testování](/azure/storage/common/storage-use-emulator).

Následující seznam zahrnuje některé další oblíbené systémů databáze, které lze použít v projektech Visual Studio. Seznam není úplný. Seznam externích dodavatelů, které nabízí zprostředkovatelé dat ADO.NET, které umožňují těsně integrovaná se sadou nástrojů sady Visual Studio najdete v tématu [zprostředkovatele dat ADO.NET](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

Je nejdůležitější databáze Microsoft SQL Server nabízí. SQL Server 2016 přináší přelomový výkon, pokročilé zabezpečení a bohatě vybavené, integrované vytváření sestav a analýzy. Je dodáván v různých edicích, které jsou určeny pro různé účely: z vysoce škálovatelné a vysoce výkonnou obchodní analýzy, používat v jednom počítači. SQL Server Express je plně funkční edice SQL serveru, který je vytvořený na míru pro automatické distribuce signatur a vkládání.  LocalDB je zjednodušenou verzi systému SQL Server Express, která není nutné nic konfigurovat a běží v procesu vaší aplikace. Můžete si stáhnout nebo oba produkty [stránku pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Mnoho příkladů SQL v této části použijte SQL Server LocalDB. SQL Server Management Studio (SSMS) je aplikace pro řízení samostatné databáze, která má více funkcí, než co je k dispozici v Průzkumníku objektů serveru SQL sady Visual Studio. SSMS můžete získat z předchozího propojení.

## <a name="oracle"></a>Oracle

Můžete stáhnout placené nebo bezplatné edice databáze Oracle [síťové technologie Oracle](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html) stránky. Pro podporu návrhu pro Entity Framework a objekty TableAdapter, budete potřebovat [Oracle Developer tools for Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Další oficiální produkty Oracle, včetně klienta Oracle rychlého, jsou k dispozici prostřednictvím Správce balíčků NuGet. Ukázka schémat Oracle si můžete stáhnout podle pokynů v [online dokumentaci Oracle](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

MySQL je systém oblíbených open source databáze, která se běžně používá v podnicích a websites. Soubory ke stažení pro MySQL, MySQL pro Visual Studio a související produkty jsou na [MySQL na Windows](https://www.mysql.com/why-mysql/windows/). Třetích stran nabízejí různé rozšíření sady Visual Studio a aplikací pro samostatnou správu for MySQL. Můžete procházet nabídek ve správci balíčků NuGet (**nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL je zdarma, open source objektu relační databázový systém. K jeho instalaci na Windows, můžete sadu stáhnout z [stránku pro stažení PostgreSQL](https://www.postgresql.org/download/windows/). Můžete také sestavit PostgreSQL ze zdrojového kódu. Systém jádra PostgreSQL zahrnuje rozhraní jazyka C. Mnoho výrobců uveďte balíčky NuGet pro používání PostgreSQL v aplikacích .NET. Můžete procházet nabídek ve správci balíčků NuGet (**nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**) . Možná je poskytována balíček nejoblíbenější [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

SQLite je li vložený stroj SQL databáze, na kterém běží v procesu aplikace vlastní. Můžete ji stáhnout [stránku pro stažení SQLite](https://www.sqlite.org/download.html). Mnoho výrobců balíčky NuGet pro SQLite jsou také k dispozici. Můžete procházet nabídek ve správci balíčků NuGet (**nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**) .

## <a name="firebird"></a>Firebird

Firebird je open source systém databáze SQL. Můžete ji stáhnout [stránku pro stažení Firebird](http://firebirdsql.org/en/downloads/). Poskytovatele dat ADO.NET je k dispozici prostřednictvím Správce balíčků NuGet.

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Jak určit verzi a edici systému SQL Server a jeho součásti](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
