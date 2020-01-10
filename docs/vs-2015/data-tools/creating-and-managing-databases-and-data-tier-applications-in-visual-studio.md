---
title: Vytváření a Správa databází a aplikací datové vrstvy
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851687"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Vytváření a správa databází a aplikací datové vrstvy v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[DŮLEŽITÉ]
> Databázové projekty, které byly obsaženy v předchozích verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jsou teď součástí [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] nástroje. Další informace najdete v tématu [SQL Server Developer Tools](https://msdn.microsoft.com/library/hh272686(VS.103).aspx).

 Databázové projekty můžete vytvářet nové databáze nové aplikace datové vrstvy (DAC) a k aktualizaci stávajících databází a aplikací datové vrstvy. Databázové projekty a projekty DAC umožňují použít verzi ovládacího prvku a projekt správy techniky k vývoji vaší databáze, jako v podstatě stejným způsobem, platí tyto techniky pro spravovaný nebo nativní kód. Vám může pomoct váš vývojový tým, správou změn databáze a databázové servery tak, že vytvoříte *DAC projektu*, *databázový projekt*, nebo *serverový projekt* a vložení v systému správy verzí. Členy týmu můžete pak rezervace souborů vytvořit, sestavit a otestovat změny v *izolované vývojové prostředí*, nebo izolovaného prostoru, než je sdílet s týmem. K zajištění kvality kódu, můžete dokončit váš tým a testovat všechny změny pro konkrétní verzi databáze v testovacím prostředí před nasazením změny do produkčního prostředí.

 Seznam vlastností databáze, které podporuje aplikace datové vrstvy, naleznete v tématu [funkce podporovány v aplikace datové vrstvy](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) na webu společnosti Microsoft. Pokud používáte funkce ve vaší databázi, které nejsou podporované aplikace datové vrstvy, místo toho používejte databázového projektu ke správě změn k vaší databázi.

## <a name="common-high-level-tasks"></a>Běžné úlohy vyšší úrovně

|Základní úlohy|Podpůrný obsah|
|----------------------|------------------------|
|**Spuštění vývoje aplikace datové vrstvy:** A DAC je nový koncept nepředchází [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] , který obsahuje definici pro [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databázi a podpůrné instance objektů, které jsou používány klient server nebo vrstvy 3 aplikace. DAC obsahuje databázové objekty, jako jsou tabulky a zobrazení, společně s instanci entity, jako jsou přihlášení. Můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pro vytvoření projektu DAC DAC soubor balíčku, ale taky popustit odeslat tento soubor balíčku DAC správce databáze pro nasazení do instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databázového stroje.|-   [Vytváření a Správa aplikace datové vrstvy](https://msdn.microsoft.com/library/ee361996(VS.100).aspx) (web společnosti Microsoft)<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**Provádění databáze iterativní vývoj:** Pokud jste vývojář nebo tester, projděte si části projektu a potom je aktualizovat v izolované vývojové prostředí. Pomocí tohoto typu prostředí můžete otestovat provedené změny aniž by to ovlivnilo ostatní členové týmu. Po dokončení se změny, zkontrolujte soubory zpět do správy verzí, kde můžete získat provedené změny a sestavení a nasazení testovacího serveru ostatním členům týmu.|-   [Dotaz a textových editorů (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (web společnosti Microsoft)<br />-   [Ladicí program Transact-SQL](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (web společnosti Microsoft)|
|**Vytváření prototypů, ověření výsledcích testu a změny databáze skripty a objekty:** můžete použít [!INCLUDE[tsql](../includes/tsql-md.md)] editor k provádění kterékoli z těchto běžných úkolů.|-   [Dotaz a textových editorů (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (web společnosti Microsoft)|

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
