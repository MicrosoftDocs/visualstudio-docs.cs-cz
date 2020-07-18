---
title: Jak funguje místní proces s Kubernetes
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Popisuje procesy pro připojení vašeho vývojového počítače ke clusteru Kubernetes pomocí místního procesu s Kubernetes.
keywords: Místní proces s Kubernetes, Docker, Kubernetes, Azure, kontejnery
monikerRange: '>=vs-2019'
ms.openlocfilehash: adde9d8ecab93bdb6f0aebbd74730ef60bd80cf6
ms.sourcegitcommit: 510a928153470e2f96ef28b808f1d038506cce0c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2020
ms.locfileid: "86454304"
---
# <a name="how-local-process-with-kubernetes-works"></a>Jak funguje místní proces s Kubernetes

Místní proces s Kubernetes umožňuje spouštět a ladit kód na vašem vývojovém počítači, ale stále je připojený ke svému clusteru Kubernetes se zbytkem vaší aplikace nebo služeb. Například pokud máte rozsáhlou architekturu mikroslužeb s mnoha vzájemně závislými službami a databázemi, může být obtížné replikovat tyto závislosti na vašem vývojovém počítači. Kromě toho může být při vytváření a nasazování kódu do clusteru Kubernetes pro každou změnu kódu během vývoje ve vnitřní smyčce pomalý, časově náročný a obtížný použití s ladicím programem.

Místní proces s Kubernetes zabraňuje sestavení a nasazení kódu do clusteru, a to tak, že vytvoří připojení přímo mezi vývojovým počítačem a vaším clusterem. Připojení vývojového počítače ke clusteru během ladění umožňuje rychlou otestování a vývoj vaší služby v kontextu plné aplikace bez vytvoření jakékoli konfigurace Docker nebo Kubernetes.

Místní proces s Kubernetes přesměruje provoz mezi připojeným clusterem Kubernetes a vaším vývojovým počítačem. Toto přesměrování provozu umožňuje kódu na vašem vývojovém počítači a službách spuštěných v clusteru Kubernetes komunikovat jako v případě, že jsou ve stejném clusteru Kubernetes. Místní proces s Kubernetes také poskytuje způsob, jak replikovat proměnné prostředí a připojené svazky k dispozici do lusků ve vašem clusteru Kubernetes ve vývojovém počítači. Poskytnutí přístupu k proměnným prostředí a připojeným svazkům ve vývojovém počítači vám umožní rychle pracovat na svém kódu, aniž byste tyto závislosti museli replikovat ručně.

## <a name="using-local-process-with-kubernetes"></a>Použití místního procesu s Kubernetes

Pokud chcete použít místní proces s Kubernetes v aplikaci Visual Studio, budete potřebovat [Visual Studio 2019][visual-studio] verze 16,7 Preview 4 nebo novější, které běží ve Windows 10 s nainstalovanou úlohou *vývoje ASP.NET a webu* a nainstalovanou [příponou Local Process Kubernetes][lpk-extension] . Když použijete místní proces s Kubernetes k navázání připojení ke clusteru Kubernetes, máte možnost přesměrovat veškerý provoz do a z existujícího objektu v clusteru do vašeho vývojového počítače.

> [!NOTE]
> Při použití místního procesu s Kubernetes se zobrazí výzva k zadání názvu služby, která se má přesměrovat do vašeho vývojového počítače. Tato možnost je pohodlný způsob, jak identifikovat pod pro přesměrování. Všechna přesměrování mezi clusterem Kubernetes a vaším vývojovým počítačem jsou pro objekt pod.

Když místní proces s Kubernetes vytvoří připojení ke clusteru,:

