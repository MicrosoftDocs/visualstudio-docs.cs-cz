---
title: Konfigurace parametrů běhu zátěžových testů
description: Přečtěte si o nastaveních spuštění, které jsou vlastnosti ovlivňující způsob, jakým běží zátěžový test. Nastavení spuštění jsou uspořádána podle kategorií v okno Vlastnosti.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24f267e32468958171266f0e8aaf45c69b2c373a
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441617"
---
# <a name="configure-load-test-run-settings"></a>Konfigurovat nastavení běhu zátěžového testu

*Parametry spuštění* jsou sada vlastností, které ovlivňují způsob spuštění zátěžového testu. Nastavení spuštění jsou uspořádána podle kategorií v okně **vlastnosti** .

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

V rámci zátěžového testu můžete mít více než jedno nastavení spuštění, ale pro každé spuštění může být aktivní pouze jedno z parametrů spuštění. Další parametry spuštění poskytují rychlý způsob výběru alternativního nastavení pro následné běhy testu.

Počáteční nastavení spuštění se vytvoří při vytvoření zátěžového testu pomocí **nového Průvodce zátěžovým testem**.

![Parametry spuštění zátěžového testu](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-|
|**Přidání dalších parametrů spuštění do zátěžového testu:** Kromě nastavení spuštění, které je vytvořeno při spuštění **nové Průvodce zátěžovým testem**, můžete do zátěžového testu přidat další parametry spuštění, abyste mohli spustit test za různých podmínek.|-   [Postupy: Přidání dalších parametrů spuštění do zátěžového testu](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Zadejte nastavení aktivního běhu pro použití s zátěžovým testem:** Můžete vybrat parametr spuštění, který chcete použít se zátěžovým testem, a to pomocí Editor zátěžového testu. Aktivní parametr spuštění lze rozpoznat pomocí přípony „[Active]“.|-   [Postupy: výběr aktivního nastavení spuštění pro zátěžový test](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Upravit vlastnosti nastavení spuštění:** Můžete upravit vlastnosti parametrů spuštění jako možnosti protokolování (viz více níže), určit délku testu, dobu zahřívání, maximální počet hlášených podrobností o chybách, vzorkovací frekvenci, model připojení (pouze testy výkonnosti webu), typ úložiště výsledků, úroveň ověřování a trasování SQL. Parametry spuštění by měly odrážet cíle zátěžového testu.|-   [Vlastnosti nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md)<br />-   [Změna vlastností nastavení spuštění](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Zadejte počet iterací testu v nastavení běhu zátěžového testu:** Můžete určit počet spuštění všech testů webového výkonu a jednotek ve všech scénářích zátěžových testů konfigurací vlastnosti **iterace testu** .|-   [Postupy: určení počtu testovacích iterací v nastavení spuštění](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Zadejte vzorkovací frekvenci pro nastavení běhu zátěžového testu:** Můžete určit, jak často má zátěžový test shromažďovat data čítače výkonu konfigurací vlastnosti **vzorkovací frekvence** .|-   [Postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Zadejte možnost úložiště podrobností časování:** Můžete určit, jak se mají podrobnosti zátěžového testu ukládat, konfigurací vlastnosti **úložiště podrobností časování** .|-   [Postupy: určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Zadejte dobu uchování prostředku testu:** Urychlete test > opravte > cyklus testování tím, že zachováte testovací prostředky po určenou dobu nastavením vlastnosti **Doba uchování prostředků** .|-   [Zachování prostředků pro urychlení zátěžového testování](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts&preserve-view=true)|
|**Použít kontextové parametry:** Můžete použít kontextové parametry k použití parametrizovat řetězec. Například pokud váš zátěžový test obsahuje test výkonnosti webu, který používá parametrizovaný webový server, můžete přidat kontextový parametr do parametrů běhu, které jsou mapovány na jiný server.|-   [Postupy: Přidání kontextových parametrů do nastavení běhu](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurace vlastností protokolování testu:** Můžete nakonfigurovat, jak často se data zapisují do protokolu, který je spojen s nastavením běhu zátěžového testu. To může být důležité při spouštění rozsáhlých nebo složitých zátěžových testů, protože protokol by mohl mít velikost několik gigabajtů.<br /><br /> Lze také nakonfigurovat, aby se soubor protokolu automaticky uložil při selhání zátěžového testu, což pomůže při ladění a analýze aplikace.|-   [Mění se nastavení protokolování zátěžového testu.](../test/modify-load-test-logging-settings.md)|