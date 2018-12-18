---
title: Konfigurace parametrů běhu zátěžových testů
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9aa2defb458fba0d7962813743fa603fe71081e2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053315"
---
# <a name="configure-load-test-run-settings"></a>Konfigurace parametrů spuštění zátěžového testu

*Nastavení spuštění* představují sadu vlastností ovlivňujících způsob běhu zátěžového testu. Parametry spuštění jsou uspořádány podle kategorií v **vlastnosti** okna.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

V rámci zátěžového testu, ale pouze jeden z parametrů běhu může být aktivní za běhu může mít více než jeden parametr spuštění. Další parametry spuštění poskytují rychlý způsob výběru alternativního nastavení pro následné běhy testu.

Počáteční parametr spuštění se vytvoří při vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**.

![Parametry spuštění zátěžového testu](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-|
|**Přidání dalších parametrů spuštění do zátěžového testu:** kromě nastavení spuštění, který je vytvořen při spuštění **nového Průvodce zátěžovým testem**, přidáním dalších parametrů spuštění do zátěžového testu tak, aby můžete spustit test v rámci různých podmínky.|-   [Postupy: přidání dalších parametrů běhu k zátěžovému testu](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Určení aktivního parametru spuštění pro zátěžový test:** vyberete parametr spuštění, který chcete používat se zátěžovým testem pomocí editoru zátěžového testu. Aktivní parametr spuštění lze rozpoznat pomocí přípony „[Active]“.|-   [Postupy: výběr aktivního parametru spuštění pro zátěžový test](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Úprava vlastností parametrů spuštění:** spuštění můžete upravit nastavení vlastností pro takové věci jako možnosti protokolování (Další informace naleznete níže), určení délky testu, dobu zahřívání, maximální počet chyb podrobnosti o ohlášených, vzorkovací frekvenci připojení Model (pouze testy webového výkonu), typ úložiště výsledků, úroveň validace a SQL trasování. Parametry spuštění by měly odrážet cíle zátěžového testu.|-   [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md)<br />-   [Změna vlastností nastavení spuštění](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Určení počtu iterací testu v spuštění zátěžového testu:** můžete určit počet, kolikrát chcete spustit všechny webového výkonu a testy jednotek ve všech scénářích zátěžových testů pomocí konfigurace **testovací iterace** Vlastnost.|-   [Postupy: určení počtu testovacích iterací v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Určení vzorkovací frekvence pro spuštění zátěžového testu:** můžete určit, jak často chcete, aby zátěžový test shromažďoval data čítačů výkonu tím, že nakonfigurujete **vzorkovací frekvence** vlastnost.|-   [Postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Zadejte možnosti úložiště podrobností časování:** můžete určit, jak chcete podrobnosti zátěžového testu uložen tím, že nakonfigurujete **úložiště podrobností časování** vlastnost.|-   [Postupy: určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Zadejte dobu uchování zdrojů testu:** urychlit test > Opravit > otestujeme cyklu zachováním testovací prostředky během zadaného období nastavením **doba uchování prostředků** vlastnost.|-   [Uchovávat prostředky pro urychlení zátěžové testování](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Použití kontextových parametrů:** můžete použít kontextové parametry pro parametrizaci řetězce. Například pokud zátěžový test obsahuje test výkonnosti webu, který používá parametrizované webový server, můžete přidat kontextový parametr parametrů spuštění, které se mapují na jiný server.|-   [Postupy: Přidání kontextových parametrů k parametrům spuštění](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurace vlastností protokolování testu:** můžete nakonfigurovat, jak často se data zapisují do protokolu, který je spojen s parametry spuštění zátěžového testu. To může být důležité při spouštění rozsáhlých nebo složitých zátěžových testů, protože protokol by mohl mít velikost několik gigabajtů.<br /><br /> Lze také nakonfigurovat, aby se soubor protokolu automaticky uložil při selhání zátěžového testu, což pomůže při ladění a analýze aplikace.|-   [Úprava nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md)|