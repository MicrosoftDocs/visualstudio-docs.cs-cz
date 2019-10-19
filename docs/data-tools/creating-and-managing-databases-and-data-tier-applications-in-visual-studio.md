---
title: Databázové projekty a projekty DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 11e60c43e2b9935f4aaf2ffcc5d5c7e3683665d1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648580"
---
# <a name="database-projects-and-data-tier-applications"></a>Databázové projekty a aplikace na datové vrstvě

Pomocí databázových projektů můžete vytvářet nové databáze, nové aplikace na datové vrstvě (DAC) a aktualizovat existující databáze a aplikace datové vrstvy. Jak databázové projekty, tak projekty DAC umožňují použít techniky řízení verzí a řízení projektů pro vaše úsilí při vývoji databáze mnohem stejným způsobem, jako byste tyto techniky použili pro spravovaný nebo nativní kód. Vašemu vývojovému týmu můžete spravovat změny databází a databázových serverů vytvořením projektu DAC, databázového projektu nebo serverového projektu a jeho vložením do správy verzí. Členové týmu si pak můžou rezervovat soubory pro vytváření, sestavování a testování změn v izolovaném vývojovém prostředí nebo v izolovaném prostoru (sandbox) před jejich sdílením s týmem. Aby se zajistila kvalita kódu, může váš tým dokončit a otestovat všechny změny konkrétní verze databáze v přípravném prostředí před nasazením změn do produkčního prostředí.

Seznam funkcí databáze podporovaných aplikacemi datové vrstvy najdete v tématu [DAC Support for SQL Server Objects](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Pokud používáte funkce v databázi, které nejsou podporovány aplikacemi datové vrstvy, měli byste místo toho použít databázový projekt ke správě změn v databázi.

## <a name="common-high-level-tasks"></a>Běžné úlohy na nejvyšší úrovni

| Úloha vysoké úrovně | Podpůrný obsah |
| - | - |
| **Zahájení vývoje aplikace na datové vrstvě:** Koncept aplikace na datové vrstvě (DAC) byl představený s SQL Server 2008. DAC obsahuje definici pro SQL Server databázi a pomocné objekty instance používané aplikací typu klient-server nebo 3 vrstva. DAC zahrnuje databázové objekty, jako jsou tabulky a zobrazení, spolu s entitami instancí, jako jsou například přihlašovací údaje. Sadu Visual Studio můžete použít k vytvoření projektu DAC, sestavení souboru balíčku DAC a odeslání souboru balíčku DAC správci databáze pro nasazení do instance databázového stroje SQL Server. | - [aplikací datové vrstvy](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Provádění iterativního vývoje databází:** Vývojáři mohou rezervovat části projektu a aktualizovat je v izolovaném vývojovém prostředí. Pomocí tohoto typu prostředí můžete testovat své změny bez ovlivnění ostatních členů týmu. Po dokončení změn se soubory vrátí zpět do správy verzí, kde ostatní členové týmu mohou získat vaše změny a sestavit je a nasadit na testovací server. | - [Vývoj offline databází orientovaný na projekt (nástroje SQL Server data)](/sql/ssdt/project-oriented-offline-database-development)<br />- [ladicí program Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| Vytváření **prototypů, ověřování výsledků testů a změna databázových skriptů a objektů:** K provedení některé z těchto běžných úloh můžete použít editor Transact-SQL. | - [Editor dotazů a textu (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)