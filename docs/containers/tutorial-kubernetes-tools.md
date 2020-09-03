---
title: Kurz pro nástroje Kubernetes | Microsoft Docs
ms.date: 06/08/2018
ms.topic: tutorial
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 7778019e73119a4b8b1a5842bb7a8c04ef017143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913298"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Začínáme s nástroji Visual Studio Kubernetes Tools

Nástroje Visual Studio Kubernetes vám pomůžou zjednodušit vývoj kontejnerových aplikací cílících na Kubernetes. Visual Studio může automaticky vytvořit soubory konfigurace s konfigurací, které jsou potřebné k podpoře nasazení Kubernetes, jako jsou fázemi a Helm grafy. Svůj kód můžete ladit v rámci živého clusteru Azure Kubernetes Service (AKS) pomocí Azure Dev Spaces nebo publikovat přímo do clusteru AKS z aplikace Visual Studio.

Tento kurz se zabývá používáním sady Visual Studio pro přidání podpory Kubernetes do projektu a publikování do AKS. Pokud se primárně zajímá použití [Azure dev Spaces](/azure/dev-spaces/) k ladění a testování projektu běžícího na AKS, můžete místo toho přejít na [Azure dev Spaces kurz](/azure/dev-spaces/get-started-netcore-visualstudio) .

## <a name="prerequisites"></a>Předpoklady

Abyste mohli využít tuto novou funkci, budete potřebovat:

