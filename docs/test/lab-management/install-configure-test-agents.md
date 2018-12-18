---
title: Instalace testovacích agentů a kontrolerů testů
ms.date: 10/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8055e1c11f38ab83ae9c3a0570064ca49158b886
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219026"
---
# <a name="install-test-agents-and-test-controllers"></a>Instalace testovacích agentů a kontrolerů testů

Pro testovací scénáře, které používají Visual Studio a Azure testovací plány nebo Team Foundation Server (TFS) nemusíte testovacího kontroléru. Agents pro Visual Studio zpracování Orchestrace tím, že komunikuje s Azure testovací plány nebo sady TFS. Scénář může být spuštění průběžné testů pro sestavení a vydání pracovních postupů v Azure testovací plány nebo sady TFS.

Můžete taky zvážit, pokud je vhodnější použít [sestavení nebo Správa vydaných verzí](use-build-or-rm-instead-of-lab-management.md) namísto správy testovacího prostředí.

## <a name="system-requirements"></a>Požadavky na systém

V následující tabulce jsou uvedeny požadavky na systém pro instalaci testovací agent nebo testovací kontrolér pro Visual Studio 2017:

| Položka | Požadavky |
| ---- | ------------ |
| **Agent** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard a Datacenter<br />Windows Server 2012 R2 |
| **Kontroler** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard a Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Nainstalujte testovací kontrolér a testovací agenty

Můžete si stáhnout agenty pro Visual Studio 2017 z [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents). Vyhledejte *Agents for Visual Studio 2017*, vyberte buď *agenta* nebo *řadič*a klikněte na tlačítko *Stáhnout*. Spouštění staženého spustitelného souboru k instalaci testovacího agenta nebo kontroler.

Agenty si můžete stáhnout pro Visual Studio 2015 a Visual Studio 2013 z [starší soubory ke stažení](https://visualstudio.microsoft.com/vs/older-downloads/) stránky.

Tyto instalační programy jsou dostupné jako soubory ISO pro snadnou instalaci na virtuálních počítačích.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Kompatibilní verze serveru TFS, Microsoft Test Manager, testovacího kontroléru a testovacího agenta

Podle následující tabulky můžete kombinovat různé verze TFS, Microsoft Test Manager, testovacího kontroléru a testovacího agenta:

| TFS | Nástroje Microsoft Test Manager pomocí centra testovacích prostředí | Kontroler | Agent |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: upgrade z 2015 nebo s novou instalací | 2017 | 2017 | 2017 |
| 2017: upgrade z 2015 nebo s novou instalací | 2017 | 2013 update 5 | 2013 update 5 |
| 2017: upgrade z 2015 nebo s novou instalací | 2015 | 2013 update 5 | 2013 update 5 |
| 2015: upgrade z 2013 | 2013 | 2013 |2013 |
| 2015: nové instalace | 2013 | 2013 | 2013 |
| 2015: upgrade z 2013 nebo s novou instalací | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

> [!NOTE]
> Scénáře správy testovacího prostředí v TFS 2018 a DevOps služby Azure jsou zastaralé. Další informace najdete v části [poznámky k verzi TFS 2018](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Upgrade z Visual Studio 2013 testovacích agentů

Doporučujeme použít produkt agents for Visual Studio ve všech nových scénářích automatizované testování. Můžete použít *nasadit testovací agenti* úlohy v kanálu ke stažení a instalaci testovacích agentů v počítači sestavení.

Následující tabulka uvádí scénáře podporované agenty pro Visual Studio 2013 a alternativ pro Team Foundation Server (TFS) 2015 a Azure testovacích plánů:

| Agents for Visual Studio 2013 podporuje scénáře | Alternativní v TFS a plány testování v Azure |
| - | - |
| Pracovní postup sestavení-nasazení-testování v sadě Visual Studio | Uživatelé můžou použít [kanálu pro sestavování](/azure/devops/pipelines/index?view=vsts) (ne sestavení XAML) pro sestavení, nasazení a testování scénářů v sadě TFS. |
| Zátěžové testování (testování výkonu) pomocí místní vzdálené počítače | Použít testovací Kontrolér a testovací agenty 2013 Update 5 spustit zátěžové testy místně. |
| Vzdálené spuštění automatizovaných testů z nástroje Microsoft Test Manager pomocí testovacího prostředí | Aktuálně neexistuje žádná alternativa pro tento scénář. Doporučujeme, abyste pomocí úlohy pro spuštění funkčních testů v buildu a definice verzí (ne v sestavení XAML) Chcete-li vzdáleně spustit testy. |
| Vývojáři provádění vzdáleného testů v sadě Visual Studio | Již nejsou podporovány. |
