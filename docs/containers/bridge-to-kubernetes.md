---
title: 'Kurz: propojení vývojových počítačů s mostem do Kubernetes'
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: tutorial
description: Připojte svůj vývojový počítač k Kubernetes clusteru s mostem na Kubernetes se sadou Visual Studio.
keywords: Přemostění do Kubernetes, Azure Dev Spaces, vývojových prostorů, Docker, Kubernetes, Azure, Containers
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: b8d6c98d2e2146ad57871b74cd2d522ed2b04259
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046115"
---
# <a name="tutorial-use-bridge-to-kubernetes-to-connect-your-clusters-and-your-development-computers"></a>Kurz: použití přemostění k Kubernetes k připojení clusterů a vašich vývojových počítačů

V tomto kurzu se naučíte, jak pomocí mostu pro Kubernetes přesměrovat provoz mezi clusterem Kubernetes a kódem běžícím na vašem vývojovém počítači. 

Tato příručka také poskytuje skript pro nasazení rozsáhlé ukázkové aplikace s více mikroslužbami v clusteru Kubernetes.

Přečtěte si další informace o mostu pro Kubernetes s článkem, [Jak funguje most na Kubernetes](overview-bridge-to-kubernetes.md).

## <a name="prerequisites"></a>Požadavky

- Cluster Kubernetes
- [Visual Studio 2019][visual-studio] verze 16,7 Preview 4 nebo novější běžící ve Windows 10.
- [Přemostění do nainstalovaného rozšíření Kubernetes][btk-extension]

## <a name="about-the-data"></a>Informace o datech

