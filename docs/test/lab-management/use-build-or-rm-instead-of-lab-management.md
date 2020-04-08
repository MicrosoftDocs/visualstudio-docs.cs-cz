---
title: Použití Azure Pipelines pro automatizované testování
ms.date: 10/19/2018
ms.topic: conceptual
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ca762c103ab5b3d3e94b3117dd9570787562b002
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880127"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Použití testovacích plánů Azure namísto správy testovacího prostředí pro automatizované testování

Pokud používáte Microsoft Test Manager a Lab Management pro automatizované testování nebo pro automatizaci sestavení nasazení a testování, toto téma vysvětluje, jak můžete dosáhnout stejných cílů pomocí [funkce sestavení a vydání](/azure/devops/pipelines/index?view=vsts) v Azure Pipelines a Team Foundation Server (TFS).

> [!NOTE]
> Microsoft Test Manager se v Sadě Visual Studio 2017 zanese a v sadě Visual Studio 2019 se odebere.

## <a name="build-deploy-test-automation"></a>Automatizace sestavení a nasazení a testování

Microsoft Test Manager a Lab Management spoléhají na definici sestavení XAML pro automatizaci sestavení, nasazení a testování vašich aplikací. Sestavení XAML závisí na různých konstrukcích vytvořených ve Správci testů společnosti Microsoft, jako je testovací prostředí, testovací sady a nastavení testování, a na různých součástech infrastruktury, jako je například řadič sestavení, agenti sestavení, testovací řadič a testovací agenti k dosažení tohoto cíle. Tosamé můžete provést s menším počtem kroků pomocí Azure Pipelines nebo TFS.

| Kroky | Se sestavením XAML | V sestavení nebo vydání |
|-------|----------------------|-----------------|
| Identifikujte počítače, do kterých chcete nasadit sestavení, a spouštějte testy. | Vytvořte standardní testovací prostředí ve Správci testů společnosti Microsoft s těmito počítači. | neuvedeno |
| Identifikujte testy, které mají být spuštěny. | Vytvořte testovací sadu ve Správci testů společnosti Microsoft, vytvořte testovací případy a přidružte automatizaci ke každému testovacímu případu. Vytvořte nastavení testu ve Správci testů společnosti Microsoft identifikující roli počítačů v testovacím prostředí, ve kterém by měly být testy spuštěny. | Vytvořte automatickou testovací sadu ve Správci testů microsoftu stejným způsobem, pokud plánujete spravovat testování prostřednictvím testovacích plánů. Případně můžete přeskočit, pokud chcete spustit testy přímo z binárních souborů testu vytvořených sestaveními. Není nutné vytvářet nastavení testu v obou případech. |
| Automatizujte nasazení a testování. | Vytvořte definici sestavení XAML pomocí labdefaulttemplate.*.xaml. Zadejte sestavení, testovací sady a testovací prostředí v definici sestavení. | Vytvořte [kanál sestavení nebo uvolnění](/azure/devops/pipelines/index?view=vsts) s jedním prostředím. Spusťte stejný skript nasazení (z definice sestavení XAML) pomocí úlohy příkazového řádku a spusťte automatizované testy pomocí úloh Nasazení testovacího agenta a spuštění funkčních testů. Zadejte seznam počítačů a jejich pověření jako vstupy pro tyto úkoly. |

Některé výhody použití Azure Pipelines nebo TFS pro tento scénář jsou:

* Nepotřebujete řadič sestavení nebo testovací řadič.
* Testovací agent je nainstalován prostřednictvím úlohy jako součást sestavení nebo vydání.
* Je snadné přizpůsobit kroky nasazení. Již nejste omezeni používat jeden skript. Můžete také využít mnoho úkolů, které jsou k dispozici v produktu, stejně jako na webu Visual Studio Marketplace.
* Není třeba udržovat testovací sady. Můžete přímo spustit testy z binárních souborů.
* Získáte bohatší prostředí pro vytváření vřádících řádků pro testy, které byly spuštěny v rámci každého sestavení nebo vydání.
* Můžete sledovat, které prostředky (vydání, sestavení, pracovní položky, potvrzení) jsou aktuálně nasazeny a testovány v každém prostředí.
* Automatizaci můžete přizpůsobit a rozšířit tak, aby se snadno nasazuje do více testovacích prostředí a dokonce i do produkčního prostředí.
* Automatizaci můžete naplánovat vždy, když dojde ke vrácení se změnami nebo potvrzení nebo v určitou dobu každý den.

## <a name="self-service-management-of-scvmm-environments"></a>Samoobslužná správa prostředí SCVMM

[Testovací centrum ve Správci testů společnosti Microsoft](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) podporuje možnost spravovat knihovnu šablon prostředí a zřizování prostředí na vyžádání pomocí serveru [SCVMM](/system-center/vmm/overview?view=sc-vmm-1801).

