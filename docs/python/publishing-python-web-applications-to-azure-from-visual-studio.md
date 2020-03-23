---
title: Publikování aplikace Pythonu do služby Azure App Service
description: Možnosti publikování aplikace Pythonu do služby Azure App Service, včetně nasazení Gitu a kontejnerů pro Linux a nasazení do Služby IIS.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: c3c8d6c16f2f7e432b6b5e988bf63521f3dfc8c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784112"
---
# <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

V současné době je Python podporovaný ve službě Azure App Service pro Linux a můžete publikovat aplikace pomocí [gitnasazení](#publish-to-app-service-on-linux-using-git-deploy) a [kontejnerů](#publish-to-app-service-on-linux-using-containers), jak je popsáno v tomto článku.

> [!Note]
> Podpora Pythonu ve službě Azure App Service pro Windows se oficiálně zastaralá. V důsledku toho je příkaz **Publikovat** v sadě Visual Studio oficiálně podporován pouze pro [cíl služby IIS](#publish-to-iis)a vzdálené ladění ve službě Azure App Service již není oficiálně podporováno.
>
> Publikování na app service v [systému Windows](publish-to-app-service-windows.md) funkce však stále funguje v současné době, jako rozšíření Pythonu pro službu aplikace v systému Windows zůstávají k dispozici, ale nebudou obsluhovány nebo aktualizovány.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publikování do služby App Service na Linuxu pomocí nasazení Gitu

Git deploy propojuje službu App Service v Linuxu s určitou větví úložiště Git. Potvrzení kódu do této větve se automaticky nasadí do služby App Service a služba App Service automaticky nainstaluje všechny závislosti uvedené v *souboru requirements.txt*. V tomto případě app service na Linuxu spustí váš kód v předem nakonfigurované image kontejneru, který používá webový server Gunicorn. V současné době je tato služba ve verzi Preview a není podporována pro produkční použití.

Další informace najdete v následujících článcích v dokumentaci k Azure:

- [Úvodní příručka: Vytvoření webové aplikace Pythonu ve službě App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) poskytuje krátký návod procesu nasazení Gitu pomocí jednoduché aplikace Flask a nasazení z místního úložiště Git.
- [Jak nakonfigurovat Python](/azure/app-service/containers/how-to-configure-python) popisuje charakteristiky app service na linuxovém kontejneru a jak přizpůsobit příkaz spuštění Gunicorn pro vaši aplikaci.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publikovat do služby App Service na Linuxu pomocí kontejnerů

Místo spoléhání se na předem sestavený kontejner se službou App Service na Linuxu můžete poskytnout vlastní kontejner. Tato možnost umožňuje zvolit, které webové servery používáte, a přizpůsobit chování kontejneru.

Kontejnery můžete vytvářet, spravovat a vystrnadit dvě možnosti:

- Použijte visual studio kód a rozšíření Dockeru, jak je popsáno v [nasazení Pythonu pomocí kontejnerů Dockeru](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). I v případě, že nepoužíváte Visual Studio kód, článek poskytuje užitečné podrobnosti o vytváření ibližů kontejnerů pro flask a Django aplikace pomocí produkční uwsgi a nginx webové servery. Potom můžete nasadit stejný kontejner pomocí azure cli.

- Použijte příkazový řádek a Azure CLI, jak je popsáno na [použití vlastní image Dockeru](/azure/app-service/containers/tutorial-custom-docker-image) v dokumentaci K Azuru. Tato příručka je však obecná a není specifická pro Python.

## <a name="publish-to-iis"></a>Publikovat do iis

Z visual studia můžete publikovat do virtuálního počítače se systémem Windows nebo jiného počítače podporujícího službu IIS pomocí příkazu **Publikovat.** Při používání služby IIS nezapomeňte vytvořit nebo upravit soubor *web.config* v aplikaci, která informuje službu IIS, kde nalezne překladač Pythonu. Další informace naleznete v [tématu Konfigurace webových aplikací pro službu IIS](configure-web-apps-for-iis-windows.md).
