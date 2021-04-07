---
title: Migrace testsettings na runsettings
description: Naučte se migrovat testsettings na runsettings.
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1cfe921777fa75d4f69251668934e8d78d9bec
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/31/2021
ms.locfileid: "106087182"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>Upgradovat z  *. testsettings* na *. runsettings*

Konfigurační soubor testu můžete upgradovat z *. testsettings* na *. runsettings* pomocí nástroje SettingsMigrator, který se nainstaluje společně se sadou Visual Studio. V závislosti na umístění instalace sady Visual Studio můžete najít nástroj Migrace nastavení v následující cestě: `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`

Ve správném umístění adresáře můžete spustit nástroj ve formátu níže:

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>Příklady
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

Pokud se chcete dozvědět víc o tom, jak se možnosti *. testsettings* převádějí na *. runsettings* , najdete další podrobnosti o implementaci v [úložišti Open Source test Platform](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration) na GitHubu.

## <a name="see-also"></a>Viz také

- [Konfigurace testovacích běhů s `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Upgrade z MSTestv1 na MSTestv2](../test/mstest-update-to-mstestv2.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Ladění testů částí pomocí Průzkumníka testů](../test/debug-unit-tests-with-test-explorer.md)
