---
title: Instalace databázových systémů, nástrojů a ukázek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299602"
---
# <a name="installing-database-systems-tools-and-samples"></a>Instalace databázových systémů, nástrojů a ukázek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio sám o sobě neobsahuje žádné databázové systémy, které používají interně. K vývoji aplikace připojená data v sadě Visual Studio, obvykle instalace databáze systému na svém místním vývojovém počítači a pak nasadit aplikace a databáze do produkčního prostředí Jakmile jsou připravené. Aby byl databázový systém přístupný z aplikací .NET a viditelný v oknech Visual Studio Data Tools, musí mít poskytovatele dat ADO.NET. Zprostředkovatel musí specificky podporují Entity Framework, pokud budete chtít použít datových modelech Entity v aplikaci .NET.     Mnoho poskytovatelů je nabízeno prostřednictvím Správce balíčků NuGet nebo pomocí galerie sady Visual Studio.

 V případě vývoje SQL se ujistěte, že máte nainstalované nástroje pro SQL Server dat v aplikaci Visual Studio. Klikněte na nabídku **zobrazení** . Pokud nevidíte Průzkumník objektů systému SQL Server, přejděte do ovládacích panelů a změňte aplikaci Visual Studio. V instalačním programu vyberte **Microsoft SQL Server Data Tools**.

 Pokud používáte rozhraní Azure Storage API, nainstalujte emulátory úložiště Azure do místního počítače během vývoje, abyste se vyhnuli poplatkům, dokud nebudete připraveni na nasazení do produkčního prostředí. Další informace najdete v tématu [použití emulátoru Azure Storage pro vývoj a testování](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 Následující seznam zahrnuje některé další oblíbené systémů databáze, které lze použít v projektech Visual Studio. Seznam není úplný. Seznam dodavatelů třetích stran, kteří nabízejí poskytovatele dat ADO.NET, kteří umožňují rozsáhlou integraci s nástroji sady Visual Studio, najdete v tématu [poskytovatelé dat ADO.NET](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 Je nejdůležitější databáze Microsoft SQL Server nabízí. SQL Server 2016 přináší přelomový výkon, pokročilé zabezpečení a bohatě vybavené, integrované vytváření sestav a analýzy. Je dodáván v různých edicích, které jsou určeny pro různé účely: z vysoce škálovatelné a vysoce výkonnou obchodní analýzy, používat v jednom počítači. SQL Server Express je plně funkční edice SQL serveru, který je vytvořený na míru pro automatické distribuce signatur a vkládání.  LocalDB je zjednodušenou verzi systému SQL Server Express, která není nutné nic konfigurovat a běží v procesu vaší aplikace. [Na stránce pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)můžete stáhnout jeden nebo oba produkty. Mnoho příkladů SQL v této části použijte SQL Server LocalDB. SQL Server Management Studio (SSMS) je aplikace pro řízení samostatné databáze, která má více funkcí, než co je k dispozici v Průzkumníku objektů serveru SQL sady Visual Studio. SSMS můžete získat z předchozího propojení.

### <a name="oracle"></a>Oracle
 Můžete si stáhnout placené nebo bezplatné edice databáze Oracle ze stránky [technologie Oracle pro síť](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) . Pro podporu Entity Framework a objekty TableAdapter v době návrhu budete potřebovat [Oracle vývojářské nástroje pro Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Další oficiální produkty Oracle, včetně klienta Oracle rychlého, jsou k dispozici prostřednictvím Správce balíčků NuGet.  Ukázková schémata Oracle si můžete stáhnout podle pokynů v [online dokumentaci k Oracle](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

### <a name="mysql"></a>MySQL
 MySQL je systém oblíbených open source databáze, která se běžně používá v podnicích a websites. Soubory ke stažení pro MySQL, MySQL pro Visual Studio a související produkty jsou k dispozici v [MySQL ve Windows](https://www.mysql.com/why-mysql/windows/).  Třetích stran nabízejí různé rozšíření sady Visual Studio a aplikací pro samostatnou správu for MySQL. Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**).

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL je zdarma, open source objektu relační databázový systém. Pokud ho chcete nainstalovat ve Windows, můžete si ho stáhnout ze [stránky pro stažení PostgreSQL](http://www.postgresql.org/download/windows/).  Můžete také sestavit PostgreSQL ze zdrojového kódu.  Systém jádra PostgreSQL zahrnuje rozhraní jazyka C. Mnoho výrobců uveďte balíčky NuGet pro používání PostgreSQL v aplikacích .NET.  Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**). Možná je nejoblíbenější balíček poskytovaný nástrojem [npgsql.org](http://www.npgsql.org/).

### <a name="sqlite"></a>SQLite
 SQLite je li vložený stroj SQL databáze, na kterém běží v procesu aplikace vlastní. Můžete si ho stáhnout ze [stránky pro stažení SQLite](http://www.sqlite.org/download.html). Mnoho výrobců balíčky NuGet pro SQLite jsou také k dispozici. Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje** > **správce balíčků NuGet** > **Spravovat balíčky NuGet pro řešení**).

### <a name="firebird"></a>Firebird
 Firebird je open source systém databáze SQL. Můžete si ho stáhnout ze [stránky pro stažení Firebird](http://firebirdsql.org/en/downloads/). Poskytovatele dat ADO.NET je k dispozici prostřednictvím Správce balíčků NuGet.

## <a name="see-also"></a>Viz také
 [Jak určit verzi a edici SQL Server a jejích komponent](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
