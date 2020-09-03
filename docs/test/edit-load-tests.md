---
title: Úpravy zátěžových testů
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b95689871a987c018720c529743b8447f39b2bf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288699"
---
# <a name="edit-load-tests"></a>Upravit zátěžové testy

Zátěžové testy spouštějí testy webového výkonu nebo testy jednotek pro simulaci velkého počtu uživatelů, kteří přistupují k serveru současně. Zátěžový test umožňuje přístup k datům zátěže a výkonu aplikace. Zátěžový test lze nakonfigurovat pro emulaci rozličných podmínek zátěže, jako je uživatelská zátěž nebo typ sítě.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Zátěžový test je definován *scénáři*, *sadami čítačů*a *parametry spuštění*. Následující ilustrace vysvětluje rozdíly mezi [scénáři](../test/edit-load-test-scenarios.md), [sadami čítačů](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)a [parametry spuštění](../test/load-test-run-settings-properties.md):

![Architektura zátěžového testu](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>Požadavky na software

Projekty webového výkonu a zátěžového testu jsou k dispozici pouze v edici Enterprise sady Visual Studio.

## <a name="edit-load-test-scenario-settings"></a>Upravit nastavení scénáře zátěžového testu

Scénář slouží k modelování způsobu, jakým skupina uživatelů komunikuje se serverovou aplikací. Scénáře se skládají ze vzoru zatížení, modelu kombinace testů, kombinace testů, kombinace prohlížečů a kombinace sítí. Zátěžový test může mít více než jeden scénář a jeden scénář může obsahovat testy výkonnosti webu a testy jednotek. Seskupením podobných nastavení umožňuje scénář seskupit podobné testy a spustit je současně.

Další informace najdete v tématu [Úpravy scénářů zátěžových testů](../test/edit-load-test-scenarios.md) a [vlastností scénáře zátěžového testu](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurace a Správa sad čítačů výkonu

Zátěžové testy poskytují pojmenované sady čítačů organizované podle technologie, které jsou užitečné při analýze dat čítače výkonu. Sady čítačů zahrnují zátěžový test, službu IIS, ASP.NET a SQL. Když vytvoříte zátěžový test s **novým Průvodce zátěžovým testem**, je pro počítače, které zadáte k zahrnutí do zátěžového testu, konfigurována počáteční sada předdefinovaných a důležitých čítačů. Čítače můžete spravovat v **Editor zátěžového testu**.

Další informace naleznete v tématu [Určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Konfigurace a Správa nastavení běhu zátěžového testu

Parametry spuštění jsou vlastnosti, které ovlivňují způsob spuštění zátěžového testu. Nastavení spuštění jsou uspořádána podle kategorií v okně **vlastnosti** .

Další informace najdete v tématu [Konfigurace nastavení běhu zátěžového testu](../test/configure-load-test-run-settings.md) a [vlastností nastavení běhu zátěžového testu](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Viz také

- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analýza porušení pravidel mezních hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
