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
ms.openlocfilehash: c2b1caf45235f9dd745841cb26a2fa10a148a7b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299638"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Vytváření a Správa databází a aplikací datové vrstvy v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[DŮLEŽITÉ]
> Databázové projekty, které byly součástí dřívějších verzí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], jsou nyní k dispozici v [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]ch nástrojích. Další informace najdete v tématu [SQL Server Developer Tools](https://go.microsoft.com/fwlink/?LinkId=228126).

 Databázové projekty můžete vytvářet nové databáze nové aplikace datové vrstvy (DAC) a k aktualizaci stávajících databází a aplikací datové vrstvy. Databázové projekty a projekty DAC umožňují použít verzi ovládacího prvku a projekt správy techniky k vývoji vaší databáze, jako v podstatě stejným způsobem, platí tyto techniky pro spravovaný nebo nativní kód. Vašemu vývojovému týmu můžete spravovat změny databází a databázových serverů vytvořením *projektu DAC*, *databázového projektu*nebo *serverového projektu* a jeho vložením do správy verzí. Členové týmu si pak můžou rezervovat soubory pro vytváření, sestavování a testování změn v *izolovaném vývojovém prostředí*nebo v izolovaném prostoru (sandbox) před jejich sdílením s týmem. K zajištění kvality kódu, můžete dokončit váš tým a testovat všechny změny pro konkrétní verzi databáze v testovacím prostředí před nasazením změny do produkčního prostředí.

 Seznam funkcí databáze podporovaných aplikacemi datové vrstvy najdete v tématu [funkce podporované v aplikacích datové vrstvy](https://go.microsoft.com/fwlink/?LinkId=164239) na webu společnosti Microsoft. Pokud používáte funkce ve vaší databázi, které nejsou podporované aplikace datové vrstvy, místo toho používejte databázového projektu ke správě změn k vaší databázi.

## <a name="common-high-level-tasks"></a>Běžné úlohy vyšší úrovně

|Základní úlohy|Podpůrný obsah|
|----------------------|------------------------|
|**Zahájení vývoje aplikace na datové vrstvě:** DAC je nový koncept představený s [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)], který obsahuje definici pro databázi [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a pomocné objekty instance používané aplikací typu klient-server nebo 3 vrstva. DAC obsahuje databázové objekty, jako jsou tabulky a zobrazení, společně s instanci entity, jako jsou přihlášení. Můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k vytvoření projektu DAC, sestavení souboru balíčku DAC a odeslání tohoto souboru balíčku DAC do správce databáze pro nasazení do instance databázového stroje [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [vytváření a Správa aplikací datové vrstvy](https://go.microsoft.com/fwlink/?LinkId=160741) (web Microsoftu)<br />-   [SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=227328)|
|**Provádění iterativního vývoje databází:** Pokud jste vývojář nebo tester, můžete se podívat na části projektu a pak je aktualizovat v izolovaném vývojovém prostředí. Pomocí tohoto typu prostředí můžete otestovat provedené změny aniž by to ovlivnilo ostatní členové týmu. Po dokončení se změny, zkontrolujte soubory zpět do správy verzí, kde můžete získat provedené změny a sestavení a nasazení testovacího serveru ostatním členům týmu.|-   [dotazy a textové editory (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (web Microsoftu)<br />-   [ladicí program Transact-SQL](https://go.microsoft.com/fwlink/?LinkId=227324) (web Microsoftu)|
|Vytváření **prototypů, ověřování výsledků testů a změna databázových skriptů a objektů:** K provedení některé z těchto běžných úloh můžete použít Editor [!INCLUDE[tsql](../includes/tsql-md.md)].|-   [dotazy a textové editory (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (web Microsoftu)|

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