::: moniker range="vs-2017"
- Nejnovější verzi sady [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s úlohou *vývoje ASP.NET a webu* .
- [Nástroje Kubernetes pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), které jsou k dispozici jako samostatné stažení.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s úlohou *vývoje ASP.NET a webu* .
::: moniker-end
- [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) nainstalovaný na vaší vývojové pracovní stanici (to znamená, kde spustíte Visual Studio), pokud chcete vytvořit image Docker, ladit kontejnery Docker místně spuštěné nebo publikovat na AKS. (Docker se *nevyžaduje* pro sestavování a ladění kontejnerů Docker v AKS pomocí Azure dev Spaces.)
::: moniker range="vs-2017"
- Pokud chcete publikovat na AKS ze sady Visual Studio (*není* vyžadováno pro ladění v AKS pomocí Azure dev Spaces):

    1. [Nástroje pro publikování AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), které jsou k dispozici jako samostatné stažení.

    1. Cluster služby Azure Kubernetes. Další informace najdete v tématu [Vytvoření clusteru AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Ujistěte se, že se ke [clusteru připojíte](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) z pracovní stanice pro vývoj.

    1. Helm CLI nainstalované na vaší pracovní stanici pro vývoj. Další informace najdete v tématu [instalace Helm](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md).

    1. Helm nakonfigurovanou pro cluster AKS pomocí `helm init` příkazu. Další informace o tom, jak to provést, najdete v tématu [How to Configure Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Vytvořit nový projekt Kubernetes

::: moniker range="vs-2017"

Po instalaci příslušných nástrojů spusťte aplikaci Visual Studio a vytvořte nový projekt. V části **Cloud**vyberte **aplikace kontejneru pro** typ projektu Kubernetes. Vyberte tento typ projektu a zvolte **OK**.

![Snímek obrazovky s vytvořením nového projektu aplikace Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

V okně Start sady Visual Studio vyhledejte *Kubernetes*a vyberte **aplikaci kontejneru pro Kubernetes**.

![Snímek obrazovky s vytvořením nového projektu aplikace Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Zadejte název projektu.

![Snímek obrazovky s vytvořením nového projektu aplikace Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Pak můžete zvolit typ ASP.NET Core webové aplikace, kterou chcete vytvořit. Vyberte možnost **Webová aplikace**. Možnost **Povolit podporu Docker** se v tomto dialogovém okně nezobrazuje.  Podpora Docker je ve výchozím nastavení povolená pro aplikaci typu kontejner pro Kubernetes.

::: moniker range="vs-2017"

![Snímek obrazovky s výběrem webové aplikace](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Snímek obrazovky s výběrem webové aplikace](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Přidání podpory Kubernetes do existujícího projektu

Alternativně můžete přidat podporu Kubernetes do existujícího projektu webové aplikace ASP.NET Core. Chcete-li to provést, klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **kontejner Orchestrator support**.

::: moniker range="vs-2017"

![Snímek obrazovky přidat položku nabídky Orchestrator kontejneru](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Snímek obrazovky přidat položku nabídky Orchestrator kontejneru](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

V dialogovém okně vyberte **Kubernetes/Helm** a zvolte **OK**.

![Snímek obrazovky dialogového okna Přidat kontejner Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Jakou aplikaci Visual Studio vytvoří

Po vytvoření nové **aplikace typu kontejner pro projekt Kubernetes** nebo přidání podpory Kubernetes kontejneru Orchestrator do existujícího projektu se zobrazí některé další soubory v projektu, které usnadňují nasazování do Kubernetes.

::: moniker range="vs-2017"

![Snímek obrazovky Průzkumník řešení po přidání kontejneru support Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Snímek obrazovky Průzkumník řešení po přidání kontejneru support Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Přidané soubory jsou:

- Souboru Dockerfile, který umožňuje vygenerovat image kontejneru Docker hostující tuto webovou aplikaci. Jak vidíte, nástroje sady Visual Studio tento souboru Dockerfile při ladění a nasazování do Kubernetes. Pokud preferujete pracovat přímo s imagí Docker, můžete kliknout pravým tlačítkem na souboru Dockerfile a zvolit **sestavit image Docker**.

   ![Snímek obrazovky s možností image Docker Build](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- graf Helm a složka *grafů* . Tyto soubory YAML tvoří graf Helm pro aplikaci, který můžete použít k jejímu nasazení na Kubernetes. Další informace o Helm naleznete v tématu [https://www.helm.sh](https://www.helm.sh) .

- *azds. yaml*. Obsahuje nastavení pro Azure Dev Spaces, které poskytuje rychlé a iterativní možnosti ladění ve službě Azure Kubernetes. Další informace najdete [v dokumentaci k Azure dev Spaces](/azure/dev-spaces/azure-dev-spaces).

:::moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publikování do služby Azure Kubernetes (AKS)

U všech těchto souborů můžete použít integrované vývojové prostředí (IDE) sady Visual Studio k psaní a ladění kódu aplikace, stejně jako vždy. [Azure dev Spaces](/azure/dev-spaces/) můžete použít také k rychlému spuštění a ladění kódu spuštěného v clusteru AKS v reálném čase. Další informace najdete v [kurzu Azure dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio) .

Jakmile budete mít kód spuštěný požadovaným způsobem, můžete publikovat přímo ze sady Visual Studio do clusteru AKS.

Chcete-li to provést, musíte nejprve dvakrát ověřit, zda jste nainstalovali vše, jak je popsáno v části [požadavky](#prerequisites) v položce pro publikování do AKS, a projít všechny kroky příkazového řádku, které jsou uvedeny v odkazech. Pak nastavte profil publikování, který publikuje image kontejneru na Azure Container Registry (ACR). Pak AKS může načíst image kontejneru z ACR a nasadit ji do clusteru.

1. V **Průzkumník řešení**klikněte pravým tlačítkem na *projekt* a vyberte **publikovat**.

   ![Snímek obrazovky položky nabídky publikovat](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Na obrazovce **publikovat** zvolte jako cíl publikování možnost **Container Registry** a podle pokynů vyberte registr kontejneru. Pokud ještě nemáte registr kontejneru, vyberte **vytvořit nový Azure Container Registry** a vytvořte si ho ze sady Visual Studio. Další informace najdete v tématu [publikování kontejneru do Azure Container Registry](hosting-web-apps-in-docker.md).

   ![Snímek obrazovky pro výběr cíle publikování](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Zpátky v Průzkumník řešení klikněte pravým tlačítkem na *řešení* a potom klikněte na **publikovat do Azure AKS**.

   ![Snímek obrazovky s položkou nabídky publikovat do Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Vyberte své předplatné a cluster AKS spolu s profilem publikování ACR, který jste právě vytvořili. Pak klikněte na **OK**.

   ![Snímek obrazovky publikování na AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Tím přejdete na obrazovku **publikovat do Azure AKS** .

5. Klikněte na odkaz **Konfigurovat Helm** a aktualizujte příkazový řádek použitý k instalaci grafů Helm na server.

   ![Snímek obrazovky s odkazem na konfiguraci Helm](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Aktualizace příkazového řádku je užitečná v případě, že existují vlastní argumenty příkazového řádku, které chcete zadat, jako je například jiný kontext Kubernetes nebo název grafu.

   ![Obrazovka obrazovky konfigurace Helm](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Až budete připraveni k nasazení, klikněte na tlačítko **publikovat** a publikujte svou aplikaci do AKS.

   ![Snímek obrazovky publikování na Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Blahopřejeme! Nyní můžete využívat plnou sílu sady Visual Studio pro všechny aplikace Kubernetes pro vývoj aplikací.

## <a name="remove-kubernetes-support"></a>Odebrat podporu Kubernetes

1. V **Průzkumník řešení**v části **vlastnosti**otevřete *launchSettings.jsna*.

1. Odstraňte kontejner oddílu **v Kubernetes**.

1. Pokud přecházíte do sestavení Docker, vyberte tento projekt v **Průzkumník řešení**, klikněte pravým tlačítkem a zvolte **nastavit jako projekt po spuštění**.

1. Volitelné Můžete také odstranit další artefakty uvedené výše v článku, například složku **grafy** a *azds. yaml*.

## <a name="next-steps"></a>Další kroky

Další informace o vývoji Kubernetes v Azure najdete v [dokumentaci k AKS](/azure/aks).

Další informace o Azure Dev Spaces najdete v [dokumentaci k Azure dev Spaces](/azure/dev-spaces/)
