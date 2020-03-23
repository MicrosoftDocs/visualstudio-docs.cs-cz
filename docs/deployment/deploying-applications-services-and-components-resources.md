---
title: Přehled nasazení | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: b7c322b960360231c2e8a1d2aa1a9920bbcf5521
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79301998"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Přehled nasazení v sadě Visual Studio

Nasazením aplikace, služby nebo komponenty ji budete distribuovat pro instalaci na dalších počítačích, zařízeních, serverech nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení.

Pro mnoho běžných typů aplikací můžete nasadit aplikaci přímo z Průzkumníka řešení v sadě Visual Studio. Pro rychlou prohlídku této funkce, viz [První pohled na nasazení](../deployment/deploying-applications-services-and-components.md).

![Volba možnosti publikování](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jaké možnosti publikování jsou pro mě to pravé?

V rámci sady Visual Studio lze aplikace publikovat přímo na následující cíle:

- [Azure App Service](#azure-app-service)
- [Virtuální počítače Azure](#azure-virtual-machines)
- [Systém souborů](#file-system)
- [Vlastní cíle (IIS, FTP atd.),](#custom-targets-iis-ftp)které zahrnují všechny libovolné webové servery.

Na kartě **Publikovat** můžete vybrat existující profil publikování, importovat existující profil nebo vytvořit nový pomocí zde popsaných možností. Prohlídka možností publikování v ide pro různé typy aplikací, najdete [v tématu První pohled na nasazení](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) a [App Service na Linuxu](/azure/app-service/containers/app-service-linux-intro) pomáhají vývojářům rychle vytvářet různé škálovatelné webové aplikace a služby bez údržby infrastruktury.

Můžete určit, kolik výpočetnívýkon app service má výběrem [cenové úrovně nebo plán](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) pro obsahující app service. Můžete mít více webových aplikací (a další typy aplikací) sdílet stejnou službu App Service beze změny cenové úrovně. Můžete například hostovat vývojové, pracovní a produkční webové aplikace společně ve stejné službě App Service.

Služba App Service běží na virtuálních počítačích hostovaných v cloudu v Azure, ale tyto virtuální počítače se spravují za vás. Každé aplikaci ve službě App \*Service bude přiřazena jedinečná adresa URL .azurewebsites.net. všechny cenové úrovně jiné než Free umožňují přiřazování vlastních názvů domén k webu.

### <a name="when-to-choose-azure-app-service"></a>Kdy si vybrat službu Azure App Service

- Chcete nasadit webovou aplikaci, která je přístupná prostřednictvím Internetu.
- Chcete automaticky škálovat webové aplikace podle poptávky bez nutnosti opětovného nasazení.
- Nechcete udržovat serverovou infrastrukturu (včetně aktualizací softwaru).
- Nepotřebujete žádné vlastní nastavení na úrovni počítače na serverech, které jsou hostitelem webové aplikace.

> Pokud chcete službu Azure App Service používat ve vlastním datovém centru nebo v jiných místních počítačích, můžete tak učinit pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Další informace o publikování ve službě App Service najdete v [tématu Úvodní příručka – publikování ve službě Azure App Service](quickstart-deploy-to-azure.md) a Úvodní [příručka – publikování ASP.NET jádra na Linuxu](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Virtuální počítače Azure](https://azure.microsoft.com/documentation/services/virtual-machines/) umožňují vytvářet a spravovat libovolný počet výpočetních prostředků v cloudu. Převzetím odpovědnosti za veškerý software a aktualizace na virtuálních počítačích, můžete přizpůsobit je podle potřeby, jak vyžaduje vaše aplikace. K virtuálním počítačům můžete přistupovat přímo prostřednictvím vzdálené plochy a každý z nich bude udržovat přiřazenou adresu IP tak dlouho, jak je požadováno.

Škálování aplikace, která je hostovaná na virtuálních počítačích zahrnuje spřádání dalších virtuálních počítačů podle potřeby a následné nasazení potřebného softwaru. Tato další úroveň ovládacího prvku umožňuje škálovat odlišně v různých globálních oblastech. Pokud například vaše aplikace obsluhuje zaměstnance v různých regionálních kancelářích, můžete virtuální počítače škálovat podle počtu zaměstnanců v těchto oblastech a potenciálně snížit náklady.

Další informace najdete v [podrobném porovnání](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) mezi službou Azure App Service, virtuálními počítači Azure a dalšími službami Azure, které můžete použít jako cíl nasazení pomocí možnosti Vlastní ve Visual Studiu.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kdy si vybrat virtuální počítače s aplikacemi Azure

- Chcete nasadit webovou aplikaci, která je přístupná prostřednictvím Internetu, s plnou kontrolou nad životností přiřazených ADRES IP.
- Potřebujete vlastní nastavení na úrovni počítače na serverech, které zahrnuje další software, jako je například specializovaný databázový systém, specifické síťové konfigurace, diskové oddíly a tak dále.
- Chcete jemnou úroveň kontroly nad škálováním webové aplikace.
- Potřebujete přímý přístup k serverům hostujícím vaši aplikaci z jakéhokoli jiného důvodu.

> Pokud chcete virtuální počítače Azure používat ve vlastním datovém centru nebo v jiných místních počítačích, můžete tak učinit pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>Systém souborů

Nasazení do systému souborů znamená jednoduše zkopírovat soubory aplikace do určité složky ve vlastním počítači. To se nejčastěji používá pro účely testování nebo k nasazení aplikace pro použití omezeným počtem osob, pokud je v počítači také spuštěn server. Pokud je cílová složka sdílena v síti, může nasazení do systému souborů zpřístupnit soubory webové aplikace ostatním uživatelům, kteří ji pak mohou nasadit na konkrétní servery.

Všechny místní počítače, ve kterých je spuštěn server, mohou zpřístupnit vaši aplikaci prostřednictvím Internetu nebo intranetu v závislosti na konfiguraci a sítích, ke kterým je připojena. (Pokud počítač připojujete přímo k Internetu, buďte obzvláště opatrní, abyste jej ochránili před vnějšími bezpečnostními hrozbami.) Vzhledem k tomu, že tyto počítače spravujete, máte úplnou kontrolu nad konfigurací softwaru a hardwaru.

Všimněte si, že pokud z nějakého důvodu (například přístup k počítači) nejste schopni používat cloudové služby, jako je Azure App Service nebo Virtuální počítače Azure, můžete použít [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) ve vašem vlastním datovém centru. Azure Stack umožňuje spravovat a používat výpočetní prostředky prostřednictvím Služby Azure App Service a virtuálních počítačů Azure a přitom zachovat všechny místní.

### <a name="when-to-choose-file-system-deployment"></a>Kdy zvolit nasazení systému souborů

- Stačí nasadit aplikaci do sdílené složky, ze které ji ostatní nasadí na různé servery.
- Potřebujete pouze místní testovací nasazení.
- Chcete prozkoumat a potenciálně upravit soubory aplikace nezávisle před jejich odesláním na jiný cíl nasazení.

Další informace naleznete [v tématu Úvodní příručka – nasazení do místní složky.](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Vlastní cíle (IIS, FTP)

Vlastní cíl umožňuje nasadit vaši aplikaci na jiný cíl než Azure App Service, Virtuální počítače Azure nebo místní souborový systém. Může se nasadit do systému souborů nebo na jakýkoli jiný server (Internet nebo Intranet), ke kterému máte přístup, včetně serverů v jiných cloudových službách. Může pracovat s webovým nasazením (soubory nebo . ZIP) a FTP.

Při výběru vlastního cíle vás Visual Studio vyzve k zadání názvu profilu a poté shromáždí další informace o **připojení,** včetně cílového serveru nebo umístění, názvu webu a pověření. Na kartě **Nastavení** můžete ovládat následující chování:

- Konfigurace, kterou chcete nasadit.
- Určuje, zda mají být z cíle odebrány existující soubory.
- Určuje, zda se má předkompilovat během publikování.
- Určuje, zda mají být soubory ve složce App_Data z nasazení vyloučeny.

V sadě Visual Studio můžete vytvořit libovolný počet vlastních profilů nasazení, což umožní spravovat profily s různými nastaveními.

### <a name="when-to-choose-custom-deployment"></a>Kdy zvolit vlastní nasazení

- Používáte cloudové služby u jiného poskytovatele než Azure, ke kterému se dá přistupovat prostřednictvím adres URL.
- Chcete nasadit pomocí jiných přihlašovacích údajů, než které používáte v rámci sady Visual Studio, nebo pomocí těch, které jsou přímo vázány na vaše účty Azure.
- Chcete odstranit soubory z cíle při každém nasazení.

Další informace naleznete [v tématu Úvodní příručka – Nasazení na webovou stránku.](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Další kroky

Kurzy:

- [Nasazení aplikace .NET Core pomocí nástroje pro publikování](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování ASP.NET základní aplikace do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Nasazení ve Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Nasazení aplikací UPW](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace Node.js do Azure pomocí nasazení webu](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace Pythonu do služby Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
