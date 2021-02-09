---
title: Použití přemostění na Kubernetes s využitím sady Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Naučte se, jak pomocí mostu Kubernetes se sadou Visual Studio připojit váš vývojový počítač k clusteru Kubernetes.
keywords: Přemostění do Kubernetes, Azure Dev Spaces, vývojových prostorů, Docker, Kubernetes, Azure, Containers
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: 23d060489a13aa8e02316e253d9367e9e3372bbe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859629"
---
# <a name="use-bridge-to-kubernetes"></a>Použití mostu na Kubernetes

Pomocí mostu pro Kubernetes můžete přesměrovat provoz mezi clusterem Kubernetes a kódem běžícím na vašem vývojovém počítači. Tato příručka také poskytuje skript pro nasazení rozsáhlé ukázkové aplikace s více mikroslužbami v clusteru Kubernetes.

## <a name="before-you-begin"></a>Než začnete

Tato příručka používá [ukázkovou aplikaci pro sdílení kol][bike-sharing-github] k předvedení připojení vývojového počítače ke clusteru Kubernetes. Pokud už máte svoji vlastní aplikaci spuštěnou v clusteru Kubernetes, můžete postupovat podle následujících kroků a používat i názvy vlastních služeb.

### <a name="prerequisites"></a>Požadavky

