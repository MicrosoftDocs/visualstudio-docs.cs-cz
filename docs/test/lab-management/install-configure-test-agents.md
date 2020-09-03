---
title: Instalace testovacích agentů a kontrolerů testů
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c374951b4d4875e4e754035ac52afb7f8fc5a2e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286892"
---
# <a name="install-test-agents-and-test-controllers"></a>Instalace testovacích agentů a kontrolerů testů

Pro testovací scénáře, které používají sadu Visual Studio a Azure Test Plans nebo Team Foundation Server (TFS), nepotřebujete kontroler testů. Agenti pro orchestraci obslužných rutin sady Visual Studio komunikují s Azure Test Plans nebo TFS. Scénář může být spuštěn průběžné testy pro pracovní postupy sestavení a vydání v Azure Test Plans nebo TFS.

Můžete také zvážit, jestli je vhodnější místo správy testovacího prostředí používat [správu sestavení nebo vydání](use-build-or-rm-instead-of-lab-management.md) .

## <a name="system-requirements"></a>Požadavky na systém

V následující tabulce jsou uvedeny požadavky na systém pro instalaci testovacího agenta nebo kontroleru testů pro Visual Studio:

| Položka | Požadavky |
| ---- | ------------ |
| **Agenta** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard a Datacenter<br />Windows Server 2012 R2 |
| **Kontrolér** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard a Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Instalace testovacího kontroléru a testovacích agentů

Agenty pro Visual Studio si můžete stáhnout z [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Vyhledejte *agenty sady Visual Studio 2019*, vyberte buď možnost *Agent* , nebo *kontrolér*a pak zvolte možnost *Stáhnout*. Spusťte stažený spustitelný soubor pro instalaci testovacího agenta nebo kontroleru.

Agenty pro Visual Studio 2017, Visual Studio 2015 a Visual Studio 2013 můžete stáhnout ze stránky [starší verze ke stažení](https://visualstudio.microsoft.com/vs/older-downloads/) .

Tyto instalační programy jsou k dispozici jako soubory ISO pro jednoduchou instalaci na virtuálních počítačích.

::: moniker range="vs-2017"
## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Kompatibilní verze serveru TFS, Microsoft Test Manager, testovací kontrolér a testovací agent

Můžete kombinovat různé verze serveru TFS, Microsoft Test Manager, testovací kontrolér a testovacího agenta, a to v závislosti na následující tabulce:

| TFS | Microsoft Test Manager s centrem testovacího prostředí | Kontrolér | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: Upgradujte z 2015 nebo nové instalace | 2017 | 2017 | 2017 |
| 2017: Upgradujte z 2015 nebo nové instalace | 2017 | 2013 aktualizace 5 | 2013 aktualizace 5 |
| 2017: Upgradujte z 2015 nebo nové instalace | 2015 | 2013 aktualizace 5 | 2013 aktualizace 5 |
| 2015: upgrade z 2013 | 2013 | 2013 |2013 |
| 2015: nová instalace | 2013 | 2013 | 2013 |
| 2015: Upgradujte z 2013 nebo nové instalace | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="compatible-versions-of-tfs-the-test-controller-and-test-agent"></a>Kompatibilní verze serveru TFS, testovací kontrolér a testovací agent

Můžete kombinovat různé verze TFS, kontroler testů a testovacího agenta, a to v závislosti na následující tabulce:

| TFS | Kontrolér | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: Upgradujte z 2015 nebo nové instalace | 2017 | 2017 |
| 2017: Upgradujte z 2015 nebo nové instalace | 2013 aktualizace 5 | 2013 aktualizace 5 |
| 2017: Upgradujte z 2015 nebo nové instalace | 2013 aktualizace 5 | 2013 aktualizace 5 |
| 2015: upgrade z 2013 | 2013 |2013 |
| 2015: nová instalace | 2013 | 2013 |
| 2015: Upgradujte z 2013 nebo nové instalace | 2013 | 2013 |
| 2013 | 2013 | 2013 |
::: moniker-end

> [!NOTE]
> Scénáře správy testovacího prostředí v TFS 2018 a Azure DevOps Services jsou zastaralé. Další informace najdete v [poznámkách k verzi TFS 2018](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Upgrade z Visual Studio 2013 testovacích agentů

Doporučujeme použít agenty pro Visual Studio ve všech nových scénářích automatizovaného testování. Můžete použít úlohu *nasadit testovací agenty* v kanálu sestavení ke stažení a instalaci testovacích agentů na vašem počítači.

V následující tabulce jsou uvedeny scénáře podporované agenty pro Visual Studio 2013 a alternativy pro Team Foundation Server (TFS) 2015 a Azure Test Plans:

| Scénáře podporované agenty pro Visual Studio 2013 | Alternativa v TFS a Azure Test Plans |
| - | - |
| Pracovní postup sestavení-nasazení-testování v aplikaci Visual Studio | Uživatelé můžou použít [kanál sestavení](/azure/devops/pipelines/index?view=vsts) (ne sestavení XAML) pro scénáře sestavení, nasazení a testování v TFS. |
| Zátěžové testování (testování výkonu) pomocí místních vzdálených počítačů | Pomocí Test Controller a test Agents 2013 Update 5 spusťte testy zatížení místně. |
| Vzdálené spuštění automatizovaných testů z Microsoft Test Manager (nepoužívané v rámci sady Visual Studio 2017) pomocí testovacího prostředí | V současné době není k dispozici žádná alternativa pro tento scénář. K provedení testů vzdáleně doporučujeme použít úlohu spustit funkční testy v definicích sestavení a vydání (nikoli v sestavení XAML). |
| Vývojáři spouštějící vzdálené testy v aplikaci Visual Studio | Již není podporováno. |
