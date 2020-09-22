---
title: Jak funguje most na Kubernetes
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Popisuje procesy pro připojení vašeho vývojového počítače ke clusteru Kubernetes pomocí mostu pro Kubernetes.
keywords: Most do Kubernetes, Docker, Kubernetes, Azure, kontejnery
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: fbb3cfe6453c68079cb4b4cc6b57f8494f45c0cc
ms.sourcegitcommit: f9179a3a6d74fbd871f62b72491e70b9e7b05637
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2020
ms.locfileid: "90845846"
---
# <a name="how-bridge-to-kubernetes-works"></a>Jak funguje most na Kubernetes

Most do Kubernetes umožňuje spouštět a ladit kód ve vývojovém počítači, ale je stále připojený ke svému clusteru Kubernetes se zbytkem vaší aplikace nebo služeb. Například pokud máte rozsáhlou architekturu mikroslužeb s mnoha vzájemně závislými službami a databázemi, může být obtížné replikovat tyto závislosti na vašem vývojovém počítači. Kromě toho může být při vytváření a nasazování kódu do clusteru Kubernetes pro každou změnu kódu během vývoje ve vnitřní smyčce pomalý, časově náročný a obtížný použití s ladicím programem.

Most na Kubernetes zabraňuje sestavení a nasazení kódu do clusteru, a to místo toho, aby se vytvořilo připojení přímo mezi vývojovým počítačem a vaším clusterem. Připojení vývojového počítače ke clusteru během ladění umožňuje rychlou otestování a vývoj vaší služby v kontextu plné aplikace bez vytvoření jakékoli konfigurace Docker nebo Kubernetes.

Most do Kubernetes přesměruje provoz mezi připojeným clusterem Kubernetes a vaším vývojovým počítačem. Toto přesměrování provozu umožňuje kódu na vašem vývojovém počítači a službách spuštěných v clusteru Kubernetes komunikovat jako v případě, že jsou ve stejném clusteru Kubernetes. Most do Kubernetes také poskytuje způsob, jak replikovat proměnné prostředí a připojené svazky k dispozici do lusků ve vašem clusteru Kubernetes ve vývojovém počítači. Poskytnutí přístupu k proměnným prostředí a připojeným svazkům ve vývojovém počítači vám umožní rychle pracovat na svém kódu, aniž byste tyto závislosti museli replikovat ručně.

> [!WARNING]
> Most do Kubernetes je určený jenom pro vývojové a testovací scénáře. Není určena ani podporována pro použití s provozními clustery nebo službami Live v aktivním použití.

## <a name="using-bridge-to-kubernetes"></a>Použití mostu na Kubernetes

Pokud chcete použít přemostění na Kubernetes v aplikaci Visual Studio, potřebujete [Visual studio 2019][visual-studio] verze 16,7 Preview 4 nebo novější, které běží na Windows 10 s nainstalovanou úlohou *vývoje ASP.NET a webu* a [přemostění na rozšíření Kubernetes][btk-extension] nainstalované. Pokud k navázání připojení ke clusteru Kubernetes použijete přemostění na Kubernetes, máte možnost přesměrovat veškerý provoz do a z existujícího objektu v clusteru do vašeho vývojového počítače.

> [!NOTE]
> Při použití mostu na Kubernetes se zobrazí výzva k zadání názvu služby, která se má přesměrovat do vašeho vývojového počítače. Tato možnost je pohodlný způsob, jak identifikovat pod pro přesměrování. Všechna přesměrování mezi clusterem Kubernetes a vaším vývojovým počítačem jsou pro objekt pod.

Když most do Kubernetes naváže připojení ke clusteru,:

* Zobrazí výzvu ke konfiguraci služby, která má být nahrazena v clusteru, portu ve vývojovém počítači, který má být použit pro váš kód, a úlohu spuštění pro váš kód jako jednorázovou akci.
* Nahradí kontejner v části pod clusterem se vzdáleným kontejnerem agenta, který přesměruje provoz do vašeho vývojového počítače.
* Spustí [kubectl][kubectl-port-forward] na svém vývojovém počítači a přesměruje provoz z vývojového počítače do vzdáleného agenta spuštěného v clusteru.
* Shromažďuje informace o prostředí z vašeho clusteru pomocí vzdáleného agenta. Toto jsou informace o prostředí, včetně proměnných prostředí, viditelných služeb, připojení svazků a tajných připojení.
* Nastaví prostředí v sadě Visual Studio tak, aby služba ve vývojovém počítači mohla přistupovat ke stejným proměnným, jako kdyby byla spuštěna v clusteru.  
* Aktualizuje soubor hostitelů, aby mapoval služby na váš cluster na místní IP adresy ve vývojovém počítači. Tyto položky souborů hostitelů umožňují, aby kód spuštěný ve vývojovém počítači vytvářely požadavky na jiné služby spuštěné v clusteru. Pokud chcete aktualizovat soubor hostitelů, přemostění na Kubernetes se požádá o přístup správce na vašem vývojovém počítači při připojování ke clusteru.
* Spustí běh a ladění kódu ve vývojovém počítači. V případě potřeby bude most na Kubernetes uvolnit požadované porty ve vývojovém počítači tím, že zastavuje služby nebo procesy, které tyto porty aktuálně používají.

