---
title: Publikování aplikace v Pythonu pro Azure App Service
description: Možnosti publikování aplikace v Pythonu pro Azure App Service, včetně nasazení a kontejnerů Git pro Linux a nasazení do služby IIS.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b2848a54ddbce41b538bf58f82db42ede76026d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912413"
---
# <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

V současnosti je Python podporován v Azure App Service pro Linux a aplikace můžete publikovat pomocí nasazení a [kontejnerů](#publish-to-app-service-on-linux-using-containers) [Git](#publish-to-app-service-on-linux-using-git-deploy) , jak je popsáno v tomto článku.

> [!Note]
> Podpora Pythonu pro Azure App Service pro Windows je oficiálně zastaralá. V důsledku toho je příkaz **publikovat** v sadě Visual Studio oficiálně podporován pouze pro [Cíl služby IIS](#publish-to-iis)a vzdálené ladění v Azure App Service již není oficiálně podporováno.
>
> [Publikování na App Service ve funkcích Windows](publish-to-app-service-windows.md) ale pořád funguje v době, protože rozšíření Pythonu pro App Service ve Windows zůstávají dostupná, ale nebudou se obsluhovat ani aktualizovat.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publikování na App Service v systému Linux pomocí nasazení Git

Nasazení Git připojí App Service v systému Linux ke konkrétní větvi úložiště Git. Potvrzení kódu do této větve se automaticky nasadí do App Service a App Service automaticky nainstaluje všechny závislosti uvedené v *requirements.txt*. V takovém případě App Service v systému Linux spustí kód v předem nakonfigurované imagi kontejneru, která používá webový server Gunicorn. V současné době je tato služba ve verzi Preview a není podporovaná pro produkční použití.

Další informace najdete v následujících článcích v dokumentaci k Azure:

- [Rychlý Start: Vytvoření webové aplikace v Pythonu v App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) poskytuje krátký návod k procesu nasazení Git pomocí jednoduché aplikace a nasazení z místního úložiště Git.
- [Postup konfigurace Pythonu](/azure/app-service/containers/how-to-configure-python) popisuje charakteristiky App Service v kontejneru Linux a postup přizpůsobení spouštěcího příkazu Gunicorn pro vaši aplikaci.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publikování na App Service v systému Linux pomocí kontejnerů

Místo toho, abyste se spoléhali na předem sestavený kontejner s App Service v systému Linux, můžete poskytnout vlastní kontejner. Tato možnost umožňuje vybrat webové servery, které používáte, a přizpůsobit chování kontejneru.

Existují dvě možnosti pro sestavování, správu a vložení kontejnerů:

- Použijte Visual Studio Code a rozšíření Docker, jak je popsáno v tématu [nasazení Pythonu pomocí kontejnerů Docker](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). I v případě, že Visual Studio Code nepoužíváte, článek poskytuje užitečné informace o vytváření imagí kontejnerů pro aplikace v baňce a Django, které využívají webové servery uwsgi a Nginx připravené pro produkční prostředí. Pak můžete stejný kontejner nasadit pomocí rozhraní příkazového řádku Azure CLI.

- Použijte příkazový řádek a Azure CLI, jak je popsáno v dokumentaci k Azure v tématu [použití vlastní image Docker](/azure/app-service/containers/tutorial-custom-docker-image) . Tato příručka je obecná, ale není specifická pro Python.

## <a name="publish-to-iis"></a>Publikování ve službě IIS

Ze sady Visual Studio můžete publikovat na virtuálním počítači s Windows nebo do jiného počítače s podporou služby IIS pomocí příkazu **publikovat** . Při používání služby IIS nezapomeňte v aplikaci vytvořit nebo upravit soubor *web.config* , který oznamuje službě IIS, kde se nachází interpret Pythonu. Další informace najdete v tématu [Konfigurace webových aplikací pro službu IIS](configure-web-apps-for-iis-windows.md).
