---
title: Databázové projekty a projekty DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8d32ddcc332264278cf76392ac69a6188ca51c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586728"
---
# <a name="database-projects-and-data-tier-applications"></a>Databázové projekty a aplikace na datové vrstvě

Databázové projekty můžete vytvářet nové databáze nové aplikace datové vrstvy (DAC) a k aktualizaci stávajících databází a aplikací datové vrstvy. Databázové projekty a projekty DAC umožňují použít verzi ovládacího prvku a projekt správy techniky k vývoji vaší databáze, jako v podstatě stejným způsobem, platí tyto techniky pro spravovaný nebo nativní kód. Vašemu vývojovému týmu můžete spravovat změny databází a databázových serverů vytvořením projektu DAC, databázového projektu nebo serverového projektu a jeho vložením do správy verzí. Členové týmu si pak můžou rezervovat soubory pro vytváření, sestavování a testování změn v izolovaném vývojovém prostředí nebo v izolovaném prostoru (sandbox) před jejich sdílením s týmem. K zajištění kvality kódu, můžete dokončit váš tým a testovat všechny změny pro konkrétní verzi databáze v testovacím prostředí před nasazením změny do produkčního prostředí.

Seznam funkcí databáze podporovaných aplikacemi datové vrstvy najdete v tématu [DAC Support for SQL Server Objects](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Pokud používáte funkce v databázi, které nejsou podporovány aplikacemi datové vrstvy, měli byste místo toho použít databázový projekt ke správě změn v databázi.

## <a name="common-high-level-tasks"></a>Běžné úlohy na nejvyšší úrovni

| Základní úlohy | Podpůrný obsah |
| - | - |
| **Zahájení vývoje aplikace na datové vrstvě:** Koncept aplikace na datové vrstvě (DAC) byl představený s SQL Server 2008. DAC obsahuje definici pro SQL Server databázi a pomocné objekty instance používané aplikací typu klient-server nebo 3 vrstva. DAC obsahuje databázové objekty, jako jsou tabulky a zobrazení, společně s instanci entity, jako jsou přihlášení. Sadu Visual Studio můžete použít k vytvoření projektu DAC, sestavení souboru balíčku DAC a odeslání souboru balíčku DAC správci databáze pro nasazení do instance databázového stroje SQL Server. | - [aplikací datové vrstvy](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Provádění iterativního vývoje databází:** Vývojáři mohou rezervovat části projektu a aktualizovat je v izolovaném vývojovém prostředí. Pomocí tohoto typu prostředí můžete testovat své změny bez ovlivnění ostatních členů týmu. Po dokončení se změny, zkontrolujte soubory zpět do správy verzí, kde můžete získat provedené změny a sestavení a nasazení testovacího serveru ostatním členům týmu. | - [Vývoj offline databází orientovaný na projekt (nástroje SQL Server data)](/sql/ssdt/project-oriented-offline-database-development)<br />- [ladicí program Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| Vytváření **prototypů, ověřování výsledků testů a změna databázových skriptů a objektů:** K provedení některé z těchto běžných úloh můžete použít editor Transact-SQL. | - [Editor dotazů a textu (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