Po navázání připojení ke clusteru můžete spustit a ladit kód nativně ve vašem počítači bez vytváření kontejnerů a kód může přímo pracovat se zbytkem vašeho clusteru. Veškerý síťový provoz, který vzdálený agent obdrží, se přesměruje na místní port zadaný během připojení, takže váš nativní běžící kód může přijmout a zpracovat tento provoz. Proměnné prostředí, svazky a tajné klíče z vašeho clusteru jsou zpřístupněny kódu běžícímu na vašem vývojovém počítači. Kromě toho, že se položky souborů hostitelů a přesměrování portů přidávají do vašeho vývojového počítače, prostřednictvím mostu na Kubernetes, váš kód může odesílat síťový provoz do služeb spuštěných v clusteru pomocí názvů služeb z vašeho clusteru a tento provoz se předává do služeb spuštěných ve vašem clusteru. Provoz se směruje mezi vývojovým počítačem a vaším clusterem a celou dobu, po kterou jste se připojili.

Kromě toho přemostění na Kubernetes poskytuje způsob, jak replikovat proměnné prostředí a připojené soubory, které jsou k dispozici ve vašem clusteru ve vývojovém počítači, prostřednictvím `KubernetesLocalProcessConfig.yaml` souboru. Tento soubor můžete také použít k vytvoření nových proměnných prostředí a připojení svazků.

> [!NOTE]
> Po dobu trvání připojení ke clusteru (plus dalších 15 minut) spustí most na Kubernetes proces s názvem *EndpointManager* s oprávněními správce v místním počítači.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Další konfigurace pomocí KubernetesLocalProcessConfig. yaml

