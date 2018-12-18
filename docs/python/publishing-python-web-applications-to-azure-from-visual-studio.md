---
title: Publikování aplikace v Pythonu do Azure App Service
description: Možnosti pro publikování, nasazení aplikace v Pythonu do služby Azure App Service, včetně úložiště Git a kontejnery Linuxu a nasazení do služby IIS.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 1c8c48eaa777da973f0a4b21d826bbab384b4536
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066688"
---
# <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

V současné době je podporován Python ve službě Azure App Service pro Linux a publikováním aplikace s využitím [nasazení Git](#publish-to-app-service-on-linux-using-git-deploy) a [kontejnery](#publish-to-app-service-on-linux-using-containers), jak je popsáno v tomto článku.

> [!Note]
> Podpora Pythonu ve službě Azure App Service pro Windows je oficiálně zastaralá. V důsledku toho **publikovat** příkaz v sadě Visual Studio se oficiálně podporuje jenom pro [cílové služby IIS](#publish-to-iis), a vzdálené ladění ve službě Azure App Service je již nejsou oficiálně podporované.
>
> Nicméně [publikování ve službě App Service v systému Windows](publish-to-app-service-windows.md) funkce prozatím stále funguje, zůstanou přípony Python aplikace služby v systému Windows k dispozici, ale nebude opraveno nebo aktualizovány.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publikování pomocí Gitu nasaďte do služby App Service v Linuxu

Git nasazení služby App Service v Linuxu se připojí ke konkrétní větvi z úložiště Git. Potvrzení kódu do této větve automaticky nasadí do služby App Service a službu App Service automaticky nainstaluje všechny závislosti uvedené v *souboru requirements.txt*. App Service v Linuxu v tomto případě spustí kód v imagi kontejneru předem nakonfigurované, která používá webový server Gunicorn. V současné době je tato služba je ve verzi Preview a není podporována pro použití v produkčním prostředí.

Další informace naleznete v následujících článcích v dokumentaci k Azure:

- [Rychlý start: Vytvoření webové aplikace v Pythonu ve službě App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) poskytuje stručný návod Git nasaďte procesu pomocí jednoduché aplikace Flask a nasazení z místního úložiště Git.
- [Jak konfigurovat Python](/azure/app-service/containers/how-to-configure-python) popisuje vlastnosti App Service v kontejneru Linuxu a tom, jak přizpůsobit spouštěcí příkaz Gunicorn pro vaši aplikaci.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publikování do služby App Service v Linuxu pomocí kontejnerů

Aniž byste museli spoléhat na kontejneru předem vytvořených pomocí služby App Service v Linuxu, můžete zadat vlastní kontejner. Tato možnost umožňuje rozhodnout, které webové servery, které můžete použít a přizpůsobit chování kontejneru.

Existují dvě možnosti, jak vytvářet, spravovat a push kontejnerů:

- Použijte Visual Studio Code a rozšíření Dockeru, jak je popsáno na [nasazení Python s pomocí kontejnerů Dockeru](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). I v případě, že nepoužíváte Visual Studio Code, tento článek poskytuje užitečné informace o vytváření imagí kontejneru pro aplikace Flask a Django pomocí předpřipravené uwsgi a nginxu webové servery. Pak můžete nasadit tyto stejné kontejnerů pomocí Azure CLI.

- Pomocí příkazového řádku a rozhraní příkazového řádku Azure, jak je popsáno na [použití vlastní image Dockeru](/azure/app-service/containers/tutorial-custom-docker-image) v dokumentaci k Azure. Tento průvodce je obecný, ale a není specifická pro Python.

## <a name="publish-to-iis"></a>Publikování do služby IIS

Ze sady Visual Studio, můžete publikovat do virtuálního počítače s Windows nebo jiné služby IIS umožňující počítače se **publikovat** příkazu. Při použití služby IIS, je potřeba vytvořit nebo změnit *web.config* souboru v aplikaci, která říká službě IIS kde najít interpret Pythonu. Další informace najdete v tématu [konfigurace webových aplikací pro službu IIS](configure-web-apps-for-iis-windows.md).
