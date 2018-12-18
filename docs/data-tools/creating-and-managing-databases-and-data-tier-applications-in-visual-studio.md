---
title: Databázové projekty a projekty DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d8671c46cf2e88ab5d5797dd7a009ff29b953c4e
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281729"
---
# <a name="database-projects-and-data-tier-applications"></a>Databázové projekty a aplikace datové vrstvy

Databázové projekty můžete vytvářet nové databáze nové aplikace datové vrstvy (DAC) a k aktualizaci stávajících databází a aplikací datové vrstvy. Databázové projekty a projekty DAC umožňují použít verzi ovládacího prvku a projekt správy techniky k vývoji vaší databáze, jako v podstatě stejným způsobem, platí tyto techniky pro spravovaný nebo nativní kód. Může pomoct váš vývojový tým, správou změn databáze a databázové servery vytvořením projektu DAC, databázový projekt nebo Serverový projekt a vložení v rámci správy verzí. Členy týmu můžete pak rezervace souborů provádět, sestavit a otestovat změny v izolované vývojové prostředí, nebo izolovaného prostoru, než je sdílet s týmem. K zajištění kvality kódu, můžete dokončit váš tým a testovat všechny změny pro konkrétní verzi databáze v testovacím prostředí před nasazením změny do produkčního prostředí.

Seznam vlastností databáze, které podporuje aplikace datové vrstvy, naleznete v tématu [podporu objektů systému SQL Server DAC](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Pokud používáte funkce ve vaší databázi, které nejsou podporované aplikace datové vrstvy, místo toho používejte databázového projektu ke správě změn k vaší databázi.

## <a name="common-high-level-tasks"></a>Běžné úlohy vyšší úrovně

| Základní úlohy | Podpůrný obsah |
| - | - |
| **Spuštění vývoje aplikace datové vrstvy:** koncept aplikace datové vrstvy (DAC) byla zavedena v systému SQL Server 2008. DAC obsahuje definici pro databázi serveru SQL Server a podpůrné instance objektů, které jsou používány klient server nebo 3vrstvé aplikace. DAC obsahuje databázové objekty, jako jsou tabulky a zobrazení, společně s instanci entity, jako jsou přihlášení. Visual Studio můžete vytvořit projekt DAC, sestavení soubor balíčku DAC a odeslat soubor balíčku DAC správce databáze pro nasazení na instanci databázového stroje systému SQL Server. | - [Aplikace datové vrstvy](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Provádění databáze iterativní vývoj:** vývojáři mohli rezervovat částí projektu a jejich aktualizaci v izolované vývojové prostředí. Pomocí tohoto typu prostředí můžete otestovat provedené změny aniž by to ovlivnilo ostatní členové týmu. Po dokončení se změny, zkontrolujte soubory zpět do správy verzí, kde můžete získat provedené změny a sestavení a nasazení testovacího serveru ostatním členům týmu. | - [Vývoj projektů objektově orientovaný offline databáze (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Ladicí program Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Vytváření prototypů, ověření výsledcích testu a změny databáze skripty a objekty:** editoru jazyka Transact-SQL můžete použít k provádění kterékoli z těchto běžných úkolů. | - [Editory dotazu a text (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)