`KubernetesLocalProcessConfig.yaml`Soubor umožňuje replikovat proměnné prostředí a připojené soubory, které jsou k dispozici pro vaše lusky v clusteru. Další informace o dalších možnostech konfigurace najdete v tématu [Konfigurace mostu na Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Používání možností směrování pro vývoj v izolaci

Ve výchozím nastavení přesměruje most do Kubernetes veškerý provoz pro službu do vašeho vývojového počítače. Máte také možnost použít možnosti směrování jenom pro přesměrování požadavků do služby pocházející z subdomény do vašeho vývojového počítače. Tyto možnosti směrování umožňují využít most do Kubernetes k tomu, abyste mohli vyvíjet izolaci a Nerušit ostatní přenosy v clusteru.

Následující animace znázorňuje dva vývojáře pracující na stejném clusteru v izolaci:

![Animovaný obrázek ve formátu GIF – ilustrující izolaci](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

Když povolíte izolaci na izolovaném prostředí, most na Kubernetes spolu s připojením ke clusteru Kubernetes zahrnuje následující:

* Ověří, jestli cluster Kubernetes nemá povolený Azure Dev Spaces.
* Provede replikaci zvolené služby v clusteru ve stejném oboru názvů a přidá popisek *Routing.VisualStudio.IO/Route-from=service_name* a *Routing.VisualStudio.IO/Route-on-Header=Kubernetes-Route-as: GENERATED_NAME* anotaci.
* Nakonfiguruje a spustí Správce směrování ve stejném oboru názvů v clusteru Kubernetes. Správce směrování používá selektor popisku k vyhledání popisku *Routing.VisualStudio.IO/Route-from=service_name* a  *Routing.VisualStudio.IO/Route-on-Header=Kubernetes-Route-as: GENERATED_NAME* anotace při konfiguraci směrování ve vašem oboru názvů.

Pokud most na Kubernetes zjistí, že je ve vašem clusteru Kubernetes povolený Azure Dev Spaces, budete vyzváni k zakázání Azure Dev Spaces předtím, než budete moci použít most na Kubernetes.

Správce směrování při spuštění provede následující kroky:
* Duplikuje všechny příchozí přenosy nalezené v oboru názvů pomocí *GENERATED_NAME* pro subdoménu. 
* Vytvoří zástupné pod pro každou službu přidruženou s duplicitními příchozími přenosy s *GENERATED_NAME* subdoménou.
* Vytvoří další zástupné pod pro službu, na které pracujete, v izolaci. To umožňuje směrovat požadavky s subdoménou do vašeho vývojového počítače.
* Konfiguruje pravidla směrování pro každý zástupné pod tím, aby zpracovávala směrování služeb s subdoménou.

Následující diagram znázorňuje cluster Kubernetes před tím, než se most připojí ke clusteru Kubernetes:

![Diagram clusteru bez mostu do Kubernetes](media/bridge-to-kubernetes/kubr-cluster.svg)

Následující diagram znázorňuje stejný cluster s mostem na Kubernetes povolený v izolovaném režimu. Tady vidíte duplicitní službu a zástupnéá lusky, které podporují směrování v izolaci.

![Diagram clusteru s povoleným přemostěním na Kubernetes](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

Při přijetí žádosti s poddoménou *GENERATED_NAME* v clusteru se do žádosti přidá hlavička *Kubernetes-Route-as = GENERATED_NAME* . Zástupné lusky zařídí směrování, které požaduje příslušnou službu v clusteru. Pokud je požadavek směrován do služby, která se zpracovává v izolaci, je tento požadavek přesměrován do vývojového počítače vzdáleným agentem.

Pokud je v clusteru přijata žádost bez subdomény *GENERATED_NAME* , do žádosti se nepřidá žádné záhlaví. Zástupné lusky zařídí směrování, které požaduje příslušnou službu v clusteru. Pokud je požadavek směrován do služby, která je měněna, je místo vzdáleného agenta směrován do původní služby.

> [!IMPORTANT]
> Každá služba v clusteru musí při vytváření dalších požadavků předávat hlavičku *Kubernetes-Route-as = GENERATED_NAME* . Například když *Služba* obdrží požadavek, odešle požadavek na *serviceB* před vrácením odpovědi. V tomto příkladu musí *služba Service* . v žádosti o *serviceB*předávat hlavičku *Kubernetes-Route-as = GENERATED_NAME* . Některé jazyky, například [ASP.NET][asp-net-header], mohou mít metody pro zpracování šíření hlaviček.

Při odpojení od clusteru se ve výchozím nastavení most do Kubernetes odebere ze všech zástupné a duplicitních služeb. 

> [!NOTE]
> Nasazení a služba správy směrování v oboru názvů zůstanou spuštěné. Chcete-li odebrat nasazení a službu, spusťte následující příkazy pro váš obor názvů.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnostika a protokolování

Při použití přemostění na Kubernetes pro připojení ke clusteru se diagnostické protokoly z vašeho clusteru protokolují do *dočasného* adresáře vašeho vývojového počítače ve složce *most do složky Kubernetes* .

## <a name="limitations"></a>Omezení

Most na Kubernetes má následující omezení:

* Služba musí být za účelem připojení k této službě zajištěna jedním pod. Nemůžete se připojit ke službě s více lusky, jako je třeba služba s replikami.
* Objekt pod může mít v takovém případě k úspěšnému připojení pouze jeden kontejner spuštěný v takovém případě pro přemostění na Kubernetes. Most do Kubernetes se nemůže připojit ke službám s lusky, které mají další kontejnery, jako jsou například kontejnery na vozíky vložené pomocí sítí služby.
* Most do Kubernetes potřebuje zvýšená oprávnění ke spuštění ve vývojovém počítači, aby bylo možné upravit soubor hostitelů.
* Most na Kubernetes se nedá použít u clusterů s povoleným Azure Dev Spaces.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Most do Kubernetes a clusterů s povoleným Azure Dev Spaces

Most nelze použít pro Kubernetes v clusteru s povoleným Azure Dev Spaces. Pokud chcete použít přemostění na Kubernetes v clusteru s povoleným Azure Dev Spaces, je nutné před připojením ke clusteru zakázat Azure Dev Spaces.

## <a name="next-steps"></a>Další kroky

Pokud chcete začít používat přemostění na Kubernetes pro připojení k vašemu místnímu počítači pro vývoj ke svému clusteru, přečtěte si téma [použití mostu na Kubernetes](bridge-to-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md