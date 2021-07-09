---
title: Nasazení Visual Studio aplikace do složky, služby IIS, Azure nebo jiného cíle
titleSuffix: ''
description: Přečtěte si další informace o možnostech publikování aplikace pomocí nástroje Publikovat.
ms.custom:
- SEO-VS-2020
- contperf-fy21q1
ms.date: 08/21/2020
ms.topic: troubleshooting
f1_keywords:
- vs.publish
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 099bd2c6cc47895c913b3f852835d2fd09d0f9c3
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549482"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Nasazení aplikace do složky, služby IIS, Azure nebo jiného cíle

Nasazením aplikace, služby nebo komponenty ji budete distribuovat pro instalaci na dalších počítačích, zařízeních, serverech nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení.

Získejte pomoc s úlohou nasazení:

- Nejste si jistí, jakou možnost nasazení zvolit? Viz [Jaké možnosti publikování jsou pro mě správné?](#what-publishing-options-are-right-for-me)
- Nápovědu k problémům s nasazením pro Azure App Service nebo IIS najdete v tématu Řešení [ASP.NET Core na Azure App Service a IIS.](/aspnet/core/test/troubleshoot-azure-iis)
- Nápovědu ke konfiguraci nastavení nasazení .NET najdete v tématu [Konfigurace nastavení nasazení .NET.](#configure-net-deployment-settings)
- Pokud chcete profil publikování nasadit do nového cíle,  vyberte v  okně Publikovat pro nakonfigurovaný profil možnost Nový.

   ![Vytvoření nového profilu publikování](../deployment/media/create-a-new-publish-profile.png)

   Potom v okně Publikovat zvolte možnost nasazení. Informace o možnostech publikování najdete v následujících částech.

## <a name="what-publishing-options-are-right-for-me"></a>Jaké možnosti publikování jsou pro mě správné?

V rámci Visual Studio lze aplikace publikovat přímo do následujících cílů:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Docker Container Registry](#docker-container-registry)
- [Složka](#folder)
- [Server FTP/FTPS](#ftpftps-server)
- [Webový server (IIS)](#web-server-iis)
- [Import profilu](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [App Service](#azure-app-service)
- [App Service Linux](#azure-app-service)
- [SLUŽBA IIS (zvolte IIS, FTP atd.)](#web-server-iis)
- [FTP/FTPS (zvolte IIS, FTP atd.)](#ftpftps-server)
- [Složka](#folder)
- [Import profilu](#import-profile)
::: moniker-end

Předchozí možnosti se zobrazí, jak je znázorněno na následujícím obrázku při vytváření nového profilu publikování.

::: moniker range=">=vs-2019"
![Volba možnosti publikování](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Volba možnosti publikování](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Stručný přehled obecných možností nasazení aplikací najdete v tématu [První pohled na nasazení.](../deployment/deploying-applications-services-and-components.md)

## <a name="azure"></a>Azure 

Když zvolíte Azure, můžete si vybrat mezi:

- [Azure App Service](#azure-app-service) běžící na Windows, Linuxu nebo jako image Dockeru
- Image Dockeru nasazená do [Azure Container Registry](#azure-container-registry)
- Virtuální [počítač Azure](#azure-virtual-machine)

![Volba služby Azure](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) pomáhá vývojářům rychle vytvářet škálovatelné webové aplikace a služby bez nutnosti udržovat infrastrukturu. Aplikace App Service běží na virtuálních počítačích hostovaných v cloudu v Azure, ale tyto virtuální počítače se spravují za vás. Každé aplikaci v App Service bude přiřazena jedinečná adresa URL .azurewebsites.net. Všechny cenové úrovně kromě úrovně Free umožňují přiřazovat k webu \* vlastní názvy domén.

Pokud zvolíte cenovou úroveň nebo plán pro [](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) App Service, zjistíte, jaký výpočetní výkon má App Service. Můžete mít několik webových aplikací (a jiných typů aplikací) sdílet stejné App Service beze změny cenové úrovně. Můžete například hostovat vývojové, pracovní a produkční webové aplikace společně ve stejné App Service.

#### <a name="when-to-choose-azure-app-service"></a>Kdy zvolit Azure App Service

- Chcete nasadit webovou aplikaci, která je přístupná přes internet.
- Chcete automaticky škálovat webovou aplikaci podle poptávky bez nutnosti opětovného nasazení.
- Nechcete udržovat serverovou infrastrukturu (včetně aktualizací softwaru).
- Na serverech, které hostí vaši webovou aplikaci, nepotřebujete žádná přizpůsobení na úrovni počítače.

> Pokud chcete použít Azure App Service ve vlastním datacentru nebo jiných místních počítačích, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Další informace o publikování do App Service najdete v těchto tématu:
- [Rychlý start – Publikování do Azure App Service](quickstart-deploy-to-azure.md)
- [Rychlý start – Publikování ASP.NET Core do Linuxu](quickstart-deploy-to-linux.md)
- [Publikování ASP.NET Core aplikace do Azure App Service](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- Řešení ASP.NET Core potíží s Azure App Service a [službou IIS.](/aspnet/core/test/troubleshoot-azure-iis)

### <a name="azure-container-registry"></a>Azure Container Registry

[Azure Container Registry](/azure/container-registry/) umožňuje sestavovat, ukládat a spravovat image a artefakty kontejnerů Dockeru v privátním registru pro všechny typy kontejnerových nasazení.

#### <a name="when-to-choose-azure-container-registry"></a>Kdy zvolit Azure Container Registry

- Když máte existující kanál vývoje a nasazení kontejneru Dockeru.
- Když chcete sestavit image kontejneru Dockeru v Azure.

Další informace najdete tady:

- [Nasazení kontejneru ASP.NET do registru kontejneru](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Virtuální počítač Azure

[Azure Virtual Machines umožňuje](https://azure.microsoft.com/documentation/services/virtual-machines/) vytvářet a spravovat libovolný počet výpočetních prostředků v cloudu. Když budete mít na virtuálních počítači odpovědnost za veškerý software a aktualizace, můžete si je podle potřeby přizpůsobit podle potřeby vaší aplikace. K virtuálním počítačům můžete přistupovat přímo přes Vzdálenou plochu a každý z nich bude mít přiřazenou IP adresu tak dlouho, jak je to žádoucí.

Škálování aplikace hostované na virtuálních počítačích zahrnuje roztáčení dalších virtuálních počítačů podle poptávky a nasazení potřebného softwaru. Tato další úroveň řízení umožňuje různě škálovat v různých globálních oblastech. Pokud například vaše aplikace obsluhuuje zaměstnance v různých regionálních pobočkách, můžete virtuální počítače škálovat podle počtu zaměstnanců v těchto oblastech a potenciálně tak snížit náklady.

Další informace najdete [](/azure/architecture/guide/technology-choices/compute-decision-tree) v podrobném porovnání služeb Azure App Service, Azure Virtual Machines a dalších služeb Azure, které můžete použít jako cíl nasazení pomocí možnosti Vlastní v Visual Studio.

#### <a name="when-to-choose-azure-virtual-machines"></a>Kdy zvolit Azure Virtual Machines

- Chcete nasadit webovou aplikaci, která je přístupná přes internet a má plnou kontrolu nad životností přiřazených IP adres.
- Na serverech potřebujete přizpůsobení na úrovni počítače, která zahrnují další software, jako je specializovaný databázový systém, konkrétní síťové konfigurace, diskové oddíly atd.
- Chcete mít přesnou úroveň kontroly nad škálováním webové aplikace.
- Z jakéhokoli jiného důvodu potřebujete přímý přístup k serverům hostující vaši aplikaci.

> Pokud chcete azure Virtual Machines ve vlastním datacentru nebo jiných místních počítačích, můžete to udělat pomocí Azure Stack [.](https://azure.microsoft.com/overview/azure-stack/)

## <a name="docker-container-registry"></a>Registr kontejneru Dockeru

Pokud vaše aplikace používá Docker, můžete kontejnerizovanou aplikaci publikovat do registru kontejnerů Dockeru.

### <a name="when-to-choose-docker-container-registry"></a>Kdy zvolit docker Container Registry

- Chcete nasadit kontejnerizovanou aplikaci

Další informace najdete v následujících článcích:

- [Nasazení kontejneru ASP.NET do registru kontejneru](../containers/hosting-web-apps-in-docker.md)
- [Nasazení do Docker Hubu](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Složka

Nasazení do systému souborů znamená zkopírování souborů aplikace do konkrétní složky ve vašem počítači. Nasazení do složky se nejčastěji používá pro účely testování nebo k nasazení aplikace pro použití omezeným počtem lidí, pokud počítač také používá server. Pokud je cílová složka sdílená v síti, pak nasazení do systému souborů může z dostupných souborů webové aplikace udělat pro ostatní, kteří ji pak můžou nasadit na konkrétní servery.
::: moniker range=">=vs-2019"
Od verze Visual Studio 2019 16.8 cíl složky zahrnuje možnost publikovat aplikaci .NET Windows pomocí ClickOnce.

Pokud chcete publikovat .NET Core 3.1 nebo novější, Windows s ClickOnce, podívejte se na nasazení aplikace [.NET Windows pomocí ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end
Všechny místní počítače, na kterých běží server, mohou vaši aplikaci z internetu nebo intranetu získat v závislosti na tom, jak je nakonfigurovaná, a v sítích, ke kterým je připojená. (Pokud počítač připojíte přímo k internetu, buďte obzvláště opatrní, abyste ho ochránili před externími bezpečnostními hrozbami.) Protože tyto počítače spravujete, máte úplnou kontrolu nad konfigurací softwaru a hardwaru.

Pokud z nějakého důvodu (například přístup k počítači) nemůžete používat cloudové služby, jako je Azure App Service [](https://azure.microsoft.com/overview/azure-stack/) nebo Azure Virtual Machines, můžete použít Azure Stack ve vlastním datacentru. Tento Azure Stack umožňuje spravovat a používat výpočetní prostředky prostřednictvím služeb Azure App Service a Azure Virtual Machines a přitom zachovat vše v místním prostředí.

### <a name="when-to-choose-file-system-deployment"></a>Kdy zvolit nasazení systému souborů

- Aplikaci je potřeba nasadit jenom do sdílené složky, ze které ji ostatní nasadí na různé servery.
::: moniker range=">=vs-2019"
- Chcete nasadit aplikaci .NET Windows pomocí ClickOnce
::: moniker-end
- Potřebujete jenom místní testovací nasazení.
- Chcete prověřit a potenciálně upravit soubory aplikace nezávisle před jejich odesláním do jiného cíle nasazení.

Další informace najdete v tématu [Rychlý start – nasazení do místní složky](quickstart-deploy-to-local-folder.md).
::: moniker range=">=vs-2019"
další informace o nasazení aplikace Windows .net pomocí ClickOnce najdete v tématu [nasazení aplikace .net Windows pomocí ClickOnce](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end

Další nápovědu k výběru nastavení najdete v následujících tématech:

- [Nasazení závislé na rozhraní vs. samostatně uzavřené nasazení](/dotnet/core/deploying/)
- [Cílové identifikátory modulu runtime (přenosná RID, et al)](/dotnet/core/rid-catalog)
- [Konfigurace ladění a vydaných verzí](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>Server FTP/FTPS

Server FTP/FTPS umožňuje nasazení aplikace na jiný server než Azure. Může se nasadit na systém souborů nebo na jiný server (Internet nebo intranet), ke kterému máte přístup, včetně těch, které jsou k dispozici v jiných cloudových službách. Může pracovat s nasazením webu (soubory nebo .ZIP) a FTP.

při volbě serveru FTP/FTPS vás Visual Studio vyzve k zadání názvu profilu a pak shromáždí další informace o **připojení** , včetně cílového serveru nebo umístění, názvu lokality a přihlašovacích údajů. na kartě **Nastavení** můžete řídit následující chování:

- Konfigurace, kterou chcete nasadit.
- Zda odebrat existující soubory z cílového umístění.
- Určuje, zda má být během publikování předkompilována.
- Určuje, zda mají být vyloučeny soubory z App_Data složky z nasazení.

v Visual Studio můžete vytvořit libovolný počet profilů nasazení FTP/FTPS, což umožňuje spravovat profily s různými nastaveními.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Kdy zvolit nasazení serveru FTP/FTPS

- Cloudové služby používáte na jiném poskytovateli než Azure, ke kterému se dá přistup prostřednictvím adres URL.
- chcete nasadit pomocí jiných přihlašovacích údajů, než jsou ty, které používáte v rámci Visual Studio, nebo je můžete přivázat přímo na vaše účty Azure.
- Chcete odstranit soubory z cíle při každém nasazení.

## <a name="web-server-iis"></a>Webový server (IIS)

Webový server služby IIS umožňuje nasazení aplikace na jiný webový server než Azure. Může se nasadit na server IIS (Internet nebo intranet), ke kterému máte přístup, včetně těch, které jsou k dispozici v jiných cloudových službách. Může pracovat s Nasazení webu nebo balíčkem Nasazení webu.

když zvolíte webový server služby IIS, Visual Studio vás vyzve k zadání názvu profilu a pak shromáždí další informace o **připojení** , včetně cílového serveru nebo umístění, názvu lokality a přihlašovacích údajů. na kartě **Nastavení** můžete řídit následující chování:

- Konfigurace, kterou chcete nasadit.
- Zda odebrat existující soubory z cílového umístění.
- Určuje, zda má být během publikování předkompilována.
- Určuje, zda mají být vyloučeny soubory z App_Data složky z nasazení.

v Visual Studio můžete vytvořit libovolný počet profilů nasazení webového serveru služby IIS, což umožňuje spravovat profily s různými nastaveními.

### <a name="when-to-choose-web-server-iis-deployment"></a>Kdy zvolit nasazení webového serveru (IIS)

- Službu IIS používáte k publikování webu nebo služby, ke které je možné přistupovat prostřednictvím adres URL.
- chcete nasadit pomocí jiných přihlašovacích údajů, než jsou ty, které používáte v rámci Visual Studio, nebo je můžete přivázat přímo na vaše účty Azure.
- Chcete odstranit soubory z cíle při každém nasazení.

Další informace najdete v tématu [rychlý Start – nasazení na web](quickstart-deploy-to-a-web-site.md).

nápovědu k řešení potíží ASP.NET Core ve službě iis najdete v tématu věnovaném [řešení potíží ASP.NET Core na Azure App Service a iis](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="import-profile"></a>Importovat profil

Profil můžete importovat při publikování do služby IIS nebo Azure App Service. Nasazení můžete nakonfigurovat pomocí *souboru nastavení publikování* (*\* . publishsettings*). Soubor nastavení publikování se vytvoří prostřednictvím služby IIS nebo Azure App Service, nebo se dá vytvořit ručně a pak ho můžete importovat do Visual Studio.

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
- [publikování aplikace ASP.NET core do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Nasazení ve Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Nasazení aplikací pro UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace Node.js do Azure pomocí Nasazení webu](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace v Pythonu pro Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
