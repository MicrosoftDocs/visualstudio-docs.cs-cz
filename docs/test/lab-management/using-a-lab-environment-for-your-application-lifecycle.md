---
title: Použití testovacího prostředí pro devops
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75847293"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Použití laboratorního prostředí pro vaše devops

Testovací prostředí je kolekce virtuálních a fyzických počítačů, které můžete použít k vývoji a testování aplikací. Testovací prostředí může obsahovat více rolí potřebných k testování vícevrstvých aplikací, jako jsou pracovní stanice, webové servery a databázové servery. Kromě toho můžete použít pracovní postup sestavení a nasazení a testování s testovacím prostředím k automatizaci procesu vytváření, nasazování a spouštění automatizovaných testů ve vaší aplikaci.

* **Použití testovacího plánu ke spuštění automatizovaných testů** – můžete spustit kolekci automatizovaných testů, nazývanou *testovací plán*a zobrazit průběh.

* **Použití pracovního postupu sestavení a nasazení a testování** – pracovní postup sestavení a nasazení a testování můžete použít k automatickému testování vícevrstvých aplikací. Typickým příkladem je pracovní postup, který spustí sestavení, nasadí soubory sestavení do příslušných počítačů v testovacím prostředí a pak provede automatizované testy. Kromě toho můžete naplánovat spuštění pracovního postupu v určitých intervalech.

* **Shromažďujte diagnostická data ze všech strojů, a to i při ručním testování** - Můžete shromažďovat diagnostická data z více strojů současně. Například během jednoho testu můžete shromažďovat IntelliTrace, dopad testu a další formy dat z webového serveru, databázového serveru a klienta.

Zde jsou příklady běžných topologie laboratorního prostředí:

| Topologie | Popis |
|---|---|
|![Topologie pouze serveru](../media/topology_backend.png)| Toto testovací prostředí má *topologii serveru*, která se často používá ke spuštění ručních testů v serverových aplikacích a která umožňuje testerům používat vlastní klientské počítače k ověření chyb v prostředí. V topologii back-endu obsahuje testovací prostředí pouze servery. Při použití tohoto typu topologie se obvykle připojujete k serverům v testovacím prostředí pomocí klientského počítače, který není součástí prostředí.|
|![Prostředí cloudové laboratoře](../media/topology_cloud.png)| Toto testovací prostředí poskytuje podobné funkce a funkce jako _topologie serveru_, ale odebere požadavek na fyzické nebo virtuální počítače spuštěné v místním prostředí. což může zkrátit dobu nastavení, zjednodušit údržbu a minimalizovat náklady. Nastavení více webů a virtuálních počítačů spolu s vlastní sítí je rychlé a snadné v cloudovém prostředí, jako je Microsoft Azure.|
|![Testovací prostředí klient-server](../media/topology_clientserver.png)| Toto testovací prostředí má *topologii klient-server*, která se často používá k testování aplikace, která má serverové a klientské součásti. V topologii klient/server jsou všechny klientské a serverové počítače používané k testování vaší aplikace v testovacím prostředí. Při použití této topologie můžete shromažďovat testovací data z každého počítače, který má vliv na vaše testy.|

| | |
|---|---|
| ![ikona filmové kamery pro video](../../install/media/video-icon.png) | [Podívejte se](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) na video o správě testovacích prostředí pro testování. |

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Použití cloudu s Azure Pipelines nebo Team Foundation Server Build and Release

Můžete provádět automatizované testování a automatizaci sestavení a nasazení a testování pomocí funkcí [sestavení a vydání](/azure/devops/pipelines/index?view=vsts) v Team Foundation Server (TFS) a Azure Test Plans. Některé z výhod jsou:

