---
title: Konfigurace parametrů běhu zátěžových testů
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ffc9d6c2e563fcd16a61e91eaa94889de8607efc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595979"
---
# <a name="configure-load-test-run-settings"></a>Konfigurace nastavení spuštění zátěžového testu

*Nastavení spuštění* jsou sada vlastností, které ovlivňují způsob spuštění zátěžového testu. Nastavení spuštění jsou uspořádána podle kategorií v okně **Vlastnosti.**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

V zátěžovém testu můžete mít více než jedno nastavení spuštění, ale pouze jedno nastavení spuštění může být aktivní na spuštění. Další parametry spuštění poskytují rychlý způsob výběru alternativního nastavení pro následné běhy testu.

Počáteční nastavení spuštění je vytvořeno při vytvoření zátěžového testu pomocí **Průvodce novým zátěžového testu**.

![Parametry spuštění zátěžového testu](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-|
|**Přidejte další nastavení spuštění do zátěžového testu:** Kromě nastavení spuštění, které je vytvořeno při spuštění **Průvodce novým zátěžového testu**, můžete do zátěžového testu přidat další nastavení spuštění, abyste mohli spustit test za různých podmínek.|-   [Postup: Přidání dalších nastavení spuštění do zátěžového testu](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Určete nastavení aktivního spuštění, které se má použít při zátěžovém testu:** Pomocí editoru zátěžového testu můžete vybrat nastavení spuštění, které chcete použít se zátěžovým testem. Aktivní parametr spuštění lze rozpoznat pomocí přípony „[Active]“.|-   [Postup: Vyberte nastavení aktivního spuštění pro zátěžový test](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Upravit vlastnosti nastavení spuštění:** Můžete upravit vlastnosti nastavení spuštění pro takové věci, jako jsou možnosti protokolování (viz více níže), určení délky testu, doba zahřívání, maximální počet hlášených podrobností o chybě, vzorkovací frekvence, model připojení (pouze testy výkonu webu), typ úložiště výsledků, úroveň ověření a trasování SQL. Parametry spuštění by měly odrážet cíle zátěžového testu.|-   [Vlastnosti nastavení spuštění zátěžového testu](../test/load-test-run-settings-properties.md)<br />-   [Změna vlastností nastavení spuštění](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Zadejte počet iterací testu v nastavení spuštění zátěžového testu:** Můžete určit počet spuštění všech webových testů výkonu a částí ve všech scénářích zátěžových testů konfigurací **vlastnosti Test Iterations.**|-   [Postup: Určení počtu iterací testu v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Určete vzorkovací frekvenci pro nastavení spuštění zátěžového testu:** Můžete určit, jak často má zátěžový test shromažďovat data čítače výkonu konfigurací **vlastnosti Vzorkovací frekvence.**|-   [Postup: Určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Zadejte možnost úložiště podrobností časování:** Můžete určit, jak chcete podrobnosti zátěžového testu uložit konfigurací **vlastnosti úložiště podrobnosti časování.**|-   [Postup: Určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Zadejte dobu uchovávání testovacích prostředků:** Urychlete testovací > opravit > cyklu s opakováním testu tím, že zachováte testovací prostředky po zadanou dobu nastavením **vlastnosti Doba uchovávání prostředků.**|-   [Zachovat prostředky pro urychlení zátěžového testování](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Použít parametry kontextu:** Parametry kontextu můžete použít k parametrizaci řetězce. Pokud například zátěžový test obsahuje test výkonu webu, který používá parametrizovaný webový server, můžete přidat parametr kontextu do nastavení spuštění, které se mapuje na jiný server.|-   [Postup: Přidání parametrů kontextu do nastavení spuštění](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurace vlastností protokolování testů:** Můžete nakonfigurovat, jak často jsou data zapsána do protokolu, který je přidružen k nastavení spuštění zátěžového testu. To může být důležité při spouštění rozsáhlých nebo složitých zátěžových testů, protože protokol by mohl mít velikost několik gigabajtů.<br /><br /> Lze také nakonfigurovat, aby se soubor protokolu automaticky uložil při selhání zátěžového testu, což pomůže při ladění a analýze aplikace.|-   [Změna nastavení protokolování zátěžového testu](../test/modify-load-test-logging-settings.md)|