Samoobslužné zřizovací funkce Lab Center mají dva odlišné cíle:

* Poskytněte jednodušší způsob správy infrastruktury. Správa šablon virtuálních podniků a prostředí a automatické vytváření privátních sítí pro vzájemnou izolátí klonů prostředí byly příklady správy infrastruktury.

* Poskytněte týmům jednodušší způsob, jak využívat virtuální počítače v jejich testovacích a naovacích aktivitách. Zpřístupnění testovacích prostředí prostřednictvím stejného modelu zabezpečení projektu a integrované použití těchto virtuálních počítačů v testovacích scénářích byly příklady snadné spotřeby.

Vzhledem k vývoji bohatších systémů správy veřejného a soukromého cloudu, jako jsou [Microsoft Azure](https://azure.microsoft.com/) a Microsoft [Azure Stack](https://azure.microsoft.com/overview/azure-stack/), však v TFS 2017 a dalších aplikacích neexistuje žádný vývoj funkcí správy infrastruktury. Místo toho pokračuje zaměření na snadnou spotřebu prostředků spravovaných prostřednictvím těchto cloudových infrastruktur.

Následující tabulka shrnuje typické aktivity, které provádíte v Centru testovacího prostředí, a způsob, jakým je můžete provést prostřednictvím scvmm nebo Azure (pokud se jedná o aktivity správy infrastruktury) nebo prostřednictvím TFS a Azure DevOps Services (pokud se jedná o aktivity testování nebo nasazení):

| Kroky | S Lab Center | V sestavení nebo vydání |
|-------|-----------------|-----------------------|
| Správa knihovny šablon prostředí. | Vytvořte testovací prostředí. Nainstalujte potřebný software na virtuálních počítačích. Sysprep a uložit prostředí jako šablonu v knihovně. | Pomocí konzoly pro správu SCVMM přímo vytvořte a spravujte šablony virtuálních strojů nebo šablony služeb. Při používání Azure vyberte jednu ze [šablon azure quickstart](https://azure.microsoft.com/resources/templates/). |
| Vytvořte testovací prostředí. | Vyberte šablonu prostředí v knihovně a nasaďte ji. Zadejte potřebné parametry pro přizpůsobení konfigurací virtuálních počítačů. | Pomocí konzoly pro správu SCVMM přímo vytvořte virtuální počítače nebo instance služeb ze šablon. K vytváření prostředků použijte portál Azure přímo. Nebo vytvořte definici verze s prostředím. K vytvoření nových virtuálních počítačů použijte úkoly nebo úkoly Azure z [rozšíření Integrace SCVMM.](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) Vytvoření nové verze této definice je ekvivalentní k vytvoření nového prostředí v Centru testovacího prostředí. |
| Připojte se k strojům. | Otevřete testovací prostředí v prohlížeči Prostředí. | Pomocí konzoly pro správu SCVMM se můžete připojit přímo k virtuálním počítačům. Případně můžete k otevření relací vzdálené plochy použít IP adresu nebo názvy DNS virtuálních počítačů. |
| Vezměte kontrolní bod prostředí nebo obnovit prostředí čistého kontrolního bodu. | Otevřete testovací prostředí v prohlížeči Prostředí. Vyberte možnost pro kontrolní bod nebo obnovení předchozího kontrolního bodu. | Pomocí konzoly pro správu SCVMM přímo k provádění těchto operací na virtuálních počítačích. Nebo chcete-li provést tyto kroky jako součást větší automatizace, zahrnout úlohy kontrolního bodu z [rozšíření integrace SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) jako součást prostředí v definici verze. |

## <a name="create-network-isolated-environments"></a>Vytváření prostředí izolovaných v síti

Síťové izolované testovací prostředí je skupina virtuálních počítačů SCVMM, které lze bezpečně klonovat, aniž by došlo ke konfliktům v síti. To bylo provedeno v MTM pomocí řady instrukcí, které používají sadu karet síťového rozhraní ke konfiguraci virtuálních počítačů v privátní síti a další sadu karet síťového rozhraní pro konfiguraci virtuálních počítačů ve veřejné síti.

Azure Pipelines a TFS, ve spojení s úlohou sestavení a nasazení SCVMM, se však dá použít ke správě prostředí SCVMM, zřizování izolovaných virtuálních sítí a implementaci scénářů sestavení a nasazení a testování. Tuto úlohu můžete například použít k:

* Vytváření, obnovení a odstraňování kontrolních bodů
* Vytvoření nových virtuálních počítačů pomocí šablony
* Spuštění a zastavení virtuálních počítačů
* Spuštění vlastních skriptů prostředí PowerShell pro SCVMM

Další informace naleznete [v tématu Vytvoření izolovaného prostředí virtuální sítě pro scénáře sestavení a nasazení a testování](/azure/devops/pipelines/targets/create-virtual-network?view=vsts).
