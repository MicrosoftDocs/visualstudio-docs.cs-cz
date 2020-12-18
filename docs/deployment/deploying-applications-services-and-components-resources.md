---
title: Nasazení aplikace sady Visual Studio do složky, služby IIS, Azure nebo jiného cíle
titleSuffix: ''
description: Přečtěte si další informace o možnostech publikování aplikace pomocí nástroje Publikovat.
ms.custom:
- SEO-VS-2020
- contperf-fy21q1
ms.date: 08/21/2020
ms.topic: troubleshooting
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
ms.openlocfilehash: 86a771b1eae096227a46378c8146e6aa5d9e2a06
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683922"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Nasazení aplikace do složky, služby IIS, Azure nebo jiného cíle

Nasazením aplikace, služby nebo komponenty ji budete distribuovat pro instalaci na dalších počítačích, zařízeních, serverech nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení.

Získejte nápovědu pro úlohu nasazení:

- Nejste si jisti, jakou možnost nasazení zvolit? Podívejte [se, jaké možnosti publikování jsou pro mě nejvhodnější?](#what-publishing-options-are-right-for-me)
- Nápovědu k potížím s nasazením Azure App Service nebo IIS najdete v tématu věnovaném [řešení potíží ASP.NET Core na Azure App Service a IIS](/aspnet/core/test/troubleshoot-azure-iis).
- Nápovědu ke konfiguraci nastavení nasazení rozhraní .NET najdete v tématu [Konfigurace nastavení nasazení rozhraní .NET](#configure-net-deployment-settings).
- Pokud chcete nasadit nový cíl, pokud jste předtím vytvořili profil publikování, vyberte v okně **publikovat** pro nakonfigurovaný profil **Nový** .

   ![Vytvořit nový profil publikování](../deployment/media/create-a-new-publish-profile.png)

   Pak zvolte možnost nasazení v okně Publikovat. Informace o možnostech publikování najdete v následujících oddílech.

## <a name="what-publishing-options-are-right-for-me"></a>Jaké možnosti publikování jsou pro mě nejvhodnější?

V rámci sady Visual Studio lze aplikace publikovat přímo do následujících cílů:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Container Registry Docker](#docker-container-registry)
- [Složka](#folder)
- [Server FTP/FTPS](#ftpftps-server)
- [Webový server (IIS)](#web-server-iis)
- [Importovat profil](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [App Service](#azure-app-service)
- [App Service Linux](#azure-app-service)
- [IIS (výběr služby IIS, FTP atd.)](#web-server-iis)
- [FTP/FTPS (výběr služby IIS, FTP atd.)](#ftpftps-server)
- [Složka](#folder)
- [Importovat profil](#import-profile)
::: moniker-end

Předchozí možnosti se zobrazí, jak je znázorněno na následujícím obrázku při vytváření nového profilu publikování.

::: moniker range=">=vs-2019"
![Zvolit možnost publikování](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Zvolit možnost publikování](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Rychlou prohlídku obecnější možností nasazení aplikací najdete v tématu [první pohled na nasazení](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

Když zvolíte Azure, můžete si vybrat mezi:

- [Azure App Service](#azure-app-service) spuštěný v systému Windows, Linux nebo jako image Docker
- Image Docker nasazená do [Azure Container Registry](#azure-container-registry)
- [Virtuální počítač Azure](#azure-virtual-machine)

![Zvolit službu Azure](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) pomáhá vývojářům rychle vytvářet škálovatelné webové aplikace a služby bez zachování infrastruktury. App Service běží na virtuálních počítačích hostovaných v cloudu v Azure, ale tyto virtuální počítače se spravují za vás. Každé aplikaci v App Service bude přiřazená jedinečná \* Adresa URL azurewebsites.NET; všechny cenové úrovně jiné než Free umožňují přiřazení vlastních názvů domén k lokalitě.

Určíte, kolik výpočetní síly má App Service, výběrem [cenové úrovně nebo plánu](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) pro obsahující App Service. Můžete mít více webových aplikací (a jiných typů aplikací) stejné App Service bez změny cenové úrovně. Můžete například hostovat webové aplikace pro vývoj, přípravu a provoz společně na stejném App Service.

#### <a name="when-to-choose-azure-app-service"></a>Kdy zvolit Azure App Service

- Chcete nasadit webovou aplikaci, která je přístupná prostřednictvím Internetu.
- Chcete automaticky škálovat webovou aplikaci podle požadavků, aniž byste museli znovu nasazovat.
- Nechcete spravovat serverovou infrastrukturu (včetně aktualizací softwaru).
- Nepotřebujete žádné vlastní nastavení na úrovni počítače na serverech, které hostují vaši webovou aplikaci.

> Pokud chcete použít Azure App Service ve vlastním datovém centru nebo jiných místních počítačích, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Další informace o publikování do App Service najdete v tématech:
- [Rychlý Start – publikování do Azure App Service](quickstart-deploy-to-azure.md)
- [Rychlý Start – publikování ASP.NET Core do systému Linux](quickstart-deploy-to-linux.md).
- [Publikování aplikace ASP.NET Core pro Azure App Service](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Řešení potíží s ASP.NET Core v Azure App Service a IIS](/aspnet/core/test/troubleshoot-azure-iis).

### <a name="azure-container-registry"></a>Azure Container Registry

[Azure Container Registry](/azure/container-registry/) umožňuje sestavovat, ukládat a spravovat image kontejnerů Docker a artefakty v privátním registru pro všechny typy kontejnerových nasazení.

#### <a name="when-to-choose-azure-container-registry"></a>Kdy zvolit Azure Container Registry

- Pokud máte existující kanál pro vývoj a nasazení kontejnerů Docker.
- Když chcete vytvořit image kontejneru Docker v Azure.

Další informace najdete tady:

- [Nasazení kontejneru ASP.NET do registru kontejneru](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Virtuální počítač Azure

[Azure Virtual Machines (virtuální počítače)](https://azure.microsoft.com/documentation/services/virtual-machines/) umožňují vytvářet a spravovat libovolný počet výpočetních prostředků v cloudu. Pokud předpokládáte zodpovědnost za veškerý software a aktualizace virtuálních počítačů, můžete je přizpůsobit podle požadavků vaší aplikace. K virtuálním počítačům můžete přistupovat přímo prostřednictvím vzdálené plochy a každá z nich bude mít přiřazenou IP adresu tak dlouho, jak je potřeba.

Škálování aplikace, která je hostována na virtuálních počítačích, zahrnuje i další virtuální počítače podle požadavků a následné nasazení potřebného softwaru. Tato dodatečná úroveň řízení umožňuje škálovat odlišně v různých globálních oblastech. Pokud vaše aplikace například obsluhuje zaměstnance v celé řadě regionálních poboček, můžete škálovat virtuální počítače podle počtu zaměstnanců v těchto oblastech, což může snižovat náklady.

Další informace najdete v [podrobném porovnání](/azure/architecture/guide/technology-choices/compute-decision-tree) mezi Azure App Service, Azure Virtual Machines a dalšími službami Azure, které můžete použít jako cíl nasazení pomocí vlastní možnosti v aplikaci Visual Studio.

#### <a name="when-to-choose-azure-virtual-machines"></a>Kdy zvolit Azure Virtual Machines

- Chcete nasadit webovou aplikaci, která je přístupná přes Internet, s plnou kontrolou po dobu života přiřazených IP adres.
- Na vašich serverech potřebujete přizpůsobení na úrovni počítače, což zahrnuje další software, jako je specializovaný databázový systém, konkrétní síťové konfigurace, oddíly disku a tak dále.
- Požadujete jemnou úroveň kontroly nad škálováním webové aplikace.
- Potřebujete přímý přístup k serverům hostujícím aplikaci z jakéhokoli jiného důvodu.

> Pokud chcete používat Azure Virtual Machines ve vlastním datovém centru nebo jiných místních počítačích, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="docker-container-registry"></a>Registr kontejneru Dockeru

Pokud vaše aplikace používá Docker, můžete svoji aplikaci publikovat do registru kontejneru Docker.

### <a name="when-to-choose-docker-container-registry"></a>Kdy zvolit Docker Container Registry

- Chcete nasadit kontejnerové aplikace

Další informace najdete v následujících článcích:

- [Nasazení kontejneru ASP.NET do registru kontejneru](../containers/hosting-web-apps-in-docker.md)
- [Nasazení do Docker Hubu](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Složka

Nasazení do systému souborů znamená kopírování souborů aplikace do konkrétní složky na vašem počítači. Nasazení do složky se nejčastěji používá pro účely testování nebo pro nasazení aplikace pro použití v omezeném počtu lidí, pokud počítač používá taky Server. Pokud je cílová složka sdílena v síti, pak nasazení do systému souborů může zpřístupnit soubory webové aplikace ostatním uživatelům, kteří je pak mohli nasadit na konkrétní servery.
::: moniker range=">=vs-2019"
Počínaje sadou Visual Studio 2019 16,8 obsahuje cíl složky možnost publikování aplikace .NET pro Windows pomocí technologie ClickOnce.

Pokud chcete publikovat rozhraní .NET Core 3,1 nebo novější, aplikace pro Windows s ClickOnce, přečtěte si téma [nasazení aplikace .NET pro Windows pomocí technologie ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end
Všechny místní počítače, na kterých běží server, můžou aplikaci zpřístupnit přes Internet nebo intranet v závislosti na tom, jak je nakonfigurovaná, a sítích, ke kterým jsou připojené. (Pokud počítač připojujete přímo k Internetu, buďte obzvláště opatrní při ochraně před externími bezpečnostními hrozbami.) Vzhledem k tomu, že tyto počítače spravujete, budete mít plnou kontrolu nad tím, jak softwarové, tak hardwarové konfigurace.

Pokud z nějakého důvodu (například přístup k počítači) nemůžete používat cloudové služby, jako je Azure App Service nebo Azure Virtual Machines, můžete [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) použít ve svém vlastním datovém centru. Azure Stack umožňuje spravovat a používat výpočetní prostředky prostřednictvím Azure App Service a Azure Virtual Machines, a přitom přitom udržuje vše v místním prostředí.

### <a name="when-to-choose-file-system-deployment"></a>Kdy zvolit nasazení systému souborů

- Aplikaci musíte nasadit jenom do sdílené složky, ze které ji ostatní nasadí na různé servery.
::: moniker range=">=vs-2019"
- Chcete nasadit aplikaci .NET pro Windows pomocí technologie ClickOnce
::: moniker-end
- Potřebujete pouze místní testovací nasazení.
- Chcete prošetřit a potenciálně upravit soubory aplikace nezávisle, než je odešlete do jiného cíle nasazení.

Další informace najdete v tématu [rychlý Start – nasazení do místní složky](quickstart-deploy-to-local-folder.md).
::: moniker range=">=vs-2019"
Další informace o nasazení aplikace .NET pro Windows pomocí technologie ClickOnce naleznete v tématu [nasazení aplikace .NET pro Windows pomocí technologie ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end

Další nápovědu k výběru nastavení najdete v následujících tématech:

- [Nasazení závislé na rozhraní vs. samostatně uzavřené nasazení](/dotnet/core/deploying/)
- [Cílové identifikátory modulu runtime (přenosná RID, et al)](/dotnet/core/rid-catalog)
- [Konfigurace ladění a vydaných verzí](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>Server FTP/FTPS

Server FTP/FTPS umožňuje nasazení aplikace na jiný server než Azure. Může se nasadit na systém souborů nebo na jiný server (Internet nebo intranet), ke kterému máte přístup, včetně těch, které jsou k dispozici v jiných cloudových službách. Může pracovat s nasazením webu (soubory nebo. ZIP) a FTP.

Při volbě serveru FTP/FTPS vás Visual Studio vyzve k zadání názvu profilu a pak shromáždí další informace o **připojení** , včetně cílového serveru nebo umístění, názvu lokality a přihlašovacích údajů. Na kartě **Nastavení** můžete řídit následující chování:

- Konfigurace, kterou chcete nasadit.
- Zda odebrat existující soubory z cílového umístění.
- Určuje, zda má být během publikování předkompilována.
- Určuje, zda mají být vyloučeny soubory z App_Data složky z nasazení.

V aplikaci Visual Studio můžete vytvořit libovolný počet profilů nasazení FTP/FTPS, aby bylo možné spravovat profily s různými nastaveními.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Kdy zvolit nasazení serveru FTP/FTPS

- Cloudové služby používáte na jiném poskytovateli než Azure, ke kterému se dá přistup prostřednictvím adres URL.
- Chcete nasadit pomocí jiných přihlašovacích údajů, než jsou ty, které používáte v rámci sady Visual Studio, nebo které se vztahují přímo k vašim účtům Azure.
- Chcete odstranit soubory z cíle při každém nasazení.

## <a name="web-server-iis"></a>Webový server (IIS)

Webový server služby IIS umožňuje nasazení aplikace na jiný webový server než Azure. Může se nasadit na server IIS (Internet nebo intranet), ke kterému máte přístup, včetně těch, které jsou k dispozici v jiných cloudových službách. Může pracovat s Nasazení webu nebo balíčkem Nasazení webu.

Při výběru webového serveru služby IIS vás aplikace Visual Studio vyzve k zadání názvu profilu a následnému shromažďování dalších informací o **připojení** , včetně cílového serveru nebo umístění, názvu lokality a přihlašovacích údajů. Na kartě **Nastavení** můžete řídit následující chování:

- Konfigurace, kterou chcete nasadit.
- Zda odebrat existující soubory z cílového umístění.
- Určuje, zda má být během publikování předkompilována.
- Určuje, zda mají být vyloučeny soubory z App_Data složky z nasazení.

V aplikaci Visual Studio můžete vytvořit libovolný počet profilů nasazení webového serveru služby IIS, aby bylo možné spravovat profily s různými nastaveními.

### <a name="when-to-choose-web-server-iis-deployment"></a>Kdy zvolit nasazení webového serveru (IIS)

- Službu IIS používáte k publikování webu nebo služby, ke které je možné přistupovat prostřednictvím adres URL.
- Chcete nasadit pomocí jiných přihlašovacích údajů, než jsou ty, které používáte v rámci sady Visual Studio, nebo které se vztahují přímo k vašim účtům Azure.
- Chcete odstranit soubory z cíle při každém nasazení.

Další informace najdete v tématu [rychlý Start – nasazení na web](quickstart-deploy-to-a-web-site.md).

Nápovědu k řešení potíží ASP.NET Core ve službě IIS najdete v tématu věnovaném [řešení potíží ASP.NET Core na Azure App Service a IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="import-profile"></a>Importovat profil

Profil můžete importovat při publikování do služby IIS nebo Azure App Service. Nasazení můžete nakonfigurovat pomocí *souboru nastavení publikování* (*\* . publishsettings*). Soubor nastavení publikování se vytvoří prostřednictvím služby IIS nebo Azure App Service, nebo se dá vytvořit ručně a pak ho můžete importovat do sady Visual Studio.

Použití souboru nastavení publikování může zjednodušit konfiguraci nasazení a funguje lépe v týmovém prostředí, a to v případě ruční konfigurace jednotlivých profilů nasazení.

### <a name="when-to-choose-import-profile"></a>Kdy zvolit možnost importovat profil

- Publikujete do služby IIS a chcete zjednodušit konfiguraci nasazení.
- Publikujete do služby IIS nebo Azure App Service a chcete zrychlit konfiguraci nasazení pro opakované použití nebo pro členy týmu, kteří publikují do stejné služby.

Další informace najdete v následujících článcích:

- [Import nastavení publikování a nasazení do služby IIS](tutorial-import-publish-settings-iis.md)
- [Import nastavení publikování a nasazení do Azure](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>Konfigurovat nastavení nasazení rozhraní .NET

Další nápovědu k výběru nastavení najdete v následujících tématech:

- [Nasazení závislé na rozhraní vs. samostatně uzavřené nasazení](/dotnet/core/deploying/)
- [Cílové identifikátory modulu runtime (přenosná RID, et al)](/dotnet/core/rid-catalog)
- [Konfigurace ladění a vydaných verzí](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Další kroky

Kurzy:

- [Nasazení aplikace .NET Core pomocí nástroje Publikovat](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace ASP.NET Core do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Nasazení ve Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Nasazení aplikací pro UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace Node.js do Azure pomocí Nasazení webu](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace v Pythonu pro Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
