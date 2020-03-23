---
title: Úpravy zátěžových testů
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c61c13f6a9eca416a52221ba9da37be820dd4b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593223"
---
# <a name="edit-load-tests"></a>Upravit zátěžové testy

Zátěžové testy spustit testy výkonu webu nebo testování částí simulovat mnoho uživatelů přístup k serveru ve stejnou dobu. Zátěžový test umožňuje přístup k datům zátěže a výkonu aplikace. Zátěžový test lze nakonfigurovat pro emulaci rozličných podmínek zátěže, jako je uživatelská zátěž nebo typ sítě.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Zátěžový test je definován *scénáři*, *sadami čítačů*a *nastaveními spuštění*. Následující obrázek vysvětluje rozdíly mezi [scénáři](../test/edit-load-test-scenarios.md), [sadami čítačů](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)a [nastaveními spuštění](../test/load-test-run-settings-properties.md):

![Architektura zátěžového testu](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>Požadavky na software

Projekty webového výkonu a zátěžového testu jsou k dispozici pouze v edici Enterprise sady Visual Studio.

## <a name="edit-load-test-scenario-settings"></a>Upravit nastavení scénáře zátěžového testu

Scénář se používá k modelování, jak skupina uživatelů spolupracuje se serverovou aplikací. Scénáře se skládají ze vzoru zatížení, modelu kombinace testů, kombinace testů, kombinace prohlížečů a kombinace sítí. Zátěžový test může mít více než jeden scénář a jeden scénář může obsahovat testy výkonu webu a testy částí. Seskupením podobných nastavení umožňuje scénář seskupit podobné testy a spustit je současně.

Další informace naleznete v [tématu Úprava scénářů zátěžového testu](../test/edit-load-test-scenarios.md) a [vlastnosti scénáře zatížení .](../test/load-test-scenario-properties.md)

## <a name="configure-and-manage-performance-counter-sets"></a>Konfigurace a správa sad čítačů výkonu

Zátěžové testy poskytují pojmenované sady čítačů uspořádané podle technologie, které jsou užitečné při analýze dat čítače výkonu. Sady čítačů zahrnují zátěžový test, iis, ASP.NET a SQL. Při vytváření zátěžového testu pomocí **Průvodce novým zátěžovým testem**je pro počítače, které zadáte zahrnout do zátěžového testu, nakonfigurována počáteční sada předdefinovaných a důležitých čítačů. Čítače spravujete v **Editoru zátěžových testů**.

Další informace naleznete [v tématu Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Konfigurace a správa nastavení spuštění zátěžového testu

Nastavení spuštění jsou vlastnosti, které ovlivňují způsob spuštění zátěžového testu. Nastavení spuštění jsou uspořádána podle kategorií v okně **Vlastnosti.**

Další informace naleznete [v tématech Konfigurace nastavení spuštění zátěžového testu](../test/configure-load-test-run-settings.md) a [Vlastnosti nastavení spuštění testu zatížení](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analýza porušení pravidel prahové hodnoty](../test/analyze-threshold-rule-violations-in-load-tests.md)