* Zobrazí výzvu ke konfiguraci služby, která má být nahrazena v clusteru, portu ve vývojovém počítači, který má být použit pro váš kód, a úlohu spuštění pro váš kód jako jednorázovou akci.
* Nahradí kontejner v části pod clusterem se vzdáleným kontejnerem agenta, který přesměruje provoz do vašeho vývojového počítače.
* Spustí [kubectl][kubectl-port-forward] na svém vývojovém počítači a přesměruje provoz z vývojového počítače do vzdáleného agenta spuštěného v clusteru.
* Shromažďuje informace o prostředí z vašeho clusteru pomocí vzdáleného agenta. Toto jsou informace o prostředí, včetně proměnných prostředí, viditelných služeb, připojení svazků a tajných připojení.
* Nastaví prostředí v sadě Visual Studio tak, aby služba ve vývojovém počítači mohla přistupovat ke stejným proměnným, jako kdyby byla spuštěna v clusteru.  
* Aktualizuje soubor hostitelů, aby mapoval služby na váš cluster na místní IP adresy ve vývojovém počítači. Tyto položky souborů hostitelů umožňují, aby kód spuštěný ve vývojovém počítači vytvářely požadavky na jiné služby spuštěné v clusteru. Pokud chcete aktualizovat soubor hostitelů, místní proces s Kubernetes se požádá o přístup správce na vašem vývojovém počítači při připojování ke clusteru.
* Spustí běh a ladění kódu ve vývojovém počítači. Pokud je to nutné, místní proces s Kubernetes uvolní požadované porty ve vývojovém počítači tím, že zastavuje služby nebo procesy, které tyto porty aktuálně používají.

Po navázání připojení ke clusteru můžete spustit a ladit kód nativně ve vašem počítači bez vytváření kontejnerů a kód může přímo pracovat se zbytkem vašeho clusteru. Veškerý síťový provoz, který vzdálený agent obdrží, se přesměruje na místní port zadaný během připojení, takže váš nativní běžící kód může přijmout a zpracovat tento provoz. Proměnné prostředí, svazky a tajné klíče z vašeho clusteru jsou zpřístupněny kódu běžícímu na vašem vývojovém počítači. Kromě toho, že z důvodu položek souborů hosta a přesměrování portů přidaných do vašeho vývojářského počítače místním procesem s Kubernetes, může váš kód odesílat síťový provoz do služeb spuštěných ve vašem clusteru pomocí názvů služeb z vašeho clusteru a tento provoz se předává do služeb spuštěných ve vašem clusteru. Provoz se směruje mezi vývojovým počítačem a vaším clusterem a celou dobu, po kterou jste se připojili.

## <a name="diagnostics-and-logging"></a>Diagnostika a protokolování

Při použití místního procesu s Kubernetes pro připojení ke clusteru se diagnostické protokoly z vašeho clusteru protokolují do [dočasného adresáře][azds-tmp-dir]vašeho vývojového počítače.

## <a name="limitations"></a>Omezení

Místní proces s Kubernetes má následující omezení:

* Místní proces s Kubernetes přesměruje provoz pro jednu službu do vašeho vývojového počítače. Místní proces se Kubernetes nejde použít k přesměrování několika služeb současně.
* Služba musí být za účelem připojení k této službě zajištěna jedním pod. Nemůžete se připojit ke službě s více lusky, jako je třeba služba s replikami.
* Objekt pod může mít v takovém případě pouze jeden kontejner spuštěný pro místní proces s Kubernetes pro úspěšné připojení. Místní proces s Kubernetes se nemůže připojit ke službám s lusky, které mají další kontejnery, jako jsou například kontejnery na postranní vozíky vložené pomocí sítí služby.
* Místní proces s Kubernetes potřebuje zvýšená oprávnění ke spuštění ve vývojovém počítači, aby bylo možné upravit soubor hostitelů.

## <a name="next-steps"></a>Další kroky

Pokud chcete začít používat místní proces s Kubernetes a připojit se k místnímu počítači pro vývoj ke svému clusteru, přečtěte si téma [použití místního procesu s Kubernetes](local-process-kubernetes.md).

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro