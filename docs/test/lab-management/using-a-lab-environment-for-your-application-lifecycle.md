---
title: Použití testovacího prostředí pro vývoj a provoz
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b02f8bf9542b5de4737d173835c011f59c3fdc86
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847293"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Použít prostředí laboratoře pro váš vývoj a provoz

Testovací prostředí je kolekce virtuálních a fyzických počítačů, které slouží k vývoji a testování aplikací. Testovací prostředí může obsahovat více rolí potřebných k testování vícevrstevných aplikací, například pracovní stanice, webové servery a databázové servery. Kromě toho můžete pracovního postupu sestavení nasazení testování s testovacím prostředím pro automatizaci vytváření, nasazování a spouštění automatizovaných testů ve své aplikaci.

* **Spuštění automatizovaných testů pomocí testovacího plánu** – můžete spustit kolekci automatických testů, volá se *testovacího plánu*a sledovat průběh.

* **Použití pracovního postupu sestavení nasazení testování** – pracovní postup sestavení nasazení testování můžete použít k testování vícevrstevných aplikací automaticky. Typickým příkladem je pracovní postup, který spustí sestavení, nasadí soubory sestavení do příslušné počítačů v testovacím prostředí a potom provede automatizované testy. Kromě toho můžete naplánovat pracovní postup spouštět v určitých intervalech.

* **Shromažďovat diagnostická data ze všech počítačů, i během ručního testování** – diagnostická data můžete shromažďovat z více počítačů současně. Například během jednoho testovacího běhu, můžete shromažďovat IntelliTrace, test, dopad a další formy data z webový server, databázový server a klienta.

Tady jsou příklady běžných topologie prostředí laboratoře:

| Topologie | Popis |
|---|---|
|![Pouze topologie serveru](../media/topology_backend.png)| Má tohoto testovacího prostředí *topologie serveru*, což se často používá ke spuštění ručních testů na serverové aplikace a který umožňuje testerům sloužící k ověření chyby v prostředí svoje vlastní klientské počítače. Testovací prostředí v topologii back-endu, obsahuje jenom servery. Při použití tohoto typu topologie, obvykle připojení k serverům v testovacím prostředí pomocí klientského počítače, který je součástí prostředí.|
|![Testovací prostředí cloud](../media/topology_cloud.png)| Tohoto testovacího prostředí poskytuje podobné funkce a funkce jako _topologie serveru_, ale eliminuje požadavek pro fyzický nebo virtuální počítače spuštěné v místním prostředí, která mohou zkrátit čas, instalační program, zjednodušit Údržba a minimalizaci nákladů. Nastavení více webů a virtuálních počítačů spolu s vlastní sítě, je rychlý a snadný v cloudovém prostředí, jako je například Microsoft Azure.|
|![Klient server testovacího prostředí](../media/topology_clientserver.png)| Má tohoto testovacího prostředí *klient server topologie*, což se často používá k testování aplikace, která obsahuje součásti serveru a klienta. V topologii klient/server všechny klientské a serverové počítače použít k testování vaší aplikace se ve vašem testovacím prostředí. Když tuto topologii použijte, může shromažďovat testovací data z každý počítač, který má vliv na vaše testy.|

| | |
|---|---|
| ![Ikona fotoaparátu videa pro videa](../../install/media/video-icon.png) | [Podívejte se na video](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) týkající se správy testovacích prostředí pro testování. |

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Použití cloudu s Azure kanály nebo Team Foundation Server sestavení a vydání

Můžete provádět automatizované testování a pomocí automatizace sestavení nasazení testování [sestavení a vydání](/azure/devops/pipelines/index?view=vsts) funkce v produktech Team Foundation Server (TFS) a testovací plány Azure. Mezi výhody patří:

