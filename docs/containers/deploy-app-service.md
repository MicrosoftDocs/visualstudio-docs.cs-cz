---
title: Nasazení kontejneru ASP.NET Core Dockeru do služby Azure App Service | Dokumenty společnosti Microsoft
description: Přečtěte si, jak pomocí nástrojů kontejnerů Sady Visual Studio nasadit do služby Azure App Service ASP.NET webovou aplikaci Core.
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027292"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Nasazení kontejneru ASP.NET Core do služby Azure App Service pomocí Visual Studia

Tento kurz vás provede pomocí Visual Studia k publikování kontejnerizované webové aplikace ASP.NET Core do [služby Azure App Service](/azure/app-service). Azure App Service je vhodná služba pro webovou aplikaci s jedním kontejnerem hostovohovou v Azure.

Pokud nemáte předplatné Azure, vytvořte si [bezplatný účet,](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) než začnete.

## <a name="prerequisites"></a>Požadavky

Pro absolvování tohoto kurzu potřebujete:

::: moniker range="vs-2017"
- Instalace nejnovější verze [Visual Studia 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s úlohou "ASP.NET a vývoj webových aplikací"
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s *ASP.NET a zatížení mno žahou webu.*
::: moniker-end
- Instalace [plochy Dockeru](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Vytvoření webové aplikace ASP.NET Core

Následující kroky vás provedou vytvořením základní aplikace ASP.NET Core, která se bude používat v tomto kurzu.

::: moniker range="vs-2017"
1. V nabídce Visual Studio vyberte **Soubor > Nový > Project**.
2. V části **Šablony** v dialogovém okně **Nový projekt** vyberte **položku Visual C# > Web**.
3. Vyberte **ASP.NET základní webovou aplikaci**.
4. Pojmenujte novou aplikaci (nebo převezměte výchozí) a vyberte **OK**.
5. Vyberte **webovou aplikaci**.
6. Zaškrtněte políčko **Povolit podporu Dockeru.**
7. Vyberte typ kontejneru **Linux** a klepněte na tlačítko **OK**. Kontejnery Windows nejsou podporované k nasazení do služby Azure App Service jako kontejner.
::: moniker-end
::: moniker range=">= vs-2019"
1. V počátečním okně sady Visual Studio zvolte **Vytvořit nový projekt**.
1. Zvolte **ASP.NET Základní webová aplikace**a zvolte **Další**.
1. Pojmenujte novou aplikaci (nebo převezměte výchozí) a zvolte **Vytvořit**.
1. Zvolte **Webová aplikace**.
1. Pomocí **zaškrtávacího** políčka Konfigurovat pro protokol HTTPS zvolte, zda chcete podporu protokolu SSL.
1. Zaškrtněte políčko **Povolit podporu Dockeru.**
1. Vyberte typ kontejneru a klepněte na **vytvořit**. Kontejnery Windows nejsou podporované k nasazení do služby Azure App Service jako kontejner.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Nasazení kontejneru do Azure

1. Klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a zvolte **Publikovat**.
1. V dialogovém okně publikovat cíl zvolte **App Service Linux** nebo App **Service**. Jedná se o operační systém, který bude hostitelem webového serveru.
1. Můžete publikovat jenom do služby App Service, nebo můžete publikovat do služby App Service a Azure Container Registry (ACR). Pokud chcete publikovat kontejner v registru kontejnerů Azure (ACR), zvolte **Vytvořit novou službu aplikace pro kontejnery**a klikněte na **Publikovat**.

   ![Snímek obrazovky s dialogem publikovat](media/deploy-app-service/publish-app-service-linux.PNG)

   Pokud chcete publikovat jenom do služby Azure App Service bez použití registru kontejnerů Azure, zvolte **Vytvořit nový**a klikněte na **Publikovat**.

1. Zkontrolujte, jestli jste přihlášení pomocí účtu, který je přidružený k vašemu předplatnému Azure, a zvolte jedinečný název, předplatné, skupinu prostředků, plán hostování a registr kontejnerů (pokud je to možné) nebo přijměte výchozí hodnoty.

   ![Snímek obrazovky s nastavením publikování](media/deploy-app-service/publish-app-service-linux2.png)

1. Zvolte **Vytvořit**. Váš kontejner se nasadí do Azure ve skupině prostředků a registru kontejnerů, který jste vybrali. Tento proces trvá trochu času. Po dokončení se na kartě **Publikovat** zobrazí informace o tom, co bylo publikováno, včetně adresy URL webu.

   ![Snímek obrazovky s kartou Publikovat](media/deploy-app-service/publish-succeeded.PNG)

1. Kliknutím na odkaz na web ověřte, že vaše aplikace funguje podle očekávání v Azure.

   ![Snímek obrazovky webové aplikace](media/deploy-app-service/web-application-running.png)

1. Profil publikování se uloží se všemi vybranými podrobnostmi, například se skupinou prostředků a registrem kontejnerů.

1. Chcete-li znovu nasadit se stejným profilem publikování, použijte tlačítko **Publikovat,** tlačítko **Publikovat** v okně **Aktivita publikování webu** nebo klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a v místní nabídce zvolte položku **Publikovat.**

## <a name="view-container-settings"></a>Zobrazit nastavení kontejneru

Na [webu Azure Portal](https://portal.azure.com)můžete otevřít nasazenou službu App Service.

Nastavení nasazené služby App Service můžete zobrazit otevřením nabídky ** Nastavení kontejneru* (pokud používáte Visual Studio 2019 verze 16.4 nebo novější).

![Snímek obrazovky s nabídkou Nastavení kontejneru na webu Azure Portal](media/deploy-app-service/container-settings-menu.png)

Odtud můžete zobrazit informace o kontejneru, zobrazit nebo stáhnout protokoly nebo nastavit průběžné nasazení. Viz [Azure App Service průběžné nasazení CI/CD](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Vyčištění prostředků

Chcete-li odebrat všechny prostředky Azure přidružené k tomuto kurzu, odstraňte skupinu prostředků pomocí [portálu Azure](https://portal.azure.com). Chcete-li najít skupinu prostředků přidruženou k publikované webové aplikaci, zvolte **Zobrazit** > další**aktivitu publikování na webu systému****Windows** > a pak zvolte ikonu ozubeného kola. Otevře se karta **Publikovat,** která obsahuje skupinu prostředků.

Na webu Azure Portal zvolte **Skupiny prostředků**, vyberte skupinu prostředků a otevřete stránku podrobností. Ověřte, zda se jedná o správnou skupinu prostředků, a pak zvolte **Odebrat skupinu prostředků**, zadejte název a zvolte **Odstranit**.

## <a name="next-steps"></a>Další kroky

Další informace o [Azure App Service Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Viz také

[Nasazení do Azure Container Registry](hosting-web-apps-in-docker.md)