* Nepotřebujete řadič sestavení nebo testovací řadič.
* Testovací agent je nainstalován prostřednictvím úlohy jako součást sestavení nebo vydání.
* Je snadné přizpůsobit kroky nasazení. Již nejste omezeni používat jeden skript. Můžete také využít mnoho úkolů, které jsou k dispozici v produktu, stejně jako na webu Visual Studio Marketplace.
* Nemusíte udržovat testovací sady. Můžete přímo spustit testy z binárních souborů.
* Získáte bohatší prostředí pro vytváření vřádících řádků pro testy, které běží v rámci každého sestavení nebo vydání.
* Můžete sledovat, které prostředky (vydání, sestavení, pracovní položky, potvrzení) jsou aktuálně nasazeny a testovány v každém prostředí.
* Automatizaci můžete přizpůsobit a rozšířit tak, aby se snadno nasazuje do více testovacích prostředí a dokonce i do produkčního prostředí.
* Automatizaci můžete naplánovat vždy, když dojde ke vrácení se změnami nebo potvrzení nebo v určitou dobu každý den.

Další informace naleznete v [tématu Použití správy sestavení nebo vydání](use-build-or-rm-instead-of-lab-management.md).

## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Použití funkcí visual studio lab management u Microsoft Test Manager

Při použití edice Visual Studio Enterprise můžete vytvářet a spravovat testovací prostředí pomocí funkcí visual studio lab management u Microsoft Test Manageru.

Lab Management automaticky nainstaluje testovací agenty do každého počítače ve vašem prostředí.

Pokud používáte Lab Management ve spojení s System Center Virtual Machine Manager (SCVMM), získáte také tyto výhody při použití testovacího prostředí:

* **Rychle reprodukovat konfigurace počítačů** – můžete ukládat kolekce virtuálních počítačů, které jsou nakonfigurované k opětovnému vytvoření typických produkčních prostředí. Potom můžete provést každý test spustit na novou kopii uloženého prostředí.

* **Reprodukovat přesné podmínky chyby** – Při spuštění testu se nezdaří, můžete uložit kopii stavu testovacího prostředí a přístup k němu z výsledků sestavení nebo pracovní položky.

* **Spusťte více kopií testovacího prostředí současně** – můžete spustit více kopií testovacího prostředí současně bez konfliktů názvů.

### <a name="standard-environments-and-scvmm-environments"></a>Standardní prostředí a prostředí SCVMM

Existují dva typy testovacích prostředí, které můžete vytvořit pomocí správy sady Visual Studio Lab: **standardní prostředí** a **prostředí SCVMM**. Možnosti každého typu prostředí jsou však různé.

**Standardní prostředí:** může obsahovat kombinaci virtuálních a fyzických počítačů. Virtuální počítače můžete také přidat do standardního prostředí, které jsou spravované virtualizačními rámci jiných výrobců. Standardní prostředí navíc nevyžadují další serverové prostředky, například server SCVMM.

**Prostředí SCVMM:** může obsahovat pouze virtuální počítače, které jsou spravované SCVMM (System Center Virtual Machine Manager), takže virtuální počítače v prostředíCh SCVMM lze spustit pouze v rámci virtualizace Hyper-V. Prostředí SCVMM však poskytují následující funkce automatizace a správy, které nejsou k dispozici ve standardních prostředích:

- **Snímky prostředí:** Snímky prostředí obsahují stav testovacího prostředí, takže můžete rychle obnovit čisté prostředí nebo uložit stav prostředí, které bylo změněno. Pracovní postup sestavení a nasazení a testování můžete také automatizovat proces ukládání a obnovení snímků prostředí.

- **Uložená prostředí:** Můžete uložit kopii prostředí SCVMM a potom nasadit více kopií tohoto prostředí.

- **Izolace sítě:** Izolace sítě umožňuje současně spouštět více identických kopií prostředí SCVMM bez konfliktu názvů počítačů.

- **Šablony virtuálních strojů:** Šablona virtuálního počítače je virtuální počítač, kterému byl odebrán název a další identifikátory. Když je šablona virtuálního počítače nasazená v prostředí SCVMM, Microsoft Test Manager generuje nové identifikátory. To umožňuje nasadit více kopií virtuálního počítače ve stejném prostředí nebo ve více prostředích a potom spustit virtuální počítače současně.

- **Uložené virtuální počítače:** Virtuální počítač, který je uložen v knihovně projektu a obsahuje jedinečné identifikátory.

> [!NOTE]
> Správa testovacího prostředí nepodporuje SCVMM 2016.

Informace o smpaměti SCVMM naleznete [v tématu Virtual Machine Manager](/azure/devops/pipelines/?view=vsts).

