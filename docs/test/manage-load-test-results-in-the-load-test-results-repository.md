---
title: Správa výsledků zátěžových testů
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd0562a6cceeb50d43222a7850de11d52b0587cf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584423"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů

Při spuštění zátěžových testů mohou být všechny informace shromážděné během spuštění zátěžového testu uloženy v *úložišti výsledků zátěžového testu*, což je databáze SQL. Úložiště výsledků zátěžových testů obsahuje data čítačů výkonu a veškeré informace o zaznamenaných chybách. Databáze úložiště výsledků je vytvořena nastavením pro řadiče nebo automaticky vytvořena při prvním místním spuštění zátěžového testu. Pro místní spuštění databáze bude vytvořena automaticky, pokud schéma zátěžového testu není k dispozici.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pokud změníte připojovací řetězec úložiště výsledků řadiče tak, aby používal jiný server, musí být nový server spuštěn skript *loadtestresultsrepository.sql,* aby bylo schéma spuštěno.

Visual Studio Enterprise poskytuje pojmenované sady čítačů, které shromažďují běžné čítače výkonu založené na technologii. Tyto sady jsou užitečné při analýze serveru služby IIS, serveru ASP.NET nebo serveru SQL. Všechna data shromážděná pomocí sad čítačů jsou uložena v úložišti výsledků zátěžových testů.

> [!IMPORTANT]
> Existuje rozdíl mezi sadou čítačů a daty čítače výkonu. Sada čítačů jsou metadata. Definuje skupinu čítačů výkonu, které by měly být shromažďovány z počítače, který plní určitou roli, jako je služba IIS nebo SQL Server. Sada čítačů je součástí definice zátěžového testu. Data čítače výkonu jsou shromažďována na základě sad čítačů, mapování čítače nastaveného na konkrétní počítač a vzorkovací frekvence.

## <a name="sql-server-versions"></a>Verze SQL Serveru

Chcete-li použít zátěžové testy, můžete použít SQL Server Express LocalDB, který je nainstalován s Visual Studio. Jedná se o výchozí databázový server pro zátěžové testy (včetně integrace aplikace Microsoft Excel). SQL Server Express LocalDB je režim spuštění SQL Server Express, který je určen pro vývojáře programů. Instalace LOCALDB serveru SQL Server Express zkopíruje minimální sadu souborů potřebných ke spuštění databázového stroje serveru SQL Server.

Pokud váš tým očekává náročné potřeby databáze nebo vaše projekty přerůst SQL Server Express LocalDB, měli byste zvážit upgrade na SQL Express nebo úplné SQL Server poskytnout další škálování potenciál. Pokud inovujete SQL Server, soubory MDF a LDF pro SQL Server Express LocalDB jsou uloženy ve složce profilu uživatele. Tyto soubory lze použít k importu databáze zátěžového testu do SQL Server Express nebo SQL Server.

## <a name="load-test-results-store-considerations"></a>Důležité informace o uložení výsledků zátěžových testů

Při instalaci visual studio enterprise je úložiště výsledků zátěžového testu nastaveno tak, aby používalo instanci sql express, která je nainstalována v počítači. SQL Express je omezena na použití maximálně 4 GB místa na disku. Pokud spustíte mnoho zátěžových testů po dlouhou dobu, měli byste zvážit konfiguraci úložiště výsledků zátěžového testu tak, aby používalo instanci úplného produktu SQL Server, pokud je k dispozici.

## <a name="load-test-analyzer-tasks"></a>Úlohy analyzátoru zátěžového testu

|Úlohy|Přidružená témata|
|-|-----------------------|
|**Nastavení úložiště výsledků zátěžových testů:** Můžete nastavit úložiště výsledků zátěžového testu v databázi SQL. **Poznámka:**  Úložiště zátěžového testu lze také vytvořit při instalaci testovacího řadiče. Další informace naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).||
|**Výběr a zobrazení úložiště výsledků:** Můžete vybrat konkrétní úložiště výsledků. Nejste omezeni na místní úložiště výsledků. Zátěžové testy jsou často spouštěny ve vzdálené sadě počítačů agenta. Výsledky testů z vašich agentů nebo místního počítače lze uložit na libovolný server SQL, na kterém jste vytvořili úložiště výsledků zátěžového testu. V obou případech je nutné určit, kam uložit výsledky zátěžového testu pomocí okna **Spravovat testovací řadiče.**|-   [Postup: Výběr úložiště výsledků zátěžového testu](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Postup: Přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)|
|**Odstranění výsledku zátěžového testu z úložiště:** Výsledek zátěžového testu můžete z **Editoru zátěžového testu** odebrat pomocí dialogového okna **Otevřít a spravovat výsledky zátěžového testu.**|-   [Postup: Odstranění výsledků zátěžového testu z úložiště](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Import a export výsledků do úložiště:** Výsledky zátěžového testu můžete importovat a exportovat z **Editoru zátěžového testu**.|-   [Postup: Import výsledků zátěžového testu do úložiště](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Postup: Export výsledků zátěžového testu z úložiště](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Související úlohy

[Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

Výsledky průběžného zátěžového testu i dokončeného zátěžového testu můžete zobrazit pomocí **analyzátoru zátěžového testu**.

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postup: Přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)
