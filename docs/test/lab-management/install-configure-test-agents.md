---
title: Instalace testovacích agentů a kontrolerů testů
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 271e9253daf4ab23a5fb06a189ac3042bc925b2a
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880270"
---
# <a name="install-test-agents-and-test-controllers"></a>Instalace testovacích agentů a kontrolerů testů

Pro testovací scénáře, které používají Visual Studio a Azure Test Plans nebo Team Foundation Server (TFS), nepotřebujete testovací řadič. Agenti pro Visual Studio popisovat orchestraci komunikací s plány testování Azure nebo TFS. Scénář může být, že spustíte průběžné testy pro sestavení a uvolnění pracovních postupů v plánech testování Azure nebo TFS.

Můžete také zvážit, pokud je lepší použít [správu sestavení nebo vydání](use-build-or-rm-instead-of-lab-management.md) namísto správy testovacího prostředí.

## <a name="system-requirements"></a>Systémové požadavky

V následující tabulce jsou uvedeny systémové požadavky na instalaci testovacího agenta nebo testovacího řadiče pro sady Visual Studio:

| Položka | Požadavky |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard a datové centrum<br />Windows Server 2012 R2 |
| **Řadič** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard a datové centrum<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Instalace testovacího řadiče a testovacích agentů

Agenty sady Visual Studio můžete stáhnout z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Vyhledejte *agenty pro Visual Studio 2019*, vyberte *agenta* nebo *ovladač*a pak zvolte *Stáhnout*. Spusťte stažený spustitelný soubor a nainstalujte testovacího agenta nebo řadiče.

Agenti pro Visual Studio 2017, Visual Studio 2015 a Visual Studio 2013 si můžete stáhnout ze starší stránky [ke stažení.](https://visualstudio.microsoft.com/vs/older-downloads/)

Tyto instalační programy jsou k dispozici jako ISO soubory pro snadnou instalaci na virtuálních počítačích.

::: moniker range="vs-2017"
## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Kompatibilní verze TFS, Microsoft Test Manager, testovací řadič a testovací agent

Můžete kombinovat různé verze TFS, Microsoft Test Manager, testovací řadič a testovací agent, podle následující tabulky:

| TFS | Správce testů microsoftu s Lab Center | Řadič | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: upgrade z roku 2015 nebo nová instalace | 2017 | 2017 | 2017 |
| 2017: upgrade z roku 2015 nebo nová instalace | 2017 | Aktualizace 5 z roku 2013 | Aktualizace 5 z roku 2013 |
| 2017: upgrade z roku 2015 nebo nová instalace | 2015 | Aktualizace 5 z roku 2013 | Aktualizace 5 z roku 2013 |
| 2015: upgrade z roku 2013 | 2013 | 2013 |2013 |
| 2015: nová instalace | 2013 | 2013 | 2013 |
| 2015: upgrade z roku 2013 nebo nová instalace | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="compatible-versions-of-tfs-the-test-controller-and-test-agent"></a>Kompatibilní verze TFS, testovacího řadiče a testovacího agenta

Můžete kombinovat různé verze TFS, testovací řadič a testovací agent podle následující tabulky:

| TFS | Řadič | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: upgrade z roku 2015 nebo nová instalace | 2017 | 2017 |
| 2017: upgrade z roku 2015 nebo nová instalace | Aktualizace 5 z roku 2013 | Aktualizace 5 z roku 2013 |
| 2017: upgrade z roku 2015 nebo nová instalace | Aktualizace 5 z roku 2013 | Aktualizace 5 z roku 2013 |
| 2015: upgrade z roku 2013 | 2013 |2013 |
| 2015: nová instalace | 2013 | 2013 |
| 2015: upgrade z roku 2013 nebo nová instalace | 2013 | 2013 |
| 2013 | 2013 | 2013 |
::: moniker-end

> [!NOTE]
> Scénáře správy testovacího prostředí v TFS 2018 a Azure DevOps Services jsou zastaralé. Další informace naleznete v [tématu TFS 2018 Release Notes](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Upgrade z testovacích agentů sady Visual Studio 2013

Doporučujeme používat agenty pro Visual Studio ve všech nových scénářích automatizovaného testování. Úlohu *Nasadit testovací agenty* v kanálu sestavení můžete použít ke stažení a instalaci testovacích agentů do počítače.

Následující tabulka ukazuje scénáře podporované agenty pro Visual Studio 2013 a alternativy pro Team Foundation Server (TFS) 2015 a Plány testů Azure:

| Scénáře podporované agenty pro Visual Studio 2013 | Alternativa v TFS a testovacích plánech Azure |
| - | - |
| Pracovní postup Build-Deploy-Test ve Visual Studiu | Uživatelé mohou použít [kanál sestavení](/azure/devops/pipelines/index?view=vsts) (nikoli sestavení XAML) pro scénáře sestavení, nasazení a testování v TFS. |
| Testování zatížení (testování výkonu) pomocí místních vzdálených počítačů | Použití testovacího řadiče a testovacích agentů 2013 Aktualizace 5 pro spuštění zátěžových testů v místním prostředí. |
| Vzdálené spuštění automatizovaných testů ze Správce testů Microsoftu (zastaralé v sadě Visual Studio 2017) pomocí testovacího prostředí | V současné době neexistuje žádná alternativa pro tento scénář. Doporučujeme použít spustit funkční testy úlohy v sestavení a vydání definice (není v sestavení XAML) ke vzdálenému spuštění testů. |
| Vývojáři provádějící vzdálené testy v sadě Visual Studio | Již není podporováno. |