* Nepotřebujete řadič sestavení nebo testovacího kontroléru.
* Testovací agent se instaluje prostřednictvím úkolu jako součást sestavení nebo vydané verzi.
* Je snadné k přizpůsobení kroků nasazení. Už nejsou omezené na pomocí jednoho skriptu. Můžete taky využít výhod celé řadě úloh, které jsou dostupné v produktu stejně jako v aplikaci Visual Studio Marketplace.
* Není nutné udržovat testovací sady. Testy můžete spustit přímo z binárních souborů.
* Můžete získat bohatší vložených sestav prostředí pro testy, které běží v rámci každého sestavení nebo vydané verzi.
* Můžete sledovat, které prostředky (verze, sestavení, pracovních položek, potvrzení) jsou aktuálně nasadila a otestovala v každém prostředí.
* Můžete přizpůsobit a rozšířit automatizace snadno nasazovat do více testovacích prostředích a dokonce i do produkčního prostředí.
* Můžete naplánovat, automatizace, která se provede při každém vrácení se změnami nebo potvrzení změn, nebo v určitý čas každý den.

Další informace najdete v tématu [použít sestavení nebo Release management](use-build-or-rm-instead-of-lab-management.md).

## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Pomocí funkcí Visual Studio Lab Management nástroje Microsoft Test Manager

Při použití Visual Studio Enterprise Edition můžete vytvářet a spravovat testovací prostředí s funkcemi Visual Studio Lab Management Microsoft Test Manager.

Testovací agenti Lab Management automaticky nainstaluje na každém počítači, ve vašem prostředí.

Pokud používáte správu testovacího prostředí ve spojení s System Center Virtual Machine Manager (SCVMM), získáte také tyto výhody při použití testovacích prostředí:

* **Rychle reprodukovat konfigurace počítačů** – můžete uložit kolekce virtuálních počítačů, které jsou nakonfigurované pro opětovné vytvoření typickém produkčním prostředí. Pak můžete provádět každého testovacího běhu na novou kopii uložené prostředí.

* **Reprodukovat přesné podmínky chyby** – když se testovací běh se nezdaří, můžete uložit kopii stavu testovacího prostředí a k němu přístup z výsledků sestavení nebo pracovní položky.

* **Spuštění více kopií testovacího prostředí ve stejnou dobu** – můžete spustit několik kopií testovacího prostředí ve stejnou dobu bez konfliktům pojmenování.

### <a name="standard-environments-and-scvmm-environments"></a>Standardní prostředí a prostředí SCVMM

Existují dva typy testovacích prostředí, které můžete vytvořit pomocí Visual Studio Lab Management: **standardní prostředí** a **prostředí SCVMM**. Možnosti každého typu prostředí se však liší.

**Standardní prostředí:** může obsahovat kombinaci virtuálních a fyzických počítačů. Virtuální počítače můžete také přidat do standardního prostředí, která se spravují přes rozhraní virtualizace třetích stran. Standardní prostředí nevyžadují dalšího serveru pro prostředky, například SCVMM server.

**Prostředí SCVMM:** může obsahovat jenom virtuální počítače, které jsou spravovány serverem SCVMM (System Center Virtual Machine Manager), takže virtuální počítače v prostředí SCVMM spustit pouze v rámci virtualizace Hyper-V. Prostředí SCVMM ale poskytuje následující funkce automatizace a správy, které nejsou k dispozici ve standardní prostředí:

- **Snímky prostředí:** snímky prostředí obsahují stavu testovacího prostředí, takže můžete rychle obnovit čisté prostředí, nebo uložit stav prostředí, ve kterém byl změněn. Pracovní postup sestavení nasazení testování můžete použít také k automatizaci procesu ukládání a obnovení snímků prostředí.

- **Uložené prostředí:** můžete uložit kopii prostředí SCVMM a pak nasadit více kopií daného prostředí.

- **Izolace sítě:** izolace sítě vám umožní současně spustit více kopií stejné prostředí SCVMM bez konflikty názvů počítačů.

- **Šablony virtuálních počítačů:** šablonu virtuálního počítače je virtuální počítač, pro který byla její název a odebrat další identifikátory. Při nasazení šablony virtuálního počítače v prostředí SCVMM, nástroje Microsoft Test Manager vytvoří nové identifikátory. To umožňuje nasazovat více kopií virtuálního počítače ve stejném prostředí, nebo více prostředí a současně spuštění virtuálních počítačů.

