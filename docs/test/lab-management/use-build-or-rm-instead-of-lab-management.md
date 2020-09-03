---
title: Použít Azure Pipelines pro automatizované testování
ms.date: 10/19/2018
ms.topic: how-to
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 37455c05a010681eac343287abf25aad642328c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286840"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Použití Azure Test Plans místo Lab Management pro automatizované testování

Použijete-li Microsoft Test Manager a Lab Management pro automatizované testování nebo pro automatizaci sestavení-nasazení-testování, toto téma vysvětluje, jak lze dosáhnout stejných cílů pomocí funkcí [sestavení a vydání](/azure/devops/pipelines/index?view=vsts) v Azure Pipelines a Team Foundation Server (TFS).

> [!NOTE]
> Microsoft Test Manager je zastaralá v aplikaci Visual Studio 2017 a odebrána v aplikaci Visual Studio 2019.

## <a name="build-deploy-test-automation"></a>Automatizace sestavení – nasazení a testování

Microsoft Test Manager a Lab Management se spoléhají na definici sestavení XAML pro automatizaci sestavování, nasazování a testování vašich aplikací. Sestavení XAML spoléhá na různé konstrukce vytvořené v Microsoft Test Manager, jako je testovací prostředí, testovací sady a nastavení testování, a na různých součástech infrastruktury, jako je například kontrolér sestavení, agenti sestavení, testovací kontrolér a testovací agenty pro dosažení tohoto cíle. Můžete dosáhnout stejného s méně kroky pomocí Azure Pipelines nebo TFS.

| Postup | Pomocí sestavení XAML | V sestavení nebo vydané verzi |
|-------|----------------------|-----------------|
| Identifikujte počítače, do kterých chcete nasadit sestavení, a spusťte testy. | Pomocí těchto počítačů vytvořte standardní laboratorní prostředí v Microsoft Test Manager. | Není k dispozici |
| Identifikujte testy, které mají být spuštěny. | Vytvořte testovací sadu v Microsoft Test Manager, vytvořte testovací případy a přidružte automatizaci ke každému testovacímu případu. Vytvořte nastavení testu v Microsoft Test Manager identifikaci role počítačů v testovacím prostředí, ve kterém mají být testy spuštěny. | Pokud plánujete spravovat testování prostřednictvím testovacích plánů, vytvořte sadu automatických testů v Microsoft Test Manager stejným způsobem. Případně můžete přeskočit tuto možnost, pokud chcete spustit testy přímo z testovacích binárních souborů vytvořených sestavením. V obou případech není nutné vytvářet nastavení testu. |
| Automatizujte nasazení a testování. | Vytvořte definici sestavení XAML pomocí LabDefaultTemplate. *. XAML. Určete sestavení, testovací sady a testovací prostředí v definici sestavení. | Vytvořte [kanál sestavení nebo vydání](/azure/devops/pipelines/index?view=vsts) s jedním prostředím. Spusťte stejný skript nasazení (z definice sestavení XAML) pomocí úlohy příkazového řádku a spusťte automatizované testy pomocí úlohy testovacího agenta nasazení a spusťte úkoly funkčních testů. Zadejte seznam počítačů a jejich přihlašovací údaje jako vstupy pro tyto úlohy. |

Mezi výhody použití Azure Pipelines nebo TFS pro tento scénář patří:

* Nepotřebujete kontrolér sestavení nebo řadič testu.
* Testovací agent je nainstalován prostřednictvím úlohy jako součást sestavení nebo vydání.
* Postup nasazení lze snadno přizpůsobit. Nebudete už mít přístup k použití jednoho skriptu. Můžete také využít celou řadu úloh, které jsou k dispozici v produktu, a také v Visual Studio Marketplace.
* Nemusíte spravovat testovací sady. Můžete přímo spouštět testy z binárních souborů.
* Získáte rozsáhlejší prostředí pro vytváření sestav pro testy, které byly spuštěny v rámci každého sestavení nebo vydání.
* Můžete sledovat, které prostředky (verze, sestavení, pracovní položky, potvrzení) jsou aktuálně nasazeny a testovány v každém prostředí.
* Automatizaci můžete přizpůsobit a rozšíříte tak, aby bylo možné snadno nasadit do více testovacích prostředí a dokonce i do produkčního prostředí.
* Automatizaci můžete naplánovat tak, že dojde k vrácení se změnami nebo potvrzení nebo v konkrétní době každý den.

## <a name="self-service-management-of-scvmm-environments"></a>Samoobslužná správa prostředí SCVMM

[Centrum testování v Microsoft Test Manager](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) podporuje možnost správy knihovny šablon prostředí a zřizování prostředí na vyžádání pomocí [serveru SCVMM](/system-center/vmm/overview?view=sc-vmm-1801).

