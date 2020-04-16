---
title: Publikování aplikace v Node.js do služby App Service v Linuxu
description: Aplikace Node.js vytvořené v sadě Visual Studio do linuxové služby App Service můžete publikovat v Azure.
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
ms.openlocfilehash: d75bb4f5274201b7cf745ff8c7c6f27b869855c3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445009"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publikování aplikace Node.js do Azure (Linux App Service)

Tento kurz vás provede úkolem vytvořit jednoduchou aplikaci Node.js a publikovat ji do Azure.

Při publikování aplikace Node.js do Azure existuje několik možností. Patří mezi ně Azure App Service, virtuální počítač se spuštěným os podle vašeho výběru, Služba Azure Container Service (AKS) pro správu s Kubernetes, instance kontejneru pomocí Dockeru a další. Další podrobnosti o každé z těchto možností naleznete v [tématu Compute](https://azure.microsoft.com/product-categories/compute/).

V tomto kurzu nasadíte aplikaci do [linuxové služby App Service](/azure/app-service/containers/app-service-linux-intro).
Linux App Service nasazuje linuxový docker kontejner ke spuštění aplikace Node.js (na rozdíl od služby Windows App Service, která spouští aplikace Node.js za službou IIS ve Windows).

Tento kurz ukazuje, jak vytvořit aplikaci Node.js počínaje šablonou nainstalovanou pomocí nástrojů Node.js pro Visual Studio, přesunut kód do úložiště na GitHubu a pak zřídit službu Azure App Service prostřednictvím webového portálu Azure, abyste mohli nasadit z úložiště GitHuby. Pokud chcete pomocí příkazového řádku zřídit službu Azure App Service a vysunout kód z místního úložiště Git, přečtěte si viz [Vytvoření aplikace Node.js](/azure/app-service/containers/quickstart-nodejs).

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvoření projektu Node.js
> * Vytvoření úložiště GitHub pro kód
> * Vytvoření linuxové služby aplikací v Azure
> * Nasazení do Linuxu

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou visual studio a úlohu vývoje Node.js.

    ::: moniker range=">=vs-2019"
    Pokud jste visual studio 2019 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste visual studio 2017 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...**, který otevře Instalační program sady Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úloha node.js v Instalačníslužbě VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud se nainstalovaný modul runtime nerozpozná, můžete projekt nakonfigurovat na stránce vlastností pomocí odkazu na nainstalovaný modul runtime (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu a zvolte **Vlastnosti**).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Vytvoření projektu Node.js, který se bude spouštět v Azure

1. Otevřete sadu Visual Studio.

1. Vytvořte novou aplikaci TypeScript Express.

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** otevřete vyhledávací pole, zadejte **Node.js**a pak zvolte **Vytvořit novou základní aplikaci Azure Node.js Express 4** (TypeScript). V zobrazeném dialogovém okně zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** rozbalte **položku TypeScript**a zvolte **Node.js**. V prostředním podokně zvolte **Základní aplikace Azure Node.js Express 4**a pak zvolte **OK**.

    ![Vytvoření nové aplikace TypeScript Express](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Pokud nevidíte šablonu **projektu aplikace Basic Node.js Express 4,** musíte přidat vývojové **úlohy Node.js.** Podrobné pokyny naleznete v tématu [Požadavky](#prerequisites).

    Visual Studio vytvoří projekt a otevře jej v Průzkumníku řešení (pravé podokno).

1. Stisknutím **klávesy F5** vytvořte a spusťte aplikaci a ujistěte se, že vše běží podle očekávání.

1. Vyberte **Přidat soubor** > **do správy zdrojového kódu** a vytvořte místní úložiště Git pro projekt.

    V tomto okamžiku aplikace Node.js pomocí express frameworku a napsané v TypeScriptu funguje a vrácena se změnami do místního řízení zdrojového kódu.

1. Před pokračováním v dalších krocích upravte projekt podle potřeby.

## <a name="push-code-from-visual-studio-to-github"></a>Nabízený kód z Visual Studia na GitHub

Nastavení GitHubu pro Visual Studio:

1. Ujistěte se, že [rozšíření GitHub pro Visual Studio](https://visualstudio.github.com/) je nainstalována a povolena pomocí**položky**nabídky **Nástroje** > rozšíření a aktualizace .

2. V nabídce vyberte **Zobrazit** > **jiný Windows** > **GitHub**.

    Otevře se okno GitHub.

3. Pokud v okně GitHub unevidíte tlačítko **Začínáme,** klikněte na **Přidat soubor** > **do správy zdrojového kódu** a počkejte, až se aktualizuje ui.

    ![Otevření okna GitHubu](../javascript/media/azure-github-get-started.png)

4. Klikněte na **Začínáme**.

    Pokud jste již připojeni k GitHubu, panel nástrojů se zobrazí podobně jako na následujícím obrázku.

    ![Nastavení úložiště GitHub](../javascript/media/azure-github-publish.png)

5. Vyplňte pole pro publikování nového úložiště a klepněte na tlačítko **Publikovat**.

    Po několika okamžicích se zobrazí banner s nápisem "Úložiště bylo úspěšně vytvořeno".

    V další části se dozvíte, jak publikovat z tohoto úložiště do služby Azure App Service na Linuxu.

## <a name="create-a-linux-app-service-in-azure"></a>Vytvoření linuxové služby aplikací v Azure

1. Přihlaste se k webu [Azure Portal](https://portal.azure.com).

2. Ze seznamu služeb vlevo vyberte **Služby aplikací** a klikněte na **Přidat**.

3. V případě potřeby vytvořte nový plán skupiny prostředků a služby App Service pro hostování nové aplikace.

4. Ujistěte se, že nastavení **operačního systému** na **Linux**a **runtime stack** na požadovanou verzi Node.js, jak je znázorněno na obrázku.

    ![Vytvoření linuxové služby aplikací](../javascript/media/azure-create-appservice-annotated.png)

5. Kliknutím na **Vytvořit** vytvořte službu App Service.

    Nasazení může trvat několik minut.

6. Po nasazení přejděte do části **Nastavení aplikace** a přidejte nastavení `SCM_SCRIPT_GENERATOR_ARGS` s názvem `--node`a hodnotou .

    ![Nastavení aplikace](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Proces nasazení služby App Service používá sadu heuristik k určení, který typ aplikace se má pokusit spustit. Pokud . *sln* soubor je zjištěn v nasazeném obsahu, bude předpokládat, msbuild založený projekt je nasazen. Výše přidané nastavení tuto logiku přepíše a explicitně určuje, že se jedná o aplikaci Node.js. Bez tohoto nastavení se aplikaci Node.js nepodaří nasadit, pokud je soubor . *sln* soubor je součástí úložiště, které se nasazuje do služby App Service.

7. V části **Nastavení aplikace**přidejte `WEBSITE_NODE_DEFAULT_VERSION` další nastavení `8.9.0`s názvem a hodnotou .

8. Po nasazení otevřete službu App Service a vyberte **možnosti nasazení**.

    ![Možnosti nasazení](../javascript/media/azure-deployment-options.png)

9. Klikněte na **Vybrat zdroj**a pak zvolte **GitHub**a nakonfigurujte všechna požadovaná oprávnění.

    ![Oprávnění GitHubu](../javascript/media/azure-choose-source.png)

10. Vyberte úložiště a větev, které chcete publikovat, a pak vyberte **OK**.

    ![Publikování do App Service pro Linux](../javascript/media/azure-repo-and-branch.png)

    Při synchronizaci se zobrazí stránka **možností nasazení.**

    ![Nasazení a synchronizace s GitHubem](../javascript/media/azure-deployment-options-sync.png)

    Po dokončení synchronizace se zobrazí zaškrtnutí.

    Na webu je teď spuštěna aplikace Node.js z úložiště GitHub a je přístupná na adrese URL vytvořené pro službu Azure App Service (ve výchozím nastavení název pro službu Azure App Service následovaný ".azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Úprava aplikace a nabízená změna

1. Přidejte kód zde zobrazený v *app.ts* za řádek `app.use('/users', users);`. Tím přidáte rozhraní REST API na adresu URL */API*.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Sestavte kód a otestujte ho místně, pak ho zkontrolujte a převezte na GitHub.

    Na webu Azure Portal trvá několik okamžiků, než zjistíte změny v úložišti GitHub a pak se spustí nová synchronizace nasazení. Vypadá podobně jako na následujícím obrázku.

    ![Úprava a synchronizace](../javascript/media/azure-changes-detected.png)

3. Po dokončení nasazení přejděte na veřejný web a připojte */api* k adrese URL. Získá vrácena odpověď JSON.

## <a name="troubleshooting"></a>Řešení potíží

* Pokud proces node.exe zemře (to znamená, že dojde k neošetřené výjimce), kontejner se restartuje.
* Při spuštění kontejneru, prochází různými heuristiky zjistit, jak spustit proces Node.js. Podrobnosti o implementaci lze zobrazit na [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js).
* Můžete se připojit k běžící kontejner přes SSH pro vyšetřování. To se dá snadno provést pomocí portálu Azure. Vyberte službu App Service a posuňte se dolů v seznamu nástrojů, dokud nedosáhnete **SSH** v části **Vývojové nástroje.**
* Chcete-li pomoci při řešení potíží, přejděte na nastavení **protokolů diagnostiky** pro službu App Service a změňte nastavení **protokolování kontejneru Dockeru** z **vypnuto** na **systém souborů**. Protokoly jsou vytvořeny v kontejneru pod */home/LogFiles/*_docker.log*, a lze přistupovat na poli pomocí SSH nebo FTP(S).
* Webu může být přiřazen vlastní název domény, nikoli adresa URL *.azurewebsites.net přiřazená ve výchozím nastavení. Další podrobnosti naleznete v tématu [Mapovat vlastní doménu](/azure/app-service/app-service-web-tutorial-custom-domain).
* Nasazení do pracovní lokality pro další testování před přechodem do produkčního prostředí je osvědčeným postupem. Podrobnosti o tom, jak tuto konfiguraci nakonfigurovat, naleznete v tématu [Vytvoření pracovních prostředí](/azure/app-service/web-sites-staged-publishing).
* Další nejčastější dotazy najdete v nejčastějších dotazech [v tématu App Service on Linux.](/azure/app-service/containers/app-service-linux-faq)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se dozvěděli, jak vytvořit linuxovou službu app service a nasadit aplikaci Node.js do služby. Můžete se dozvědět více o linuxové app service.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
