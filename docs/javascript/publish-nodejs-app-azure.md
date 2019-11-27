---
title: Publikování aplikace v Node.js do služby App Service v Linuxu
description: Aplikace Node. js vytvořené v aplikaci Visual Studio můžete publikovat na platformě Azure App Service
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c304aca5171e1addab9a941105f11fb534eaa5ff
ms.sourcegitcommit: e825d1223579b44ee2deb62baf4de0153f99242a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474016"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publikování aplikace Node. js do Azure (Linux App Service)

Tento kurz vás provede úkolem vytvoření jednoduché aplikace Node. js a její publikování do Azure.

Při publikování aplikace Node. js do Azure je k dispozici několik možností. Mezi ně patří Azure App Service, virtuální počítač s operačním systémem vašeho výběru, Azure Container Service (AKS) pro správu pomocí Kubernetes, instance kontejneru s použitím Docker a další. Další podrobnosti o každé z těchto možností najdete v tématu [COMPUTE](https://azure.microsoft.com/product-categories/compute/).

V tomto kurzu nasadíte aplikaci na [Linux App Service](/azure/app-service/containers/app-service-linux-intro).
Linux App Service nasadí kontejner pro Linux Docker pro spuštění aplikace Node. js (na rozdíl od App Service Windows, která spouští aplikace Node. js za IIS ve Windows).

V tomto kurzu se dozvíte, jak vytvořit aplikaci Node. js počínaje šablonou, která je nainstalovaná s Node.js Tools for Visual Studio, nahrajte kód do úložiště na GitHubu a potom zřídíte Azure App Service prostřednictvím webového portálu Azure, abyste ho mohli nasadit z Úložiště GitHub. Chcete-li použít příkazový řádek ke zřízení Azure App Service a vložení kódu z místního úložiště Git, přečtěte si téma [Vytvoření aplikace Node. js](/azure/app-service/containers/quickstart-nodejs).

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvořit projekt Node.js
> * Vytvoření úložiště GitHub pro kód
> * Vytvoření App Service pro Linux v Azure
> * Nasazení na Linux

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje Node. js.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2019, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2017, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úloha Node.js v instalačním programu VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud se nainstalovaný modul runtime nerozpozná, můžete projekt nakonfigurovat na stránce vlastností pomocí odkazu na nainstalovaný modul runtime (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu a zvolte **Vlastnosti**).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Vytvoření projektu Node. js pro spuštění v Azure

1. Otevřít Visual Studio.

1. Vytvořte novou aplikaci TypeScript Express.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **Node. js**a pak zvolte **vytvořit novou základní aplikaci Azure Node. js Express 4** (TypeScript). V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte **TypeScript**a pak zvolte **Node. js**. V prostředním podokně zvolte **základní aplikace Node. js Express 4**a pak zvolte **OK**.

    ![Vytvoření nové aplikace TypeScript Express](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Pokud nevidíte základní šablonu projektu **aplikace Node. js Express 4 v Azure** , musíte přidat úlohu **vývoje Node. js** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

    Visual Studio vytvoří projekt a otevře ho v Průzkumník řešení (pravé podokno).

1. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci a ujistěte se, že vše funguje podle očekávání.

1. Vyberte **soubor** > **Přidat do správy zdrojového kódu** a vytvořte pro projekt místní úložiště Git.

    V tomto okamžiku aplikace v Node. js používající rozhraní Express Framework a napsaná v nástroji TypeScript funguje a vrácena se změnami na místní správu zdrojového kódu.

1. Než budete pokračovat k dalším krokům, upravte projekt podle potřeby.

## <a name="push-code-from-visual-studio-to-github"></a>Vložení kódu ze sady Visual Studio do GitHubu

Nastavení GitHubu pro Visual Studio:

1. Zajistěte, aby bylo nainstalované a povolené [rozšíření GitHub pro Visual Studio](https://visualstudio.github.com/) , a to pomocí položek nabídky **nástroje** > **rozšíření a aktualizace**.

2. V nabídce vyberte **zobrazení** > **jiných oknech** > **GitHubu**.

    Otevře se okno GitHub.

3. Pokud v okně GitHubu nevidíte **tlačítko Začínáme, klikněte na** **soubor** > **Přidat do správy zdrojových kódů** a počkejte na aktualizaci uživatelského rozhraní.

    ![Otevřít okno GitHubu](../javascript/media/azure-github-get-started.png)

4. Klikněte **na Začínáme.**

    Pokud jste již připojeni k GitHubu, sada nástrojů vypadá podobně jako na následujícím obrázku.

    ![Nastavení úložiště GitHub](../javascript/media/azure-github-publish.png)

5. Vyplňte pole pro publikování nového úložiště a pak klikněte na **publikovat**.

    Po chvíli se zobrazí banner s oznámením, že se úspěšně vytvořilo úložiště.

    V další části se dozvíte, jak publikovat z tohoto úložiště do Azure App Service v systému Linux.

## <a name="create-a-linux-app-service-in-azure"></a>Vytvoření App Service pro Linux v Azure

1. Přihlaste se k [Azure Portal](https://portal.azure.com).

2. V seznamu služeb vlevo vyberte **App Services** a pak klikněte na **Přidat**.

3. V případě potřeby vytvořte novou skupinu prostředků a App Service Naplánujte hostování nové aplikace.

4. Ujistěte se, že jste nastavili **operační systém** na **Linux**, a nastavte **zásobník modulu runtime** na požadovanou verzi Node. js, jak je znázorněno na obrázku.

    ![Vytvoření App Service pro Linux](../javascript/media/azure-create-appservice-annotated.png)

5. Kliknutím na **vytvořit** vytvořte App Service.

    Nasazení může trvat několik minut.

6. Po nasazení přejdete do části **nastavení aplikace** a přidáte nastavení s názvem `SCM_SCRIPT_GENERATOR_ARGS` a hodnotou `--node`.

    ![Nastavení aplikací](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Proces nasazení App Service používá sadu heuristik k určení typu aplikace, kterou chcete vyzkoušet a spustit. Pokud. v nasazeném obsahu se zjistil soubor *sln* , který bude předpokládat nasazení projektu založeného na MSBuild. Nastavení přidané výše Přepisuje tuto logiku a explicitně určuje, že se jedná o aplikaci Node. js. Bez tohoto nastavení se aplikace Node. js nespustí při nasazení, pokud. soubor *sln* je součástí úložiště nasazeného do App Service.

7. V části **nastavení aplikace**přidejte další nastavení s názvem `WEBSITE_NODE_DEFAULT_VERSION` a hodnotu `8.9.0`.

8. Po nasazení otevřete App Service a vyberte **Možnosti nasazení**.

    ![Možnosti nasazení](../javascript/media/azure-deployment-options.png)

9. Klikněte na **Zvolit zdroj**a pak zvolte **GitHub**a pak nakonfigurujte všechna požadovaná oprávnění.

    ![Oprávnění GitHubu](../javascript/media/azure-choose-source.png)

10. Vyberte úložiště a větev, které chcete publikovat, a pak vyberte **OK**.

    ![Publikování do App Service pro Linux](../javascript/media/azure-repo-and-branch.png)

    Během synchronizace se zobrazí stránka **Možnosti nasazení** .

    ![Nasazení a synchronizace s GitHubem](../javascript/media/azure-deployment-options-sync.png)

    Po dokončení synchronizace se zobrazí značka zaškrtnutí.

    Web teď spouští aplikaci Node. js z úložiště GitHubu a je přístupná na adrese URL vytvořené pro Azure App Service (ve výchozím nastavení je název zadaný pro Azure App Service následovaný ". azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Úprava aplikace a nabízených změn

1. Sem přidejte kód, který se tady zobrazuje v *App. TS* po `app.use('/users', users);`řádku. Tím se přidá REST API na adrese URL */API*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Sestavte kód a otestujte ho místně a pak ho vraťte se změnami do GitHubu.

    V Azure Portal může chvíli trvat, než se detekuje změny v úložišti GitHub, a pak se spustí nová synchronizace nasazení. To vypadá podobně jako na následujícím obrázku.

    ![Upravit a synchronizovat](../javascript/media/azure-changes-detected.png)

3. Po dokončení nasazení přejděte na veřejný web a přidejte */API* k adrese URL. Vrátila se odpověď JSON.

## <a name="troubleshooting"></a>Poradce při potížích

* Pokud proces Node. exe zemře (to znamená, že dojde k neošetřené výjimce), kontejner se restartuje.
* Po spuštění kontejneru se spustí různými heuristickými metodami, které vám pomůžou zjistit, jak spustit proces Node. js. Podrobnosti o implementaci lze zobrazit v [generateStartupCommand. js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js).
* Ke spuštěnému kontejneru se můžete připojit přes SSH pro vyšetřování. To se dá snadno udělat pomocí Azure Portal. Vyberte App Service a posuňte se dolů na seznam nástrojů, dokud nedosáhnete **SSH** v části **vývojové nástroje** .
* Pokud chcete pomoci při řešení potíží, přejděte do nastavení **diagnostické protokoly** pro App Service a změňte nastavení **protokolování kontejneru Docker** z možností **vypnuto** na **systém souborů**. Protokoly se vytvoří v kontejneru pod */home/LogFiles/* _docker. log * a přístup k nim se dá v poli použít přes SSH nebo FTP.
* K lokalitě může být přiřazen vlastní název domény, nikoli adresa URL *. azurewebsites.net přiřazená ve výchozím nastavení. Další podrobnosti najdete v tématu [Mapování vlastní domény](/azure/app-service/app-service-web-tutorial-custom-domain).
* Osvědčeným postupem je nasazení do přípravného webu pro další testování. Podrobnosti o tom, jak to nakonfigurovat, najdete v tématu [vytváření](/azure/app-service/web-sites-staged-publishing)přípravných prostředí.
* Další Nejčastější dotazy najdete v tématu Nejčastější dotazy k [App Service v systému Linux](/azure/app-service/containers/app-service-linux-faq) .

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak vytvořit App Service pro Linux a nasadit aplikaci Node. js do služby. Možná budete chtít získat další informace o App Service pro Linux.

> [!div class="nextstepaction"]
> [App Service pro Linux](/azure/app-service/containers/app-service-linux-intro)
