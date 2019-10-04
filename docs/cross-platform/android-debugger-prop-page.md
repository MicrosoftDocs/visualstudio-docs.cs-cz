---
title: Vlastnosti ladicího programuC++pro Android () | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 0a052223fe7acac87acf15c5c5091c774451e4e4
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950622"
---
# <a name="android-debugger-properties"></a>Vlastnosti ladicího programu pro Android

Vlastnost | Popis | Vlastnit
--- | ---| ---
Typ ladicího programu | Určuje, který typ kódu se má ladit. | **Pouze nativní**<br>**Pouze Java**<br>
Cíl ladění | Určuje emulátor nebo zařízení, které se má použít pro ladění. Pokud nejsou spuštěné žádné emulátory, spusťte prosím zařízení pomocí příkazu ' Android Virtual Device (AVD) Manager '.
Balíček, který se má spustit | Určuje umístění *. apk* , které se bude ladit. Tuto možnost vyberte, pokud chcete určit, že se má při ladění aplikace spustit konkrétní balíček (APK).
Spouštěcí aktivita | Aktivita Androidu, která se má použít pro spuštění aplikace, musí odpovídat hodnotě používané v manifestu. Stisknutím tlačítka použít načtete seznam ze *souboru souboru AndroidManifest. XML* a dynamicky jej nasadíte.
Další cesty pro hledání symbolů | Další cesta hledání pro symboly ladění
Další cesty pro vyhledávání zdrojového kódu Java | Další vyhledávací cesty pro zdrojové soubory Java (Platí pouze v případě, že typ ladicího programu je pouze Java.)