Standardní prostředí a prostředí SCVMM podporují mnoho stejných funkcí. Nicméně, tam jsou některé důležité rozdíly, aby zvážila. Následující tabulka porovnává funkce, které jsou k dispozici pro standardní prostředí a prostředí SCVMM.

|Schopnost|Prostředí SCVMM|Standardní prostředí|
|-|------------------------|-|
|**Testování**|||
|Spustit ruční testy|Podporuje se|Podporuje se|
|Spuštění kódovaného ui a dalších automatizovaných testů|Podporuje se|Podporuje se|
|Chyby bohaté na soubory pomocí diagnostických adaptérů|Podporuje se|Podporuje se|
|**Nasazení sestavení**|||
|Automatické pracovní postupy sestavení,nasazování a testování|Podporuje se|Podporuje se|
|**Tvorba a správa prostředí**|||
|Kromě virtuálních počítačů používejte fyzické počítače|Nepodporuje se|Podporuje se|
|Použití virtuálních počítačů třetích stran|Nepodporuje se|Podporuje se|
|Automatická instalace testovacích agentů do počítačů v laboratorním prostředí|Podporuje se|Podporuje se|
|Uložení a nasazení stavu testovacího prostředí pomocí snímků prostředí|Podporuje se|Nepodporuje se|
|Vytvoření testovacích prostředí ze šablon virtuálních počítače|Podporuje se|Nepodporuje se|
|Prostředí Start/stop/snímek|Podporuje se|Nepodporuje se|
|Připojení k prostředí pomocí Prohlížeče prostředí|Podporuje se|Podporuje se|
|Spuštění více kopií prostředí současně pomocí izolace sítě|Podporuje se|Nepodporuje se|

### <a name="lab-management-concepts"></a>Koncepce správy laboratoří

Zde jsou některé další koncepty, které byste měli znát, než budete pokračovat:

|Označení|Popis|
|-|-----------------|
|Laboratorní centrum|Oblast Microsoft Test Manager, kde můžete vytvářet a spravovat testovací prostředí.|
|Azure DevOps Project Lab|Kolekce testovacích prostředí, které byly nastaveny tak, abyste se k nim mohli připojit a spustit jejich virtuální počítače.|
|Knihovna projektů Azure DevOps|Archiv uložených virtuálních počítačů, šablon a uložených testovacích prostředí, které byly importovány do hostitelské skupiny projektu. Položky v knihovně můžete použít s prostředími SCVMM. nelze je však přidat přímo do standardního prostředí. Položky v knihovně nelze spustit. místo toho je použijete k nasazení nového prostředí.|
|Nasazené prostředí|Testovací prostředí, které bylo nasazeno do testovacího prostředí projektu, takže se k němu můžete připojit a spustit jeho počítače.|

Další informace o správě testovacího prostředí naleznete v tématu:

* [Naplánujte si svou laboratoř](https://msdn.microsoft.com/library/ff756575%28v=vs.140%29.aspx)
* [Správa laboratoře](https://msdn.microsoft.com/library/dd936084%28v=vs.140%29.aspx)
* [Nastavení pro prostředí SCVMM](https://msdn.microsoft.com/library/dd380687%28v=vs.140%29.aspx)
* [Správa oprávnění](https://msdn.microsoft.com/library/dd380760%28v=vs.140%29.aspx)
* [Změnit nastavení](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
* [Řešení potíží](https://msdn.microsoft.com/library/ee853230%28v=vs.140%29.aspx)

Informace o nastavení prostředí naleznete v tématu:

* [Vytváření a vydávání cloudových prostředí](use-build-or-rm-instead-of-lab-management.md)
* [Standardní laboratorní prostředí](https://msdn.microsoft.com/library/ee390842.aspx)
* [SCVMM (virtuální) prostředí](https://msdn.microsoft.com/library/ee943322.aspx)
* [Vytváření a používání izolovaného síťového prostředí](https://msdn.microsoft.com/library/ee518924.aspx)

## <a name="see-also"></a>Viz také

* [Instalace a konfigurace testovacích agentů](../../test/lab-management/install-configure-test-agents.md)
* [Průvodce správou laboratoří sady Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2015/04/22/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions/)
* [Blog Microsoft DevOps](https://devblogs.microsoft.com/devops/)