Funkce samoobslužného zřizování v centru testovacího prostředí mají dva různé cíle:

* Poskytněte jednodušší způsob správy infrastruktury. Správa virtuálních počítačů a šablon prostředí a automatické vytváření privátních sítí k izolaci klonů prostředí od sebe byly příklady správy infrastruktury.

* Poskytněte týmům jednodušší způsob využívání virtuálních počítačů ve svých aktivitách testování a nasazení. Příklady snadné spotřeby jsou vytváření testovacích prostředí přes stejný model zabezpečení projektu a integrované použití těchto virtuálních počítačů v testovacích scénářích.

Nicméně vzhledem k vývoji bohatých systémů správy veřejného a privátního cloudu, jako jsou [Microsoft Azure](https://azure.microsoft.com/) a [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), neexistuje žádný vývoj funkcí správy infrastruktury v TFS 2017 a novějším. Místo toho se bude zaměřte na snadnou spotřebu prostředků spravovaných prostřednictvím takových cloudových infrastruktur.

Následující tabulka shrnuje typické aktivity, které provedete v centru testovacích prostředí, a způsob, jakým je můžete provádět prostřednictvím SCVMM nebo Azure (Pokud se jedná o aktivity správy infrastruktury) nebo prostřednictvím TFS a Azure DevOps Services (Pokud se jedná o aktivity testování nebo nasazení):

| Postup | S centrem testovacího prostředí | V sestavení nebo vydané verzi |
|-------|-----------------|-----------------------|
| Správa knihovny šablon prostředí. | Vytvořte testovací prostředí. Nainstalujte na virtuální počítače potřebný software. Nástroj Sysprep a uložte prostředí jako šablonu v knihovně. | Konzolu pro správu SCVMM můžete použít přímo k vytvoření a správě šablon virtuálních počítačů nebo šablon služeb. Při používání Azure vyberte jednu ze [šablon Azure pro rychlý Start](https://azure.microsoft.com/resources/templates/). |
| Vytvořte testovací prostředí. | Vyberte šablonu prostředí v knihovně a nasaďte ji. Zadejte potřebné parametry pro přizpůsobení konfigurací virtuálních počítačů. | Použijte konzolu pro správu SCVMM přímo k vytvoření virtuálních počítačů nebo instancí služby ze šablon. K vytváření prostředků použijte Azure Portal přímo. Případně vytvořte definici vydané verze s prostředím. K vytvoření nových virtuálních počítačů použijte úlohy nebo úkoly Azure z [rozšíření Integration SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) . Vytvoření nové verze této definice je stejné jako vytvoření nového prostředí v centru testovacích prostředí. |
| Připojte se k počítačům. | Otevřete testovací prostředí v prohlížeči prostředí. | Použijte konzolu pro správu SCVMM přímo pro připojení k virtuálním počítačům. Případně můžete k otevření relací vzdálené plochy použít IP adresy nebo názvy DNS virtuálních počítačů. |
| Vytvoření kontrolního bodu prostředí nebo obnovení prostředí do čistého kontrolního bodu. | Otevřete testovací prostředí v prohlížeči prostředí. Vyberte možnost pro provedení kontrolního bodu nebo obnovení do předchozího kontrolního bodu. | Použijte konzolu pro správu SCVMM přímo k provedení těchto operací na virtuálních počítačích. Nebo pokud chcete tyto kroky provést v rámci většího automatizace, zahrňte jako součást prostředí v definici vydané verze úlohy kontrolního bodu z [rozšíření Integration SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) . |

## <a name="create-network-isolated-environments"></a>Vytváření prostředí s izolací sítě

Prostředí s izolací sítě je skupina virtuálních počítačů SCVMM, které je možné bezpečně klonovat, aniž by to způsobilo konflikty v síti. K tomu došlo v MTM pomocí série instrukcí, které používaly sadu síťových adaptérů ke konfiguraci virtuálních počítačů v privátní síti a další sadu síťových adaptérů pro konfiguraci virtuálních počítačů ve veřejné síti.

Azure Pipelines a TFS se ale ve spojení s úlohou sestavení a nasazení SCVMM dají použít ke správě prostředí SCVMM, zřízení izolovaných virtuálních sítí a implementaci scénářů sestavení-nasazení-testování. Úkol můžete například použít k těmto akcím:

* Vytváření, obnovování a odstraňování kontrolních bodů
* Vytvoření nových virtuálních počítačů pomocí šablony
* Spuštění a zastavení virtuálních počítačů
* Spuštění vlastních skriptů PowerShellu pro SCVMM

Další informace najdete v tématu [Vytvoření izolovaného prostředí virtuální sítě pro scénáře sestavení-nasazení-testování](/azure/devops/pipelines/targets/create-virtual-network?view=vsts).
