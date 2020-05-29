---
title: Přehled nasazení | Microsoft Docs
ms.custom: seodec18
ms.date: 06/22/2018
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff5091a7ca7136cd8b62f75ee7f317b1e5b1f3be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173721"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Přehled nasazení v aplikaci Visual Studio

Nasazením aplikace, služby nebo komponenty ji budete distribuovat pro instalaci na dalších počítačích, zařízeních, serverech nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení.

Pro mnoho běžných typů aplikací můžete nasadit aplikaci přímo z Průzkumník řešení v aplikaci Visual Studio. Pro rychlou prohlídku této funkce si Projděte [první pohled na nasazení](../deployment/deploying-applications-services-and-components.md).

![Zvolit možnost publikování](../deployment/media/quickstart-publish-dialog.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jaké možnosti publikování jsou pro mě nejvhodnější?

V rámci sady Visual Studio lze aplikace publikovat přímo do následujících cílů:

- [Azure](#azure)
- [Container Registry Docker](#docker-container-registry)
- [Složka](#folder)
- [Vlastní cíle (IIS, FTP)](#Custom targets (IIS, FTP))

Na kartě **publikovat** můžete vybrat existující publikační profil, importovat stávající nebo vytvořit nový pomocí možností popsaných tady. Prohlídku možností publikování v integrovaném vývojovém prostředí pro různé typy aplikací najdete v tématu [první pohled na nasazení](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) , které vývojářům umožňují rychle vytvářet škálovatelné webové aplikace a služby bez zachování infrastruktury. App Service běží na virtuálních počítačích hostovaných v cloudu v Azure, ale tyto virtuální počítače se spravují za vás. Každé aplikaci v App Service bude přiřazená jedinečná \* Adresa URL azurewebsites.NET; všechny cenové úrovně jiné než Free umožňují přiřazení vlastních názvů domén k lokalitě.

Určíte, kolik výpočetní síly má App Service, výběrem [cenové úrovně nebo plánu](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) pro obsahující App Service. Můžete mít více webových aplikací (a jiných typů aplikací) stejné App Service bez změny cenové úrovně. Můžete například hostovat webové aplikace pro vývoj, přípravu a provoz společně na stejném App Service.

### <a name="when-to-choose-azure-app-service"></a>Kdy zvolit Azure App Service

- Chcete nasadit webovou aplikaci, která je přístupná prostřednictvím Internetu.
- Chcete automaticky škálovat webovou aplikaci podle požadavků, aniž byste museli znovu nasazovat.
- Nechcete spravovat serverovou infrastrukturu (včetně aktualizací softwaru).
- Nepotřebujete žádné vlastní nastavení na úrovni počítače na serverech, které hostují vaši webovou aplikaci.

> Pokud chcete použít Azure App Service ve vlastním datovém centru nebo jiných místních počítačích, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Další informace o publikování do App Service najdete v tématu [rychlý Start – publikování do Azure App Service](quickstart-deploy-to-azure.md) a [rychlé zprovoznění – publikování ASP.NET Core na Linux](quickstart-deploy-to-linux.md).

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Azure Virtual Machines (virtuální počítače)](https://azure.microsoft.com/documentation/services/virtual-machines/) umožňují vytvářet a spravovat libovolný počet výpočetních prostředků v cloudu. Pokud předpokládáte zodpovědnost za veškerý software a aktualizace virtuálních počítačů, můžete je přizpůsobit podle požadavků vaší aplikace. K virtuálním počítačům můžete přistupovat přímo prostřednictvím vzdálené plochy a každá z nich bude mít přiřazenou IP adresu tak dlouho, jak je potřeba.

Škálování aplikace, která je hostována na virtuálních počítačích, zahrnuje i další virtuální počítače podle požadavků a následné nasazení potřebného softwaru. Tato dodatečná úroveň řízení umožňuje škálovat odlišně v různých globálních oblastech. Pokud vaše aplikace například obsluhuje zaměstnance v celé řadě regionálních poboček, můžete škálovat virtuální počítače podle počtu zaměstnanců v těchto oblastech, což může snižovat náklady.

Další informace najdete v [podrobném porovnání](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) mezi Azure App Service, Azure Virtual Machines a dalšími službami Azure, které můžete použít jako cíl nasazení pomocí vlastní možnosti v aplikaci Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kdy zvolit Azure App Virtual Machines

- Chcete nasadit webovou aplikaci, která je přístupná přes Internet, s plnou kontrolou po dobu života přiřazených IP adres.
- Na vašich serverech potřebujete přizpůsobení na úrovni počítače, což zahrnuje další software, jako je specializovaný databázový systém, konkrétní síťové konfigurace, oddíly disku a tak dále.
- Požadujete jemnou úroveň kontroly nad škálováním webové aplikace.
- Potřebujete přímý přístup k serverům hostujícím aplikaci z jakéhokoli jiného důvodu.

> Pokud chcete používat Azure Virtual Machines ve vlastním datovém centru nebo jiných místních počítačích, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="docker-container-registry"></a>Container Registry Docker

Pokud vaše aplikace používá Docker, můžete svou aplikaci publikovat v kontejneru Container Registry Docker.

### <a name="when-to-choose-docker-container-registry"></a>Kdy zvolit Docker Container Registry

- Chcete nasadit kontejnerové aplikace

## <a name="folder"></a>Složka

Nasazení do systému souborů znamená jednoduše zkopírovat soubory aplikace do konkrétní složky ve vašem počítači. Tento postup se nejčastěji používá pro účely testování nebo pro nasazení aplikace pro použití v omezeném počtu lidí, pokud počítač používá také server. Pokud je cílová složka sdílena v síti, pak nasazení do systému souborů může zpřístupnit soubory webové aplikace ostatním uživatelům, kteří je pak mohli nasadit na konkrétní servery.

Všechny místní počítače, na kterých běží server, můžou aplikaci zpřístupnit přes Internet nebo intranet v závislosti na tom, jak je nakonfigurovaná, a sítích, ke kterým jsou připojené. (Pokud počítač připojujete přímo k Internetu, buďte obzvláště opatrní při ochraně před externími bezpečnostními hrozbami.) Vzhledem k tomu, že tyto počítače spravujete, budete mít plnou kontrolu nad tím, jak softwarové, tak hardwarové konfigurace.

Všimněte si, že pokud z nějakého důvodu (například přístup k počítači) nemůžete používat cloudové služby, jako je Azure App Service nebo Azure Virtual Machines, můžete [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) použít ve svém vlastním datovém centru. Azure Stack umožňuje spravovat a používat výpočetní prostředky prostřednictvím Azure App Service a Azure Virtual Machines, a přitom přitom udržuje vše v místním prostředí.

### <a name="when-to-choose-file-system-deployment"></a>Kdy zvolit nasazení systému souborů

- Aplikaci musíte nasadit jenom do sdílené složky, ze které ji ostatní nasadí na různé servery.
- Potřebujete pouze místní testovací nasazení.
- Chcete prošetřit a potenciálně upravit soubory aplikace nezávisle, než je odešlete do jiného cíle nasazení.

Další informace najdete v tématu [rychlý Start – nasazení do místní složky](quickstart-deploy-to-local-folder.md) .

## <a name="custom-targets-iis-ftp"></a>Vlastní cíle (IIS, FTP)

Vlastní cíl umožňuje nasazení aplikace na jiný cíl než Azure App Service, Azure Virtual Machines nebo místní systém souborů. Může se nasadit na systém souborů nebo na jiný server (Internet nebo intranet), ke kterému máte přístup, včetně těch, které jsou k dispozici v jiných cloudových službách. Může pracovat s nasazením webu (soubory nebo. ZIP) a FTP.

Při volbě vlastního cíle vás Visual Studio vyzve k zadání názvu profilu a následnému shromáždění dalších informací o **připojení** , včetně cílového serveru nebo umístění, názvu lokality a přihlašovacích údajů. Na kartě **Nastavení** můžete řídit následující chování:

- Konfigurace, kterou chcete nasadit.
- Zda odebrat existující soubory z cílového umístění.
- Určuje, zda má být během publikování předkompilována.
- Určuje, zda mají být vyloučeny soubory z App_Data složky z nasazení.

V aplikaci Visual Studio můžete vytvořit libovolný počet vlastních profilů nasazení, což umožňuje spravovat profily s různými nastaveními.

### <a name="when-to-choose-custom-deployment"></a>Kdy zvolit vlastní nasazení

- Cloudové služby používáte na jiném poskytovateli než Azure, ke kterému se dá přistup prostřednictvím adres URL.
- Chcete nasadit pomocí jiných přihlašovacích údajů, než jsou ty, které používáte v rámci sady Visual Studio, nebo které se vztahují přímo k vašim účtům Azure.
- Chcete odstranit soubory z cíle při každém nasazení.

Další informace najdete v tématu [rychlý Start – nasazení na](quickstart-deploy-to-a-web-site.md) Web.

## <a name="next-steps"></a>Další kroky

Kurzy:

- [Nasazení aplikace .NET Core pomocí nástroje Publikovat](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace ASP.NET Core do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Nasazení ve Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Nasazení aplikací pro UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace v Node. js do Azure pomocí Nasazení webu](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace v Pythonu pro Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
