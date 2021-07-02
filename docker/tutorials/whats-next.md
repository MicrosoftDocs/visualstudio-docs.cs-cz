---
title: Kurz Dockeru – Co dál
description: Popisuje možnosti rozšíření aplikací Dockeru pomocí orchestrace pomocí projektů Cloud Native Computing Foundation.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: e777d80f44c9a11e4d2a893c968d33e348ca442a
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222692"
---
# <a name="whats-next"></a>Kam dál

I když jste s kurzem hotovi, je toho ještě mnohem víc, co se o kontejnerech dozvíte!
Tady se do hloubky nezadáte, ale tady je několik dalších oblastí, na které se můžete podívat v další části.

## <a name="container-orchestration"></a>Orchestrace kontejnerů

Spouštění kontejnerů v produkčním prostředí je obtížné. Nechcete se přihlašovat k počítači a jednoduše spustit `docker run` nebo `docker-compose up` . Proč ne? Co se stane, když kontejnery umřou? Jak můžete škálovat napříč několika počítači? Tento problém řeší orchestrace kontejnerů. Tento problém pomáhají vyřešit nástroje, jako je Kubernetes, Swarm, Nomad a AKS, a to vše trochu různými způsoby.

Obecným nápadem je, že máte "manažery", kteří obdrží **očekávaný stav**. Tento stav může být "Chci spustit dvě instance webové aplikace a zveřejnit port 80". Manažeři pak prohlédněte všechny počítače v clusteru a delegovat práci na pracovní uzly. Manažeři sledují změny (například ukončují kontejner)  a pak pracují na skutečném stavu, který odráží očekávaný stav.

## <a name="cloud-native-computing-foundation-projects"></a>Základní projekty nativní pro cloud computing

TENTO PROGRAMF je neutrální dodavatelský domov pro různé open source projekty, včetně Kubernetes, Prometheus, Envoy, Linkerd, NATS a dalších! Odstupňované a [inkubované](https://www.cncf.io/projects/) projekty si můžete prohlédnout tady a celou oblast [NCF tady.](https://landscape.cncf.io/) Existuje mnoho projektů, které vám pomůžou řešit problémy související s monitorováním, protokolováním, zabezpečením, registry obrázků, zasíláním zpráv a prováděním dalších věcí.

Takže pokud s vývojem aplikací nativních pro cloud a prostředí kontejnerů ještě ne, vítá vás! Připojte se ke komunitě, ptejte se a pokračujte v učení. Jsme rádi, že vás máme!

## <a name="working-with-docker-in-vs-code"></a>Práce s Dockerem v VS Code

Další informace o používání rozšíření VS Code Docker:

- [VS Code Přehled rozšíření Dockeru](https://code.visualstudio.com/docs/containers/overview)
- [Začínáme s Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Začínáme s Pythonem](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Začínáme s .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Ladění kontejnerizovaných aplikací](https://code.visualstudio.com/docs/containers/debug-common)
