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
ms.openlocfilehash: 2d6ed13f2e21ea6b9da82eb47afefdd16088e71d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672468"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Vytváření a správa databází a aplikací datové vrstvy v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VÝZNAMNÁ
> Databázové projekty, které byly součástí dřívějších verzí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], jsou nyní k dispozici v [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)]ch nástrojích. Další informace najdete v tématu [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126).

 Pomocí databázových projektů můžete vytvářet nové databáze, nové aplikace na datové vrstvě (DAC) a aktualizovat existující databáze a aplikace datové vrstvy. Jak databázové projekty, tak projekty DAC umožňují použít techniky řízení verzí a řízení projektů pro vaše úsilí při vývoji databáze mnohem stejným způsobem, jako byste tyto techniky použili pro spravovaný nebo nativní kód. Vašemu vývojovému týmu můžete spravovat změny databází a databázových serverů vytvořením *projektu DAC*, *databázového projektu*nebo *serverového projektu* a jeho vložením do správy verzí. Členové týmu si pak můžou rezervovat soubory pro vytváření, sestavování a testování změn v *izolovaném vývojovém prostředí*nebo v izolovaném prostoru (sandbox) před jejich sdílením s týmem. Aby se zajistila kvalita kódu, může váš tým dokončit a otestovat všechny změny konkrétní verze databáze v přípravném prostředí před nasazením změn do produkčního prostředí.

 Seznam funkcí databáze podporovaných aplikacemi datové vrstvy najdete v tématu [funkce podporované v aplikacích datové vrstvy](http://go.microsoft.com/fwlink/?LinkId=164239) na webu společnosti Microsoft. Pokud používáte funkce v databázi, které nejsou podporovány aplikacemi datové vrstvy, měli byste místo toho použít databázový projekt ke správě změn v databázi.

## <a name="common-high-level-tasks"></a>Běžné úlohy na nejvyšší úrovni

|Úloha vysoké úrovně|Podpůrný obsah|
|----------------------|------------------------|
|**Zahájení vývoje aplikace na datové vrstvě:** DAC je nový koncept představený s [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)], který obsahuje definici pro databázi [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a pomocné objekty instance používané aplikací typu klient-server nebo 3 vrstva. DAC zahrnuje databázové objekty, jako jsou tabulky a zobrazení, spolu s entitami instancí, jako jsou například přihlašovací údaje. Můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k vytvoření projektu DAC, sestavení souboru balíčku DAC a odeslání tohoto souboru balíčku DAC do správce databáze pro nasazení do instance databázového stroje [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [vytváření a Správa aplikací datové vrstvy](http://go.microsoft.com/fwlink/?LinkId=160741) (web Microsoftu)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Provádění iterativního vývoje databází:** Pokud jste vývojář nebo tester, můžete se podívat na části projektu a pak je aktualizovat v izolovaném vývojovém prostředí. Pomocí tohoto typu prostředí můžete testovat své změny bez ovlivnění ostatních členů týmu. Po dokončení změn se soubory vrátí zpět do správy verzí, kde ostatní členové týmu mohou získat vaše změny a sestavit je a nasadit na testovací server.|-   [dotazy a textové editory (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (web Microsoftu)<br />-   [ladicí program Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (web Microsoftu)|
|Vytváření **prototypů, ověřování výsledků testů a změna databázových skriptů a objektů:** K provedení některé z těchto běžných úloh můžete použít Editor [!INCLUDE[tsql](../includes/tsql-md.md)].|-   [dotazy a textové editory (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (web Microsoftu)|

## <a name="see-also"></a>Viz také
 [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
