---
title: Instalace systémů databází, nástroje a ukázky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f18ace9a18eefd0758e581b83001b85c3f48a3da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244280"
---
# <a name="installing-database-systems-tools-and-samples"></a>Instalace systémů databází, nástroje a ukázky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Samotné sady Visual Studio nezahrnuje žádné databáze systémů než ty, které se používá interně. K vývoji aplikace připojená data v sadě Visual Studio, obvykle instalace databáze systému na svém místním vývojovém počítači a pak nasadit aplikace a databáze do produkčního prostředí Jakmile jsou připravené. Pro systém databáze byla přístupná z aplikací .NET a mají být zobrazeny v okna nástroje sady Visual Studio data musí mít poskytovatele dat ADO.NET. Zprostředkovatel musí specificky podporují Entity Framework, pokud budete chtít použít datových modelech Entity v aplikaci .NET.     Pomocí Správce balíčků NuGet nebo prostřednictvím Galerie sady Visual Studio nabízí mnoho poskytovatelů.  
  
 Pro vývoj pro SQL Ujistěte se, že máte nainstalované v sadě Visual Studio nástroje SQL Server Data Tools. Klikněte na tlačítko **zobrazení** nabídky. Pokud se nezobrazí Průzkumník objektů systému SQL Server, přejděte do ovládacích panelů a změňte sady Visual Studio. V instalačním programu, vyberte **Microsoft SQL Server Data Tools**.  
  
 Pokud používáte rozhraní API služby Azure Storage, nainstalujte emulátory úložiště Azure na svém místním počítači během vývoje. aby nemuseli platit případné poplatky, dokud nebudete připraveni k nasazení do produkčního prostředí. Další informace najdete v tématu [použití emulátoru úložiště Azure pro vývoj a testování](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/).  
  
 Následující seznam zahrnuje některé další oblíbené systémů databáze, které lze použít v projektech Visual Studio. Seznam není úplný. Seznam externích dodavatelů, které nabízí zprostředkovatelé dat ADO.NET, které umožňují těsně integrovaná se sadou nástrojů sady Visual Studio najdete v tématu [zprostředkovatele dat ADO.NET](https://msdn.microsoft.com/library/dd363565.aspx).  
  
### <a name="microsoft-sql-server"></a>Microsoft SQL Server  
 Je nejdůležitější databáze Microsoft SQL Server nabízí. SQL Server 2016 přináší přelomový výkon, pokročilé zabezpečení a bohatě vybavené, integrované vytváření sestav a analýzy. Je dodáván v různých edicích, které jsou určeny pro různé účely: z vysoce škálovatelné a vysoce výkonnou obchodní analýzy, používat v jednom počítači. SQL Server Express je plně funkční edice SQL serveru, který je vytvořený na míru pro automatické distribuce signatur a vkládání.  LocalDB je zjednodušenou verzi systému SQL Server Express, která není nutné nic konfigurovat a běží v procesu vaší aplikace. Můžete si stáhnout nebo oba produkty [stránce pro stažení SQL Server Express](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx).    Mnoho příkladů SQL v této části použijte SQL Server LocalDB. SQL Server Management Studio (SSMS) je aplikace pro řízení samostatné databáze, která má více funkcí, než co je k dispozici v Průzkumníku objektů serveru SQL sady Visual Studio. SSMS můžete získat z předchozího propojení.  
  
### <a name="oracle"></a>Oracle  
 Můžete stáhnout placené nebo bezplatné edice databáze Oracle [síťové technologie Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) stránky. Pro podporu návrhu pro Entity Framework a objekty TableAdapter, budete potřebovat [Oracle Developer Tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Další oficiální produkty Oracle, včetně klienta Oracle rychlého, jsou k dispozici prostřednictvím Správce balíčků NuGet.  Ukázka schémat Oracle si můžete stáhnout podle pokynů v [Online dokumentaci Oracle](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).  
  
### <a name="mysql"></a>MySQL  
 MySQL je systém oblíbených open source databáze, která se běžně používá v podnicích a websites. Soubory ke stažení pro MySQL, MySQL pro Visual Studio a související produkty jsou na [MySQL na Windows](http://www.mysql.com/why-mysql/windows/).  Třetích stran nabízejí různé rozšíření sady Visual Studio a aplikací pro samostatnou správu for MySQL. Můžete procházet nabídek ve správci balíčků NuGet (**nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**) .  
  
### <a name="postgresql"></a>PostgreSQL  
 PostgreSQL je zdarma, open source objektu relační databázový systém. K jeho instalaci na Windows, můžete sadu stáhnout z [stránku pro stažení PostgreSQL](http://www.postgresql.org/download/windows/).  Můžete také sestavit PostgreSQL ze zdrojového kódu.  Systém jádra PostgreSQL zahrnuje rozhraní jazyka C. Mnoho výrobců uveďte balíčky NuGet pro používání PostgreSQL v aplikacích .NET.  Můžete procházet nabídek ve správci balíčků NuGet (**nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**) . Možná je poskytována balíček nejoblíbenější [npgsql.org](http://www.npgsql.org).  
  
### <a name="sqlite"></a>SQLite  
 SQLite je li vložený stroj SQL databáze, na kterém běží v procesu aplikace vlastní. Můžete ji stáhnout [stránku pro stažení SQLite](http://www.sqlite.org/download.html). Mnoho výrobců balíčky NuGet pro SQLite jsou také k dispozici. Můžete procházet nabídek ve správci balíčků NuGet (**nástroje** > **Správce balíčků NuGet** > **spravovat balíčky NuGet pro řešení**) .  
  
### <a name="firebird"></a>Firebird  
 Firebird je open source systém databáze SQL. Můžete ji stáhnout [stránku pro stažení Firebird](http://firebirdsql.org/en/downloads/). Poskytovatele dat ADO.NET je k dispozici prostřednictvím Správce balíčků NuGet.  
  
## <a name="see-also"></a>Viz také  
 [Jak určit verzi a edici systému SQL Server a jeho součásti](http://support.microsoft.com/kb/321185)

