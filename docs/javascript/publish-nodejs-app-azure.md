---
title: Publikování aplikace v Node.js do služby App Service pro Linux
description: Můžete publikovat aplikace Node.js, které jsou vytvořené v sadě Visual Studio do služby App Service pro Linux v Azure
ms.custom: ''
ms.date: 11/1/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8af99919fe80f1f5e2776e381d24aa8d37bad36d
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750764"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publikování aplikace v Node.js do Azure (App Linux Service)

Tento kurz vás provede úlohu vytvoření jednoduché aplikace Node.js a publikujete ji do Azure.

Při publikování aplikace v Node.js do Azure, máte několik možností. Mezi ně patří služby Azure App Service, virtuální počítač spuštěn operační systém podle vašeho výběru, Azure Container Service (AKS) pro správu pomocí Kubernetes, Instance kontejneru pomocí Dockeru a další. Další podrobnosti o každé z těchto možností najdete v tématu [Compute](https://azure.microsoft.com/product-categories/compute/).

Pro účely tohoto kurzu, můžete aplikaci nasadit do [služby App Service pro Linux](/azure/app-service/containers/app-service-linux-intro).
Služby App Service pro Linux nasadí kontejner Dockeru pro Linux a spusťte aplikaci Node.js (na rozdíl od App Service Windows, který se spouští aplikace Node.js za služby IIS na Windows).

Tento kurz ukazuje, jak vytvořit aplikaci v Node.js od ze šablony s Node.js Tools for Visual Studio nainstalovaný, vloží kód do úložiště na Githubu a pak zřízení služby Azure App Service prostřednictvím portálu pro Azure web tak, aby můžete aplikaci nasadit z Úložiště GitHub. Pomocí příkazového řádku můžete zřídit službu Azure App Service a kódu z místního úložiště Git, naleznete v tématu [vytvoření aplikace Node.js](/azure/app-service/containers/quickstart-nodejs).

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvořit projekt Node.js
> * Vytvořit úložiště GitHub pro kód
> * Vytvoření služby App Service Linuxu v Azure
> * Nasazení do systému Linux

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Vytvoření projektu Node.js ke spuštění v Azure

1. Vytvořit nové TypeScript Express aplikace s použitím **souboru** > **nový projekt** dialogové okno.

1. V části **TypeScript** uzlu, vyberte **aplikaci základní Node.js Express 4**.

    ![Vytvoření nové aplikace TypeScript Express](../javascript/media/azure-ts-express-app.png)

1. Klikněte na tlačítko **OK** pro vytvoření projektu v sadě Visual Studio.

1. Stisknutím klávesy **F5** k vytvoření a spuštění aplikace a ujistěte se, že všechno běží podle očekávání.

1. Vyberte **souboru** > **přidat do správy zdrojových kódů** k vytvoření místního úložiště Git pro projekt.

    V tomto okamžiku Node.js app using architekturu Express a napsaných v TypeScript funguje a vráceny se změnami do místní správy zdrojového kódu.

1. Upravte projekt podle potřeby před pokračováním na další kroky.

## <a name="push-code-from-visual-studio-to-github"></a>Předejte kód ze sady Visual Studio do Githubu

Chcete-li nastavte GitHub pro Visual Studio:

1. Ujistěte se, [rozšíření GitHub pro Visual Studio](https://visualstudio.github.com/) je nainstalovaný a povolený pomocí položky nabídky **nástroje** > **rozšíření a aktualizace**.

2. Z nabídky vyberte **zobrazení** > **ostatní Windows** > **Githubu**.

    Otevře se okno Githubu.

3. Pokud se nezobrazí **Začínáme** tlačítka v okně s Githubem, klikněte na tlačítko **souboru** > **přidat do správy zdrojových kódů** a počkat na aktualizaci uživatelského rozhraní.

    ![Otevřete okno Githubu](../javascript/media/azure-github-get-started.png)

4. Klikněte na tlačítko **Začínáme**.

    Pokud již jste připojeni ke Githubu, zobrazí se podobně jako na následujícím obrázku panelu nástrojů.

    ![Nastavení úložiště GitHub](../javascript/media/azure-github-publish.png)

5. Vyplňte pole k novému úložišti publikovat, a potom klikněte na **publikovat**.

    Po chvíli zobrazí se banner s oznámením "Úspěšně vytvořil úložiště".

    V další části se dozvíte, jak publikovat z tohoto úložiště do služby Azure App Service v Linuxu.

## <a name="create-a-linux-app-service-in-azure"></a>Vytvořit službu App Service Linuxu v Azure

1. Přihlaste se k [webu Azure portal](https://portal.azure.com).

2. Vyberte **App Services** ze seznamu služeb na levé straně a potom klikněte na tlačítko **přidat**.

3. V případě potřeby vytvořte novou skupinu prostředků a App Service plán pro hostování nové aplikace.

4. Nezapomeňte nastavit **OS** k **Linux**a nastavte **zásobník modulu Runtime** na požadovanou verzi Node.js, jak je znázorněno na obrázku.

    ![Vytvořit službu App Service Linuxu](../javascript/media/azure-create-appservice-annotated.png)

5. Klikněte na tlačítko **vytvořit** k vytvoření služby App Service.

    Může trvat několik minut, než nasazení.

6. Po nasazení, přejděte **nastavení aplikace** části a přidejte nastavení s názvem `SCM_SCRIPT_GENERATOR_ARGS` a hodnotu `--node`.

    ![Nastavení aplikace](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Proces nasazení služby App Service používá sadu heuristik k určení typu aplikace a zkuste spustit. Pokud. *sln* v nasazeným obsahem je detekován soubor, bude předpokládat, projekt MSBuild na základě se nasazuje. Nastavení přidané v předchozím kroku potlačuje tuto logiku a explicitně určuje, že se jedná o aplikaci v Node.js. Bez tohoto nastavení se nepodaří nasadit, když aplikace Node.js. *sln* soubor je součástí úložiště se nasazuje do služby App Service.

7. Po nasazení, otevřete App Service a vyberte **možnosti nasazení**.

    ![Možnosti nasazení](../javascript/media/azure-deployment-options.png)

8. Klikněte na tlačítko **zvolit zdroj**a klikněte na tlačítko **Githubu**a potom nakonfigurujte všechna požadovaná oprávnění.

    ![Oprávnění v Githubu](../javascript/media/azure-choose-source.png)

9. Vyberte úložiště a větve k publikování a pak vyberte **OK**.

    ![Publikování do App Service pro Linux](../javascript/media/azure-repo-and-branch.png)

    **Možnosti nasazení** během synchronizace se zobrazí stránka.

    ![Nasazení a synchronizuje s Githubem](../javascript/media/azure-deployment-options-sync.png)

    Po dokončení synchronizace, se zobrazí zaškrtávací políčko.

    Web je teď spuštěná aplikace Node.js z úložiště Githubu a je přístupný na adrese URL vytvořené pro službu Azure App Service (ve výchozím nastavení následuje název použitý pro službu Azure App Service ". azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Upravit aplikaci a nabízených oznámení změny

1. Přidejte kód zobrazený zde v *app.ts* po řádku `app.use('/users', users);`. Tento postup přidá rozhraní REST API na adrese URL */webové rozhraní API*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Sestavení kódu a testování místně, pak vrácení se změnami a push do Githubu.

    Na webu Azure Portal trvá několik okamžiků zjišťovat změny v úložišti na Githubu a poté spustí novou synchronizaci nasazení. Ten vypadá podobně jako na následujícím obrázku.

    ![Upravit a synchronizovat](../javascript/media/azure-changes-detected.png)

3. Po dokončení nasazení přejděte na veřejný web a připojit */webové rozhraní API* na adresu URL. Získá vrátí odpověď JSON.

## <a name="troubleshooting"></a>Poradce při potížích

* Pokud je node.exe zpracování zemře (to znamená, že dojde k neošetřené výjimce), se restartuje kontejner.
* Při spuštění kontejneru spustí prostřednictvím různých heuristiky zjistit, jak spustit proces Node.js. Podrobnosti implementace, můžete zobrazit v [generateStartupCommand.js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js).
* Můžete připojit ke spuštěnému kontejneru pomocí protokolu SSH pro šetření. To se snadno provádí pomocí webu Azure Portal. Vyberte službu App Service a přejděte dolů v seznamu nástrojů, dokud nebude dosaženo **SSH** pod **nástroje pro vývoj** oddílu.
* Pokud chcete pomoci při řešení potíží, přejděte na **diagnostické protokoly** nastavení pro službu App Service a změnit **protokolování kontejneru Dockeru** nastavení z **vypnout** k  **Systém souborů**. Protokoly se vytvoří v kontejneru v rámci */home/LogFiles/*_docker.log* a je přístupný na pole pomocí SSH nebo FTP (S).
* Název vlastní domény může být přiřazen k lokalitě, místo *. azurewebsites.net URL přiřazené ve výchozím nastavení. Další podrobnosti najdete v tématu [mapování vlastní domény](/azure/app-service/app-service-web-tutorial-custom-domain).
* Nasazení do přípravného lokalitě k dalšímu testování před přesunutím do produkčního prostředí je osvědčeným postupem. Podrobnosti o tom, jak nastavit tuto konfiguraci najdete v tématu [vytvoření přípravných prostředí](/azure/app-service/web-sites-staged-publishing).
* Zobrazit [služby App Service v Linuxu – nejčastější dotazy](/azure/app-service/containers/app-service-linux-faq) pro další často kladené dotazy.

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak vytvořit službu App Service Linuxu a nasazení aplikace Node.js ve službě. Můžete získat další informace o službě App Service pro Linux.

> [!div class="nextstepaction"]
> [Služby App Service pro Linux](/azure/app-service/containers/app-service-linux-intro)