V tomto kurzu se používá most k Kubernetes k vývoji verze mikroslužeb jednoduché ukázkové aplikace TODO v jakémkoli clusteru Kubernetes. Tato [ukázková aplikace TODO][todo-app-github]s použitím sady Visual Studio byla přizpůsobena z kódu poskytovaného pomocí [TodoMVC](http://todomvc.com). 

 Tyto kroky by měly fungovat s jakýmkoli clusterem Kubernetes. Takže pokud už máte svoji vlastní aplikaci spuštěnou v clusteru Kubernetes, můžete postupovat podle následujících kroků a používat i názvy vlastních služeb.

Ukázka aplikace TODO se skládá z front-endu a back-endu, který zajišťuje trvalé úložiště. Tato rozšířená ukázka přidá komponentu statistiky a ukončí aplikaci na několik mikroslužeb, konkrétně:

- Front-end volá rozhraní API databáze pro zachování a aktualizaci položek TODO;
- Služba databázového rozhraní API spoléhá na databázi Mongo, aby zachovala položky TODO.
- Front-end zapisuje události přidání, dokončení a odstranění do fronty RabbitMQ;
- Pracovní proces statistiky přijímá události z fronty RabbitMQ a aktualizuje mezipaměť Redis.
- Rozhraní API pro statistiku zpřístupňuje statistiku pro front-end, která se má zobrazit.

U všech se tato rozšířená aplikace TODO skládá ze šesti vzájemně souvisejících komponent.


## <a name="check-the-cluster"></a>Ověřit cluster

Otevřete příkazový řádek a ověřte, že `kubectl` je nainstalovaný a v cestě je cluster, který chcete použít, dostupný a připravený a nastavte kontext na tento cluster.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

kde {Context-Name} je název kontextu clusteru, který chcete použít pro ukázku TODO-App.

## <a name="deploy-the-application"></a>Nasazení aplikace

Naklonujte [úložiště mindaro](https://github.com/Microsoft/mindaro) a otevřete příkazové okno s aktuální pracovní složkou pro *Samples/TODO-App*.

Vytvořte obor názvů pro ukázku.

```cmd
kubectl create namespace todo-app
```

Pak použijte manifest nasazení:

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Toto je jednoduché nasazení, které zpřístupňuje front-end pomocí služby typu `LoadBalancer` . Počkejte, až budou všechny lusky spuštěné a že externí IP adresa služby bude k `frontend` dispozici.

Pokud testujete pomocí MiniKube, budete muset použít `minikube tunnel` k vyřešení externí IP adresy. Pokud používáte AKS nebo jiného cloudového poskytovatele Kubernetes, automaticky se přiřadí externí IP adresa. Pomocí následujícího příkazu monitorujte `frontend` službu a počkejte, než bude spuštěna:

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Přejděte k aplikaci pomocí externí IP adresy a místního portu (první číslo ve sloupci PORT (y)).

```
http://{external-ip}:{local-port}
```

Otestujte spuštěnou aplikaci v prohlížeči. Při přidávání, dokončování a odstraňování položek TODO si všimněte, že se stránka s statistikami aktualizuje s očekávanými metrikami.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Připojení ke clusteru a ladění služby

Otevřete *samples\todo-app\database-api\database-API.csproj* v aplikaci Visual Studio. V projektu vyberte v rozevíracím seznamu nastavení spuštění možnost **most do Kubernetes** , jak je znázorněno níže.

![Zvolit most na Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Klikněte na tlačítko Start vedle položku *most do Kubernetes*. V dialogovém okně **vytvořit profil pro přemostění do Kubernetes** :

- Vyberte název clusteru.
- Vyberte *TODO-App* pro váš obor názvů.
- Vyberte *databáze – rozhraní API* pro přesměrování služby.
- Vyberte stejnou adresu URL, kterou jste dříve použili pro spuštění prohlížeče, http://{external-IP}: {Local-Port}

![Zvolit most do clusteru Kubernetes](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Vyberte, jestli chcete spustit izolovaný přístup, což znamená, že vaše změny nebudou ovlivněné jinými uživateli, kteří používají cluster. Tento režim izolace se dosahuje směrováním požadavků do vaší kopie každé ovlivněné služby, ale všechny ostatní přenosy se normálně směrují. Další vysvětlení toho, jak to jde udělat, najdete v tématu [Jak funguje most na Kubernetes][btk-overview-routing].

Klikněte na **OK**. Veškerý provoz v clusteru Kubernetes se přesměruje pro službu *databázového rozhraní API* na verzi vaší aplikace spuštěné ve vývojovém počítači. Most do Kubernetes také směruje veškerý odchozí provoz z aplikace zpátky do vašeho clusteru Kubernetes.

> [!NOTE]
> Zobrazí se výzva, abyste umožnili *EndpointManager* spouštění zvýšených oprávnění a změny souboru hostitelů.

Váš vývojový počítač se připojí, když se na stavovém řádku zobrazí připojení ke `database-api` službě.

![Připojený vývojový počítač](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Při následném spuštění se nebudete vyzváni k dialogovému oknu **vytvořit profil pro přemostění do Kubernetes** . Tato nastavení aktualizujete v **ladění** ve vlastnostech projektu.

Po připojení k vývojovému počítači spustí provoz přesměrování na váš vývojový počítač pro službu, kterou nahrazujete.

> [!NOTE]
> Chcete-li upravit ladicí profil později, například pokud chcete testovat s jinou službou Kubernetes, vyberte možnost **ladění**  >  **vlastností ladění** a klikněte na tlačítko **změnit** .

## <a name="set-a-break-point"></a>Nastavení bodu přerušení

Otevřete MongoHelper. cs a kliknutím někam na řádku 68 v metodě CreateTask – umístěte kurzor do umístění. Nastavte zarážku tak, že zasáhnete klávesu *F9* nebo vyberete **ladění**  >  **Přepnout zarážku**.

Přejděte do ukázkové aplikace otevřením veřejné adresy URL (externí IP adresa pro službu front-end). Pokud chcete službu obnovit, stiskněte klávesu **F5** nebo klikněte na **ladit**  >  **pokračovat**.

Odstraňte zarážku tak, že umístíte kurzor na řádek se zarážkou a zapnete **F9**.

> [!NOTE]
> Ve výchozím nastavení zastavování úlohy ladění také odpojí váš vývojový počítač od clusteru Kubernetes. Toto chování můžete změnit změnou možnosti **Odpojit po ladění** do `false` v části **Nástroje pro ladění Kubernetes** v   >  dialogovém okně **Možnosti** nástrojů. Po aktualizaci tohoto nastavení zůstane váš vývojový počítač po zastavení a spuštění ladění připojen. Pokud chcete odpojit svůj vývojový počítač od svého clusteru, klikněte na tlačítko **Odpojit** na panelu nástrojů.
>
>![Snímek obrazovky s možnostmi ladění Kubernetes](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Další konfigurace

Most do Kubernetes může zpracovávat směrování provozu a replikovat proměnné prostředí bez jakékoli další konfigurace. Potřebujete-li stáhnout všechny soubory, které jsou připojeny ke kontejneru v clusteru Kubernetes, jako je například soubor ConfigMap, můžete vytvořit a `KubernetesLocalProcessConfig.yaml` stáhnout tyto soubory do vývojového počítače. Další informace najdete v tématu [použití KubernetesLocalProcessConfig. yaml pro další konfiguraci s pro most na Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Používání protokolování a diagnostiky

Diagnostické protokoly můžete najít v `Bridge to Kubernetes` adresáři v *dočasném* adresáři vašeho vývojového počítače.

## <a name="next-steps"></a>Další kroky

Přečtěte si, jak přemostění na Kubernetes funguje.

> [!div class="nextstepaction"]
> [Jak funguje Přemostění na Kubernetes](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
