---
title: Použití KubernetesLocalProcessConfig. yaml pro další konfiguraci s pro místní proces s Kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: Popisuje další možnosti konfigurace pro místní proces pomocí Kubernetes s použitím KubernetesLocalProcessConfig. yaml.
keywords: Místní proces pomocí Kubernetes, Azure Dev Spaces, vývojových prostorů, Docker, Kubernetes, Azure, AKS, Azure Kubernetes Service, Containers
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 234eacedbc08007ede6bb5745a1a289aa838cccb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87508299"
---
# <a name="configure-local-process-with-kubernetes"></a>Konfigurace místního procesu s Kubernetes

`KubernetesLocalProcessConfig.yaml`Soubor umožňuje replikovat proměnné prostředí a připojené soubory, které jsou k dispozici pro vaše lusky v clusteru AKS. V souboru můžete zadat následující akce `KubernetesLocalProcessConfig.yaml` :

* Stáhněte svazek a nastavte cestu k tomuto svazku jako proměnnou prostředí.
* Zajistěte, aby byla služba spuštěná v clusteru dostupná pro procesy běžící na vašem vývojovém počítači.
* Vytvoří proměnnou prostředí s konstantní hodnotou.

Výchozí `KubernetesLocalProcessConfig.yaml` soubor není vytvořen automaticky, takže je nutné ručně vytvořit soubor v kořenu projektu.

## <a name="download-a-volume"></a>Stažení svazku

V části *ENV*zadejte *název* a *hodnotu* pro každý svazek, který chcete stáhnout. *Název* je proměnná prostředí, která se bude používat na vašem vývojovém počítači. *Hodnota* je název svazku a cesta ve vývojovém počítači. *Hodnota value má* formu *$ (volumeMounts: VOLUME_NAME)/path/to/Files*.

Příklad:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

Výše uvedený příklad stáhne svazek *Allow-List* z kontejneru a nastaví toto umístění plus cestu k proměnné prostředí *ALLOW_LIST_PATH*. Výchozím chováním je stažení souborů do zadané cesty v dočasném adresáři ve vývojovém počítači. V předchozím příkladu je *ALLOW_LIST_PATH* nastaveno na `/TEMPORARY_DIR/allow-list` . 

> [!NOTE]
> Stažením svazku se stáhne celý obsah tohoto svazku bez ohledu na cestu, kterou jste nastavili. Cesta se používá pouze k nastavení proměnné prostředí pro použití ve vývojovém počítači. Přidání */Allow-List* nebo */path/to/Files* na konec tokenu nemá ve skutečnosti vliv na to, kde je svazek trvalý. Proměnná prostředí je jenom pohodlí pro případ, že vaše aplikace potřebuje odkaz na konkrétní soubor v daném svazku.

Místo použití dočasného adresáře máte také možnost určit umístění ke stažení připojení svazku na vývojový počítač. V části *volumeMounts*zadejte *název* a *LocalPath* pro každé konkrétní umístění. *Název* je název svazku, který chcete vyhledat, a *LocalPath* je absolutní cesta k vývojovému počítači. Příklad:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

Výše uvedený příklad používá položku v *ENV* ke stažení svazku odpovídajícího * \* výchozímu tokenu*, jako je například *Default-token-1111* nebo *Default-token-1234-5678-90abcdef*. V případech, kdy se více svazků shodují, se použije první odpovídající svazek. Všechny soubory jsou staženy do `/var/run/secrets/kubernetes.io/serviceaccount` vašeho vývojového počítače pomocí záznamu v *volumeMounts*. Proměnná prostředí *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* je nastavena na `/var/run/secrets/kubernetes.io/serviceaccount` .

## <a name="make-a-service-available"></a>Zpřístupnění služby

V části *ENV*zadejte *název* a *hodnotu* každé služby, kterou chcete zpřístupnit na svém vývojovém počítači. *Název* je proměnná prostředí, která se bude používat na vašem vývojovém počítači. *Hodnota* je název služby z vašeho clusteru a cesta. *Hodnota value má* formu *$ (Services: service_name)/Path*.

Příklad:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

Výše uvedený příklad zpřístupní službu *Myapp1* pro váš vývojový počítač a proměnná prostředí *MYAPP1_SERVICE_HOST* je nastavená na místní IP adresu služby *Myapp1* s `/api/v1` cestou (tj `127.1.1.4/api/v1` .). Služba *Myapp1* je přístupná pomocí proměnné prostředí, *Myapp1*nebo *Myapp1. svc. cluster. Local*.

> [!NOTE]
> Zpřístupnění služby na vašem vývojovém počítači zajistí dostupnost celé služby bez ohledu na cestu, kterou jste nastavili. Cesta se používá pouze k nastavení proměnné prostředí pro použití ve vývojovém počítači.
Můžete také vytvořit službu z konkrétního oboru názvů Kubernetes, který je dostupný pomocí *$ (Services: service_name. NAMESPACE_NAME)*. Příklad:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

Výše uvedený příklad zpřístupní *myapp2* z oboru názvů *MyNamespace* ve vývojovém počítači a nastaví proměnnou prostředí *MYAPP2_SERVICE_HOST* na místní IP adresu *myapp2* z oboru názvů *MyNamespace* .

## <a name="create-an-environment-variable-with-a-constant-value"></a>Vytvoří proměnnou prostředí s konstantní hodnotou.

V části *ENV*zadejte *název* a *hodnotu* pro každou proměnnou prostředí, kterou chcete vytvořit ve vývojovém počítači. *Název* je proměnná prostředí, která bude použita ve vývojovém počítači, a *hodnota* je hodnota. Příklad:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

Výše uvedený příklad vytvoří proměnnou prostředí s názvem *DEBUG_MODE* s hodnotou *true*.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>Příklad KubernetesLocalProcessConfig. yaml

Tady je příklad kompletního `KubernetesLocalProcessConfig.yaml` souboru:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Další kroky

Pokud chcete začít používat místní proces s Kubernetes pro připojení k vašemu místnímu vývojovému počítači ke svému clusteru, přečtěte si téma [použití místního procesu s Kubernetes s Visual Studio Code][local-process-kubernetes-vs-code] a [použití místního procesu s Kubernetes se sadou Visual Studio][local-process-kubernetes-vs].

[local-process-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/local-process-kubernetes
[local-process-kubernetes-vs]: local-process-kubernetes.md
