---
title: Kubernetes nástroje výukový program | Dokumenty společnosti Microsoft
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 931f8c2a6d3be130ef78f59f9b3853d28fad8cd4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444684"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Začínáme s nástroji Visual Studio Kubernetes Tools

Nástroje Visual Studio Kubernetes pomáhají zefektivnit vývoj kontejnerizovaných aplikací zaměřených na Kubernetes. Visual Studio můžete automaticky vytvořit konfigurační soubory jako kód potřebné pro podporu nasazení Kubernetes, jako jsou dockerfiles a Helm grafy. Kód můžete ladit v živém clusteru služby Azure Kubernetes Service (AKS) pomocí Azure Dev Spaces nebo publikovat přímo do clusteru AKS z vnitřního visual studia.

Tento kurz popisuje použití sady Visual Studio přidat podporu Kubernetes do projektu a publikovat do AKS. Pokud máte primárně zájem o použití [Azure Dev Spaces](/azure/dev-spaces/) k ladění a testování projektu spuštěného v AKS, můžete místo toho přejít na [kurz Azure Dev Spaces.](/azure/dev-spaces/get-started-netcore-visualstudio)

## <a name="prerequisites"></a>Požadavky

Chcete-li tuto novou funkci využít, budete potřebovat:

::: moniker range="vs-2017"
- Nejnovější verze [Visual Studia 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) s *ASP.NET a zatížení mno žadou webových* aplikací.
- [Nástroje Kubernetes pro Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), které jsou k dispozici jako samostatné stažení.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) s *ASP.NET a zatížení mno žahou webu.*
::: moniker-end
- [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) nainstalovaný na vývojové pracovní stanici (to znamená, kde spustíte Visual Studio), pokud chcete vytvářet inamhnout Docker, ladit kontejnery Dockeru spuštěné místně nebo publikovat do AKS. (Docker se *nevyžaduje* pro vytváření a ladění kontejnerů Dockeru v AKS pomocí Azure Dev Spaces.)
::: moniker range="vs-2017"
- Pokud chcete publikovat do AKS z Visual Studia *(není* vyžadováno pro ladění v AKS pomocí Azure Dev Spaces):

    1. Nástroje [pro publikování AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), které jsou k dispozici jako samostatné stažení.

    1. Cluster služby Azure Kubernetes. Další informace naleznete [v tématu Vytvoření clusteru AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Ujistěte se, že [se připojíte ke clusteru](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) z vývojové pracovní stanice.

    1. Helm CLI nainstalován na vývojové pracovní stanici. Další informace naleznete [v tématu Instalace helmu](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md).

    1. Helm nakonfigurován proti clusteru AKS pomocí příkazu. `helm init` Další informace o tom, jak to provést, naleznete v [tématu Konfigurace helmu](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Vytvoření nového projektu Kubernetes

::: moniker range="vs-2017"

Jakmile budete mít nainstalované příslušné nástroje, spusťte Visual Studio a vytvořte nový projekt. V **části Cloud**zvolte typ projektu Kontejner pro **Kubernetes.** Vyberte tento typ projektu a zvolte **OK**.

![Snímek obrazovky s vytvořením nového projektu aplikace Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

V počátečním okně sady Visual Studio vyhledejte *Kubernetes*a zvolte **aplikaci kontejneru pro Kubernetes**.

![Snímek obrazovky s vytvořením nového projektu aplikace Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Zadejte název projektu.

![Snímek obrazovky s vytvořením nového projektu aplikace Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Potom můžete zvolit, jaký typ ASP.NET webové aplikace Core vytvořit. Zvolte **Webová aplikace**. Obvyklá možnost **Povolit podporu Dockeru** se v tomto dialogovém okně nezobrazí.  Podpora Dockeru je ve výchozím nastavení povolena pro kontejnerovou aplikaci pro Kubernetes.

::: moniker range="vs-2017"

![Snímek obrazovky s výběrem webové aplikace](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Snímek obrazovky s výběrem webové aplikace](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Přidání podpory Kubernetes do existujícího projektu

Případně můžete přidat podporu Kubernetes do existujícího projektu webové aplikace ASP.NET Core. Chcete-li to provést, klepněte pravým tlačítkem myši na projekt a zvolte **Přidat** > **podporu orchestratoru kontejneru**.

::: moniker range="vs-2017"

![Snímek obrazovky s položkou nabídky Přidat orchestrátor kontejneru](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Snímek obrazovky s položkou nabídky Přidat orchestrátor kontejneru](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

V dialogovém okně vyberte **Kubernetes/Helm** a zvolte **OK**.

![Snímek obrazovky s dialogovým oknem Přidat orchestrátor kontejneru](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Co pro vás Visual Studio vytvoří

Po vytvoření nové aplikace kontejneru pro projekt **Kubernetes** nebo přidání podpory orchestrátoru kontejneru Kubernetes do existujícího projektu se v projektu zobrazí některé další soubory, které usnadňují nasazení do Kubernetes.

::: moniker range="vs-2017"

![Snímek obrazovky Průzkumníka řešení po přidání podpory orchestratoru kontejnerů](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Snímek obrazovky Průzkumníka řešení po přidání podpory orchestratoru kontejnerů](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Přidané soubory jsou:

- soubor Dockerfile, který umožňuje generovat image kontejneru Dockeru hostující tuto webovou aplikaci. Jak uvidíte, nástroje Visual Studio využívá tento dockerfile při ladění a nasazování do Kubernetes. Pokud dáváte přednost práci přímo s image Dockeru, můžete kliknout pravým tlačítkem myši na dockerfile a zvolit **Build Docker Image**.

   ![Snímek obrazovky s možností Image Dockeru sestavení](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- graf helmu a složku *grafů.* Tyto yaml soubory tvoří helmgraf pro aplikaci, kterou můžete použít k nasazení do Kubernetes. Další informace o helmu naleznete v tématu [https://www.helm.sh](https://www.helm.sh).

- *azds.yaml*. To obsahuje nastavení pro Azure Dev Spaces, který poskytuje rychlé, iterativní ladění prostředí ve službě Azure Kubernetes. Další informace naleznete [v dokumentaci k Azure Dev Spaces](/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publikovat do služby Azure Kubernetes (AKS)

Se všemi těmito soubory na místě, můžete použít IDE Sady Visual Studio k zápisu a ladění kódu aplikace, stejně jako vždy. [Azure Dev Spaces](/azure/dev-spaces/) můžete také použít k rychlému spuštění a ladění kódu spuštěného živě v clusteru AKS. Další informace najdete v kurzu [Azure Dev Spaces.](/azure/dev-spaces/get-started-netcore-visualstudio)

Jakmile budete mít kód běží tak, jak chcete, můžete publikovat přímo z Visual Studio do clusteru AKS.

Chcete-li to provést, musíte nejprve zkontrolovat, zda jste nainstalovali vše, co je popsáno v části Požadavky v části [Požadavky](#prerequisites) pro publikování do AKS, a projít všechny kroky příkazového řádku uvedené v odkazech. Potom nastavte profil publikování, který publikuje image kontejneru do registru kontejnerů Azure (ACR). Pak AKS můžete vytáhnout image kontejneru z ACR a nasadit do clusteru.

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na *projekt* a zvolte **Publikovat**.

   ![Snímek obrazovky s položkou nabídky Publikovat](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Na obrazovce **Publikovat** zvolte **registr kontejnerů** jako cíl publikování a podle pokynů vyberte registr kontejnerů. Pokud ještě nemáte registr kontejnerů, zvolte **Vytvořit nový registr kontejnerů Azure** a vytvořte ho z Visual Studia. Další informace najdete [v tématu Publikování kontejneru do registru kontejnerů Azure](hosting-web-apps-in-docker.md).

   ![Snímek obrazovky Vybrat cílovou obrazovku publikování](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. V Průzkumníku řešení klikněte pravým tlačítkem myši na *vaše řešení* a klikněte na Publikovat do **Azure AKS**.

   ![Snímek obrazovky s položkou nabídky Publikovat do Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Zvolte předplatné a cluster AKS spolu s profilem publikování ACR, který jste právě vytvořili. Pak klikněte na **OK**.

   ![Snímek obrazovky Publikovat na AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Tím přejdete na obrazovku **Publikovat do Azure AKS.**

5. Zvolte odkaz **Konfigurovat helmu** a aktualizujte příkazový řádek použitý k instalaci grafů helmu na server.

   ![Snímek obrazovky s odkazem Konfigurovat helmu](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Aktualizace příkazového řádku je užitečná, pokud chcete zadat vlastní argumenty příkazového řádku, například jiný kontext Kubernetes nebo název grafu.

   ![Snímek obrazovky konfigurace helmy](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Až budete připraveni k nasazení, klikněte na tlačítko **Publikovat** publikovat aplikaci do AKS.

   ![Snímek obrazovky publikování na obrazovce Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Blahopřejeme! Teď můžete použít plný výkon Visual Studia pro veškerý vývoj aplikací Kubernetes.

## <a name="next-steps"></a>Další kroky

Další informace o vývoji Kubernetes v Azure najdete v [dokumentaci AKS](/azure/aks).

Další informace o Azure Dev Spaces najdete v [dokumentaci k Azure Dev Spaces](/azure/dev-spaces/)