* Předplatné Azure. Pokud nemáte předplatné Azure, můžete si vytvořit [bezplatný účet](https://azure.microsoft.com/free).
* [Nainstalované rozhraní Azure CLI][azure-cli]
* [Visual Studio 2019][visual-studio] verze 16,7 Preview 4 nebo novější, které běží ve Windows 10 s nainstalovanou úlohou *vývoj pro Azure* .
* Byl [nainstalován most do rozšíření Kubernetes][btk-extension].

Také pro konzolové aplikace .NET nainstalujte balíček NuGet *Microsoft. VisualStudio. Azure. Kubernetes. Tools. targets* .

## <a name="create-a-kubernetes-cluster"></a>Vytvoření clusteru Kubernetes

Vytvořte cluster AKS v [podporované oblasti][supported-regions]. Níže uvedené příkazy vytvoří skupinu prostředků s názvem *MyResourceGroup* a cluster AKS s názvem *MyAKS*.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Instalace ukázkové aplikace

Nainstalujte do clusteru ukázkovou aplikaci pomocí poskytnutého skriptu. Tento skript můžete spustit pomocí [Azure Cloud Shell][azure-cloud-shell].

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Přejděte do ukázkové aplikace, ve které je spuštěný cluster, otevřením jeho veřejné adresy URL, která se zobrazí ve výstupu instalačního skriptu.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

Ve výše uvedeném příkladu je veřejná adresa URL `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` .

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Připojení ke clusteru a ladění služby

Ve vývojovém počítači stáhněte a nakonfigurujte rozhraní příkazového řádku Kubernetes pro připojení k vašemu clusteru Kubernetes pomocí [AZ AKS Get-Credentials][az-aks-get-credentials].

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

V úložišti [aplikace s ukázkami sdílení kol][bike-sharing-github] v GitHubu použijte rozevírací seznam na zeleném tlačítku **kód** a v **aplikaci Visual Studio vyberte otevřít** a naklonujte úložiště místně a otevřete složku v aplikaci Visual Studio. Pak použijte **soubor**  >  **Otevřít projekt** k otevření projektu **App. csproj** ve složce *Samples/BikeSharingApp/ReservationEngine* .

V projektu vyberte v rozevíracím seznamu nastavení spuštění možnost **most do Kubernetes** , jak je znázorněno níže.

![Zvolit most na Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Klikněte na tlačítko Start vedle položku *most do Kubernetes*. V dialogovém okně **vytvořit profil pro přemostění do Kubernetes** :

* Vyberte své předplatné.
* Pro svůj cluster Vyberte *MyAKS* .
* Jako obor názvů vyberte *bikeapp* .
* Pro přesměrování služby vyberte *reservationengine* .
* Vyberte *aplikaci* pro spouštěcí profil.
* Vyberte `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` adresu URL pro spuštění prohlížeče.

![Zvolit most do clusteru Kubernetes](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> Můžete přesměrovat pouze služby, které mají jeden pod.

Vyberte, jestli chcete spustit izolovaný přístup, což znamená, že vaše změny nebudou ovlivněné jinými uživateli, kteří používají cluster. Tento režim izolace se dosahuje směrováním požadavků do vaší kopie každé ovlivněné služby, ale všechny ostatní přenosy se normálně směrují. Další vysvětlení toho, jak to jde udělat, najdete v tématu [Jak funguje most na Kubernetes][btk-overview-routing].

Klikněte na **Uložit a spusťte ladění**.

Veškerý provoz v clusteru Kubernetes se přesměruje do služby *reservationengine* na verzi vaší aplikace spuštěné ve vývojovém počítači. Most do Kubernetes také směruje veškerý odchozí provoz z aplikace zpátky do vašeho clusteru Kubernetes.

> [!NOTE]
> Zobrazí se výzva, abyste umožnili *EndpointManager* spouštění zvýšených oprávnění a změny souboru hostitelů.

Váš vývojový počítač se připojí, když se na stavovém řádku zobrazí připojení ke `reservationengine` službě.

![Připojený vývojový počítač](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Při následném spuštění se nebudete vyzváni k dialogovému oknu **vytvořit profil pro přemostění do Kubernetes** . Tato nastavení aktualizujete v **ladění** ve vlastnostech projektu.

Po připojení k vývojovému počítači spustí provoz přesměrování na váš vývojový počítač pro službu, kterou nahrazujete.

## <a name="set-a-break-point"></a>Nastavení bodu přerušení

Otevřete [BikesHelper.cs][bikeshelper-cs-breakpoint] a Kliknutím kamkoli na řádku 26 umístěte kurzor do umístění. Nastavte zarážku tak, že zasáhnete klávesu *F9* nebo vyberete **ladění**  >  **Přepnout zarážku**.

Přejděte na ukázkovou aplikaci otevřením veřejné adresy URL. Jako uživatel vyberte **Aurelia Briggs (zákazník)** a pak vyberte kolo k pronajmutí. Vyberte **kolo pronájmu**. Vraťte se do sady Visual Studio a sledujte řádek 26, který je zvýrazněný. Zarážka, kterou jste nastavili, pozastavila službu na řádku 26. Pokud chcete službu obnovit, stiskněte klávesu **F5** nebo klikněte na **ladit**  >  **pokračovat**. Vraťte se do prohlížeče a ověřte, že se na stránce zobrazuje, že jste toto kolo zapůjčujíi.

Odstraňte zarážku tak, že umístíte kurzor na řádek 26 v a zapnete `BikesHelper.cs` **F9**.

> [!NOTE]
> Ve výchozím nastavení zastavování úlohy ladění také odpojí váš vývojový počítač od clusteru Kubernetes. Toto chování můžete změnit změnou možnosti **Odpojit po ladění** do `false` v části **ladicí nástroje Kubernetes** v možnostech ladění. Po aktualizaci tohoto nastavení zůstane váš vývojový počítač po zastavení a spuštění ladění připojen. Pokud chcete odpojit svůj vývojový počítač od svého clusteru, klikněte na tlačítko **Odpojit** na panelu nástrojů.

## <a name="additional-configuration"></a>Další konfigurace

Most do Kubernetes může zpracovávat směrování provozu a replikovat proměnné prostředí bez jakékoli další konfigurace. Potřebujete-li stáhnout všechny soubory, které jsou připojeny ke kontejneru v clusteru Kubernetes, jako je například soubor ConfigMap, můžete vytvořit a `KubernetesLocalProcessConfig.yaml` stáhnout tyto soubory do vývojového počítače. Další informace najdete v tématu [použití KubernetesLocalProcessConfig. yaml pro další konfiguraci s pro most na Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Používání protokolování a diagnostiky

Diagnostické protokoly můžete najít v `Bridge to Kubernetes` adresáři v *dočasném* adresáři vašeho vývojového počítače. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Odebrání ukázkové aplikace z clusteru

Pomocí poskytnutého skriptu odeberte ukázkovou aplikaci z clusteru.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Další kroky

Přečtěte si, jak přemostění na Kubernetes funguje.

> [!div class="nextstepaction"]
> [Jak funguje Přemostění na Kubernetes](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/overview.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation