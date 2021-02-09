---
title: Spravovat Výsledky testů zatížení
description: Naučte se spravovat data shromážděná během zátěžového testu, který je uložený v databázi SQL úložiště Load Výsledky testů.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 5245ccdb9130d3fac9639e7befc63ee2a5ebf70a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887611"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Správa výsledků zátěžového testu v úložišti Výsledky testů zatížení

Při spuštění zátěžových testů mohou být všechny informace shromážděné během zátěžového testu uloženy v *úložišti výsledky testů zatížení*, což je databáze SQL. Úložiště Load Výsledky testů obsahuje data čítače výkonu a veškeré informace o zaznamenaných chybách. Databáze úložiště výsledků je vytvořena instalačním programem pro řadiče nebo vytvořena automaticky při prvním místním spuštění zátěžového testu. Pro místní spuštění se databáze vytvoří automaticky, pokud není k dispozici schéma zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pokud upravíte připojovací řetězec úložiště výsledků kontroleru na použití jiného serveru, musí mít nový server spuštěný skript *loadtestresultsrepository. SQL* pro vytvoření schématu.

Visual Studio Enterprise poskytuje pojmenované sady čítačů, které shromažďují běžné čítače výkonu založené na technologii. Tyto sady jsou užitečné při analýze serveru služby IIS, serveru ASP.NET nebo SQL serveru. Všechna data shromážděná pomocí sad čítačů jsou uložena v úložišti Výsledky testů zatížení.

> [!IMPORTANT]
> Mezi sadou čítačů a daty čítače výkonu je rozdíl. Sada čítačů je metadata. Definuje skupinu čítačů výkonu, které by měly být shromažďovány z počítače, který provádí určitou roli, jako je například služba IIS nebo SQL Server. Sada čítačů je součástí definice zátěžového testu. Data čítače výkonu se shromažďují na základě sad čítačů, mapování nastaveného na konkrétní počítač a vzorkovací frekvence.

## <a name="sql-server-versions"></a>Verze SQL Serveru

Chcete-li použít zátěžové testy, můžete použít SQL Server Express LocalDB, která je nainstalována se sadou Visual Studio. Je výchozím databázovým serverem pro zátěžové testy (včetně integrace aplikace Microsoft Excel). SQL Server Express LocalDB je režim spouštění SQL Server Express, který je cílen vývojářům programu. Instalace SQL Server Express LocalDB kopíruje minimální sadu souborů nezbytných ke spuštění databázového stroje SQL Server.

Pokud váš tým očekává náročné požadavky databáze nebo pokud vaše projekty přesáhne SQL Server Express LocalDB, měli byste zvážit upgrade na SQL Express nebo úplné SQL Server a poskytnout tak další možnosti škálování. Pokud upgradujete SQL Server, soubory MDF a LDF pro SQL Server Express LocalDB budou uloženy ve složce profilu uživatele. Tyto soubory lze použít k importu databáze zátěžového testu do SQL Server Express nebo SQL Server.

## <a name="load-test-results-store-considerations"></a>Požadavky na úložiště výsledků zátěžového testu

Při instalaci Visual Studio Enterprise je úložiště výsledků zátěžového testu nastaveno na použití instance SQL Express, která je nainstalována v počítači. SQL Express je omezen na použití maximálně 4 GB místa na disku. Pokud budete spouštět mnoho zátěžových testů po dlouhou dobu, měli byste zvážit konfiguraci úložiště výsledků zátěžového testu pro použití instance úplného SQL Server produktu, pokud je k dispozici.

## <a name="load-test-analyzer-tasks"></a>Úlohy analyzátoru zátěžového testu

|Úlohy|Přidružená témata|
|-|-----------------------|
|**Nastavte úložiště výsledků zátěžového testu:** V databázi SQL můžete nastavit úložiště výsledků zátěžového testu. **Poznámka:**  Úložiště zátěžového testu lze také vytvořit při instalaci kontroleru testů. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).||
|**Výběr a zobrazení úložiště výsledků:** Můžete vybrat konkrétní úložiště výsledků. Nejste omezeni na místní úložiště výsledků. Zátěžové testy jsou často spouštěny ve vzdálené sadě počítačů agenta. Výsledky testů z agentů nebo místního počítače lze uložit na jakýkoli SQL Server, na kterém jste vytvořili úložiště výsledků zátěžového testu. V obou případech je nutné určit, kam se mají ukládat výsledky zátěžového testu, pomocí okna **Spravovat testovací kontroléry** .|-   [Postupy: výběr úložiště výsledků zátěžového testu](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Postupy: přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)|
|**Odstraňování výsledků zátěžového testu z úložiště:** Výsledek zátěžového testu můžete z **Editor zátěžového testu** odebrat pomocí dialogového okna **otevřít a spravovat výsledky testů Load** .|-   [Postupy: odstranění výsledků zátěžového testu z úložiště](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Importovat a exportovat výsledky do úložiště:** Můžete importovat a exportovat výsledky zátěžových testů z **Editor zátěžového testu**.|-   [Postupy: Import výsledků zátěžového testu do úložiště](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Postupy: Export výsledků zátěžového testu z úložiště](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Související úlohy

[Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

Výsledky spuštění zátěžového testu a dokončeného zátěžového testu můžete zobrazit pomocí **analyzátoru zátěžového testu**.

## <a name="see-also"></a>Viz také

- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)