- **Uložené virtuální počítače:** virtuálního počítače, která je uložen v knihovně projektu a také jedinečné identifikátory.

> [!NOTE]
> Správa testovacího prostředí SCVMM 2016 nepodporuje.

Informace o SCVMM, naleznete v tématu [Virtual Machine Manager](/azure/devops/pipelines/?view=vsts).

Standardní prostředí a prostředí SCVMM podporují řadu stejných funkcí. Existují však několik důležitých rozdílů, které byste měli zvážit. Následující tabulka porovnává funkce, které jsou k dispozici pro standardní prostředí a prostředí SCVMM.

|Funkce|Prostředí SCVMM|Standardní prostředí|
|-|------------------------|-|
|**Testování**|||
|Spouštění manuálních testů|Podporované|Podporované|
|Spustit kódované UI a Další automatizované testy|Podporované|Podporované|
|Podrobné zaznamenávání chyb pomocí adaptérů diagnostiky|Podporované|Podporované|
|**Nasazení sestavení**|||
|Automatické pracovní postupy sestavení nasazení testování|Podporované|Podporované|
|**Vytváření prostředí a Správa**|||
|Použijte fyzické počítače kromě virtuálních počítačů|Není podporováno|Podporované|
|Použijte virtuální počítače třetích stran|Není podporováno|Podporované|
|Automaticky nainstalujte testovací agenty do počítačů v testovacím prostředí|Podporované|Podporované|
|Uložte a nasaďte stav prostředí laboratoře použití snímků prostředí|Podporované|Není podporováno|
|Vytvořte laboratorní prostředí, z šablon virtuálních počítačů|Podporované|Není podporováno|
|Spuštění/zastavení/udělat snímek prostředí|Podporované|Není podporováno|
|Připojte se k prostředí pomocí Environment Vieweru|Podporované|Podporované|
|Spuštění více kopií prostředí současně pomocí izolace sítě|Podporované|Není podporováno|

### <a name="lab-management-concepts"></a>Koncepty služby Lab management

Tady jsou některé další koncepty, které byste měli znát předtím, než budete pokračovat:

|Termín|Popis|
|-|-----------------|
|Centra testovacích prostředí|V oblasti nástroje Microsoft Test Manager kde vytvoření a správa testovacích prostředí.|
|Projekt Azure DevOps Lab|Kolekce testovací prostředí, které mají nastavení, abyste se mohli připojit k nim a spustit své virtuální počítače.|
|Knihovny Azure DevOps Project|Archiv uložené virtuální počítače, šablony a uložené testovací prostředí, které se naimportovaly do skupiny hostitelů projektu. Položky můžete použít v knihovně v prostředích SCVMM; nelze je však přidat přímo do standardního prostředí. Položky nelze spustit v knihovně; Místo toho můžete využít k nasazení nového prostředí.|
|Nasazeného prostředí|Testovacím prostředí, která byla nasazena do testovacího prostředí projektu, které lze k němu připojit a spustit jeho počítače.|

Další informace o aplikaci lab management najdete v tématu:

* [Plánování testovacího prostředí](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Správa testovacího prostředí](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [Nastavení pro prostředí SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [Správa oprávnění](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Nastavení změn](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Odstraňování potíží](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Informace o nastavení prostředí najdete tady:

* [Sestavení a vydání cloudovými prostředími](use-build-or-rm-instead-of-lab-management.md)
* [Standardní testovací prostředí](https://msdn.microsoft.com/library/ee390842.aspx)
* [(Virtuální) prostředí SCVMM](https://msdn.microsoft.com/library/ee943322.aspx)
* [Vytváření a používání izolovaného síťového prostředí](https://msdn.microsoft.com/library/ee518924.aspx)

## <a name="see-also"></a>Viz také:

* [Instalace a konfigurace testovacích agentů](../../test/lab-management/install-configure-test-agents.md)
* [Průvodce správou testovacího prostředí sady Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2015/04/22/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions/)
* [Microsoft DevOps Blog](https://devblogs.microsoft.com/devops/)
