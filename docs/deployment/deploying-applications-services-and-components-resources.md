---
title: Přehled nasazení | Dokumentace Microsoftu
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409371"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Přehled nasazení v sadě Visual Studio

Nasazením aplikace, služby nebo komponenty ji budete distribuovat pro instalaci na dalších počítačích, zařízeních, serverech nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení.

Pro mnoho běžných typů aplikací můžete nasadit vaše aplikace přímo z Průzkumníku řešení v sadě Visual Studio. Pro rychlou prohlídku této funkce si Projděte [první pohled na nasazení](../deployment/deploying-applications-services-and-components.md).

![Zvolte možnost publikování](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jaké možnosti publikování jsou pro mě nejlepší?

Z Visual Studia aplikace lze publikovat přímo do těchto cílů:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [Systém souborů](#file-system)
- [Vlastní cíle (IIS, FTP atd.)](#custom-targets-iis-ftp), které zahrnují všechny webové servery.

Na kartě **publikovat** můžete vybrat existující publikační profil, importovat stávající nebo vytvořit nový pomocí možností popsaných tady. Prohlídku možností publikování v integrovaném vývojovém prostředí pro různé typy aplikací najdete v tématu [první pohled na nasazení](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) a [App Service na Linux](/azure/app-service/containers/app-service-linux-intro) vývojářům pomůže rychle vytvářet nejrůznější škálovatelné webové aplikace a služby bez zachování infrastruktury.

Určíte, kolik výpočetní síly má App Service, výběrem [cenové úrovně nebo plánu](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) pro obsahující App Service. Může mít několik webových aplikací (a další typy aplikací) sdílejí stejné služby App Service beze změny cenové úrovně. Můžete například hostovat vývoje, testovací a produkční webové aplikace společně ve stejné službě App Service.

Služby App Service běží na virtuálních počítačích hostovaných v cloudu v Azure, ale tyto virtuální počítače spravuje za vás. Každé aplikaci v App Service bude přiřazená jedinečná \*adresa URL. azurewebsites.net; Všechny cenové úrovně jiné než Free umožňují přiřazení vlastních názvů domén k lokalitě.

### <a name="when-to-choose-azure-app-service"></a>Kdy zvolit službu Azure App Service

- Chcete nasadit webovou aplikaci, která je přístupná prostřednictvím Internetu.
- Chcete automatické škálování webové aplikace podle potřeby, aniž byste museli znovu nasadit.
- Nechcete spravovat serverovou infrastrukturu (včetně aktualizací softwaru).
- Není nutné žádné přizpůsobení na úrovni počítače na serverech, které jsou hostiteli webové aplikace.

> Pokud chcete použít Azure App Service ve vlastním datovém centru nebo jiných místních počítačích, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Další informace o publikování do App Service najdete v tématu [rychlý Start – publikování do Azure App Service](quickstart-deploy-to-azure.md) a [rychlé zprovoznění – publikování ASP.NET Core na Linux](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Azure Virtual Machines (virtuální počítače)](https://azure.microsoft.com/documentation/services/virtual-machines/) umožňují vytvářet a spravovat libovolný počet výpočetních prostředků v cloudu. Podle za předpokladu, že odpovědnost za všechny softwaru a aktualizací na virtuálních počítačích, můžete přizpůsobit je tak, jak požadovaného podle požadavků vaší aplikace. Virtuální počítače mají přístup přímo přes vzdálenou plochu a každý z nich, zůstane přiřazená IP adresa jako požadované.

Škálování aplikace, která je hostovaná na virtuálních počítačích zahrnuje roztáčení další virtuální počítače podle potřeby a poté nasaďte potřebný software. Tato další úroveň řízení umožňuje škálovat jinak v různých oblastech globální. Například pokud vaše aplikace obsluhuje zaměstnanci v různých regionální pobočky, je možné škálovat vaše virtuální počítače podle počtu zaměstnanců v těchto oblastech potenciálně snížení nákladů.

Další informace najdete v [podrobném porovnání](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) mezi Azure App Service, Azure Virtual Machines a dalšími službami Azure, které můžete použít jako cíl nasazení pomocí vlastní možnosti v aplikaci Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kdy zvolit Azure aplikace Virtual Machines

- Chcete nasadit webovou aplikaci, která je přístupná přes Internet s úplnou kontrolou nad životnost přiřazené IP adresy.
- Potřebujete přizpůsobení na úrovni počítače na serverech, které obsahuje další software, jako jsou specializované databáze systému, konkrétní síťových konfigurací, diskových oddílů a tak dále.
- Chcete, aby dobře úroveň kontroly nad škálování webové aplikace.
- Potřebujete přímý přístup k serverům hostování vaší aplikace z jiného důvodu.

> Pokud chcete používat Azure Virtual Machines ve vlastním datovém centru nebo jiných místních počítačích, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>Systém souborů

Nasazení do systému souborů znamená, že jednoduše zkopírovat soubory vaší aplikace do konkrétní složky ve vašem počítači. Toto je nejčastěji používají pro účely testování a nasazení aplikace pro použití u omezený počet lidí, pokud počítač běží na serveru. Pokud cílová složka je sdílena v síti, pak nasazení do systému souborů můžete zpřístupnit webové aplikace soubory ostatním uživatelům, kteří můžou potom ji nasadíte do konkrétních serverů.

Žádné místní počítače, na kterých běží server můžete zpřístupnit vaše aplikace přes Internet nebo Intranet v závislosti na tom, jak je nakonfigurovaný a sítě, ke kterým je připojen. (Pokud počítač připojujete přímo k Internetu, buďte obzvláště opatrní při ochraně před externími bezpečnostními hrozbami.) Vzhledem k tomu, že tyto počítače spravujete, budete mít plnou kontrolu nad tím, jak softwarové, tak hardwarové konfigurace.

Všimněte si, že pokud z nějakého důvodu (například přístup k počítači) nemůžete používat cloudové služby, jako je Azure App Service nebo Azure Virtual Machines, můžete [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) použít ve svém vlastním datovém centru. Azure Stack umožňuje spravovat a využívat přitom ještě všechno, co místní výpočetní prostředky prostřednictvím služby Azure App Service a Azure Virtual Machines.

### <a name="when-to-choose-file-system-deployment"></a>Kdy použít nasazení systému souborů

- Potřebujete pouze nasazení aplikace do sdílené složky, ze kterého ostatní nasadí ho na jiné servery.
- Potřebujete jenom místní testovací nasazení.
- Chcete prozkoumat a upravit soubory aplikace potenciálně nezávisle na sobě před jejich odesláním do jiného cíl nasazení.

Další informace najdete v tématu [rychlý Start – nasazení do místní složky](quickstart-deploy-to-local-folder.md) .

## <a name="custom-targets-iis-ftp"></a>Vlastní cíle (služba IIS, FTP)

Vlastní cílové umožňuje nasazení aplikace na jiný cíl než Azure App Service, Azure Virtual Machines nebo místního systému souborů. Můžete nasadit do systému souborů nebo libovolný jiný server (Internet nebo Intranet) ke kterým mají přístup, včetně těch v jiných cloudových službách. Můžete pracovat s rozhraním web nasazení (soubory nebo. PSČ) a protokolu FTP.

Při volbě vlastního cíle vás Visual Studio vyzve k zadání názvu profilu a následnému shromáždění dalších informací o **připojení** , včetně cílového serveru nebo umístění, názvu lokality a přihlašovacích údajů. Na kartě **Nastavení** můžete řídit následující chování:

- Konfiguraci, kterou chcete nasadit.
- Zda má být odebrána existující soubory z cílového umístění.
- Určuje, zda předkompilovat během publikování.
- Jestli se mají vyloučit soubory ve složce App_Data z nasazení.

Můžete vytvořit libovolný počet vlastních nasazení profilů v sadě Visual Studio, což umožňuje spravovat profily s různými nastaveními.

### <a name="when-to-choose-custom-deployment"></a>Kdy použít vlastní nasazení

- Použití cloudových služeb prostřednictvím poskytovatele služeb kromě Azure, který je přístupný prostřednictvím adresy URL.
- Chcete nasadit, pomocí přihlašovacích údajů než těch, které používáte v rámci sady Visual Studio, nebo ty přímo navázána na účtů Azure.
- Chcete odstranit soubory z cíle pokaždé, když nasazujete.

Další informace najdete v tématu [rychlý Start – nasazení na](quickstart-deploy-to-a-web-site.md) Web.

## <a name="next-steps"></a>Další kroky

Kurzy:

- [Nasazení aplikace .NET Core pomocí nástroje Publikovat](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace ASP.NET Core do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Nasazení ve Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Nasazení aplikací pro UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace v Node. js do Azure pomocí Nasazení webu](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace v Pythonu pro Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
