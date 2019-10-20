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
ms.openlocfilehash: 6f260af17a2fab142c5f5fa58e4ed267dc469d9f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651498"
---
# <a name="installing-database-systems-tools-and-samples"></a>Instalace databázových systémů, nástrojů a ukázek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio sám o sobě neobsahuje žádné databázové systémy, které používají interně. Pro vývoj aplikace připojené k datům v aplikaci Visual Studio obvykle nainstalujete databázový systém do místního vývojového počítače a pak nasadíte aplikaci a databázi do provozního prostředí, až budou připravené. Aby byl databázový systém přístupný z aplikací .NET a viditelný v oknech Visual Studio Data Tools, musí mít poskytovatele dat ADO.NET. Poskytovatel musí specificky podporovat Entity Framework, pokud plánujete používat modely entit (Entity Data Model) v aplikaci .NET.     Mnoho poskytovatelů je nabízeno prostřednictvím Správce balíčků NuGet nebo pomocí galerie sady Visual Studio.

 V případě vývoje SQL se ujistěte, že máte nainstalované nástroje pro SQL Server dat v aplikaci Visual Studio. Klikněte na nabídku **zobrazení** . Pokud nevidíte Průzkumník objektů systému SQL Server, přejděte do ovládacích panelů a změňte aplikaci Visual Studio. V instalačním programu vyberte **Microsoft SQL Server Data Tools**.

 Pokud používáte rozhraní Azure Storage API, nainstalujte emulátory úložiště Azure do místního počítače během vývoje, abyste se vyhnuli poplatkům, dokud nebudete připraveni na nasazení do produkčního prostředí. Další informace najdete v tématu [použití emulátoru Azure Storage pro vývoj a testování](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 Následující seznam obsahuje některé z oblíbených databázových systémů, které lze použít v projektech sady Visual Studio. Seznam není vyčerpávající. Seznam dodavatelů třetích stran, kteří nabízejí poskytovatele dat ADO.NET, kteří umožňují rozsáhlou integraci s nástroji sady Visual Studio, najdete v tématu [poskytovatelé dat ADO.NET](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server je nabídka databáze Microsoft nejdůležitější. SQL Server 2016 přináší převratný výkon, pokročilé zabezpečení a bohatou a integrovanou tvorbu sestav a analýz. Dodává se v různých edicích, které jsou navržené pro různá použití: z vysoce škálovatelné a vysoce výkonné obchodní analýzy, která se používá v jednom počítači. SQL Server Express je plně vybavená edice SQL Server, která je přizpůsobená pro redistribuci a vkládání.  LocalDB je zjednodušená edice SQL Server Express, která nevyžaduje žádnou konfiguraci a neběží v procesu vaší aplikace. [Na stránce pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)můžete stáhnout jeden nebo oba produkty. Mnohé příklady SQL v této části používají SQL Server LocalDB. SQL Server Management Studio (SSMS) je samostatná aplikace pro správu databází, která má více funkcí, než je k dispozici v sadě Visual Studio Průzkumník objektů systému SQL Server. Z předchozího odkazu můžete získat SSMS.

### <a name="oracle"></a>Oracle
 Můžete si stáhnout placené nebo bezplatné edice databáze Oracle ze stránky [technologie Oracle pro síť](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) . Pro podporu Entity Framework a objekty TableAdapter v době návrhu budete potřebovat [Oracle vývojářské nástroje pro Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Ostatní oficiální produkty Oracle, včetně okamžitého klienta Oracle, jsou k dispozici prostřednictvím Správce balíčků NuGet.  Ukázková schémata Oracle si můžete stáhnout podle pokynů v [online dokumentaci k Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

### <a name="mysql"></a>MySQL
 MySQL je oblíbený Open Source databázový systém, který se široce používá v podnicích a webech. Soubory ke stažení pro MySQL, MySQL pro Visual Studio a související produkty jsou k dispozici v [MySQL ve Windows](http://www.mysql.com/why-mysql/windows/).  Třetí strany nabízejí různá rozšíření aplikace Visual Studio a samostatné aplikace pro správu pro MySQL. Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje**  > **správce balíčků NuGet**  > **Spravovat balíčky NuGet pro řešení**).

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL je bezplatný Open Source objekt relační databázový systém. Pokud ho chcete nainstalovat ve Windows, můžete si ho stáhnout ze [stránky pro stažení PostgreSQL](http://www.postgresql.org/download/windows/).  Můžete také vytvořit PostgreSQL ze zdrojového kódu.  Základní systém PostgreSQL obsahuje rozhraní jazyka C. Mnohé třetí strany poskytují balíčky NuGet pro použití PostgreSQL z aplikací .NET.  Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje**  > **správce balíčků NuGet**  > **Spravovat balíčky NuGet pro řešení**). Možná je nejoblíbenější balíček poskytovaný nástrojem [npgsql.org](http://www.npgsql.org).

### <a name="sqlite"></a>SQLite
 SQLite je vložený modul SQL Database, který běží ve vlastním procesu aplikace. Můžete si ho stáhnout ze [stránky pro stažení SQLite](http://www.sqlite.org/download.html). K dispozici je také řada balíčků NuGet třetích stran pro SQLite. Nabídky můžete procházet ve Správci balíčků NuGet (**nástroje**  > **správce balíčků NuGet**  > **Spravovat balíčky NuGet pro řešení**).

### <a name="firebird"></a>Firebird
 Firebird je open source systém SQL Database. Můžete si ho stáhnout ze [stránky pro stažení Firebird](http://firebirdsql.org/en/downloads/). Poskytovatel dat ADO.NET je k dispozici prostřednictvím Správce balíčků NuGet.

## <a name="see-also"></a>Viz také
 [Jak určit verzi a edici SQL Server a jejích komponent](http://support.microsoft.com/kb/321185)
