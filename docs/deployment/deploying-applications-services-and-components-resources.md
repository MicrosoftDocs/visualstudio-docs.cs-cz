---
title: Přehled nasazení | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93a389fdafb6167fb132578111c7a8b5d02c8495
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068049"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Přehled nasazení v sadě Visual Studio

Nasazením aplikace, služby nebo komponenty ji budete distribuovat pro instalaci na dalších počítačích, zařízeních, serverech nebo v cloudu. V sadě Visual Studio můžete zvolit vhodnou metodu pro potřebný typ nasazení.

Pro mnoho běžných typů aplikací můžete nasadit vaše aplikace přímo z Průzkumníku řešení v sadě Visual Studio. Stručný přehled této funkce, najdete v části [první seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md).

![Zvolte možnost publikování](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jaké možnosti publikování jsou pro mě nejlepší?

Z Visual Studia aplikace lze publikovat přímo do těchto cílů:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [Systém souborů](#file-system)
- [Vlastní cíle (služba IIS, FTP atd.) ](#custom-targets), což zahrnuje všechny libovolné webové servery.

Na **publikovat** kartu, vyberte existující profil publikování, importovat existující nebo vytvořte novou pomocí možnosti uvedené tady. Prohlídka možnosti publikování v integrovaném vývojovém prostředí pro různých typů aplikací, najdete v části [první seznámení s nasazováním](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) a [App Service v Linuxu](/azure/app-service/containers/app-service-linux-intro) což vývojářům umožňuje rychle vytvářet nejrůznější škálovatelných webových aplikací a služeb bez údržbu infrastruktury.

Zjistíte, kolik výpočetního prostředí power App Service má výběrem [cenové úrovně nebo plán](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) pro obsahující službu App Service. Může mít několik webových aplikací (a další typy aplikací) sdílejí stejné služby App Service beze změny cenové úrovně. Můžete například hostovat vývoje, testovací a produkční webové aplikace společně ve stejné službě App Service.

Služby App Service běží na virtuálních počítačích hostovaných v cloudu v Azure, ale tyto virtuální počítače spravuje za vás. Každou aplikaci v App Service bude přiřazen jedinečný \*. azurewebsites.net URL; všechny cenové úrovně než Free povolit přiřazení vlastních názvů domén do lokality.

### <a name="when-to-choose-azure-app-service"></a>Kdy zvolit službu Azure App Service

- Chcete nasadit webovou aplikaci, která je přístupná prostřednictvím Internetu.
- Chcete automatické škálování webové aplikace podle potřeby, aniž byste museli znovu nasadit.
- Nechcete spravovat serverovou infrastrukturu (včetně aktualizací softwaru).
- Není nutné žádné přizpůsobení na úrovni počítače na serverech, které jsou hostiteli webové aplikace.

> Pokud chcete ve svém vlastním datovém centru nebo jiných místních počítačů pomocí služby Azure App Service, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Další informace o publikování do služby App Service najdete v tématu [rychlý start – publikování do služby Azure App Service](quickstart-deploy-to-azure.md) a [rychlý start – publikování aplikace ASP.NET Core do Linuxu](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Azure Virtual Machines (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) umožňují vytvářet a spravovat libovolný počet výpočetních prostředků v cloudu. Podle za předpokladu, že odpovědnost za všechny softwaru a aktualizací na virtuálních počítačích, můžete přizpůsobit je tak, jak požadovaného podle požadavků vaší aplikace. Virtuální počítače mají přístup přímo přes vzdálenou plochu a každý z nich, zůstane přiřazená IP adresa jako požadované.

Škálování aplikace, která je hostovaná na virtuálních počítačích zahrnuje roztáčení další virtuální počítače podle potřeby a poté nasaďte potřebný software. Tato další úroveň řízení umožňuje škálovat jinak v různých oblastech globální. Například pokud vaše aplikace obsluhuje zaměstnanci v různých regionální pobočky, je možné škálovat vaše virtuální počítače podle počtu zaměstnanců v těchto oblastech potenciálně snížení nákladů.

Další informace najdete [podrobné porovnání](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) mezi Azure App Service, Azure Virtual Machines a dalšími službami Azure, které můžete použít jako cíl nasazení pomocí vlastní možnost v sadě Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kdy zvolit Azure aplikace Virtual Machines

- Chcete nasadit webovou aplikaci, která je přístupná přes Internet s úplnou kontrolou nad životnost přiřazené IP adresy.
- Potřebujete přizpůsobení na úrovni počítače na serverech, které obsahuje další software, jako jsou specializované databáze systému, konkrétní síťových konfigurací, diskových oddílů a tak dále.
- Chcete, aby dobře úroveň kontroly nad škálování webové aplikace.
- Potřebujete přímý přístup k serverům hostování vaší aplikace z jiného důvodu.

> Pokud chcete ve svém vlastním datovém centru nebo jiných místních počítačů pomocí Azure Virtual Machines, můžete to udělat pomocí [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>Systém souborů

Nasazení do systému souborů znamená, že jednoduše zkopírovat soubory vaší aplikace do konkrétní složky ve vašem počítači. Toto je nejčastěji používají pro účely testování a nasazení aplikace pro použití u omezený počet lidí, pokud počítač běží na serveru. Pokud cílová složka je sdílena v síti, pak nasazení do systému souborů můžete zpřístupnit webové aplikace soubory ostatním uživatelům, kteří můžou potom ji nasadíte do konkrétních serverů.

Žádné místní počítače, na kterých běží server můžete zpřístupnit vaše aplikace přes Internet nebo Intranet v závislosti na tom, jak je nakonfigurovaný a sítě, ke kterým je připojen. (Pokud se počítač připojit přímo k Internetu, buďte obezřetně, aby je chránil před externí ohrožení zabezpečení.) Vzhledem k tomu, že budete spravovat tyto počítače, jste si úplnou kontrolu nad softwarových a hardwarových konfiguracích.

Všimněte si, že pokud z nějakého důvodu (jako je například přístup k počítačům) nejste schopni ohledně použití cloudových služeb, jako je Azure App Service nebo Azure Virtual Machines, můžete použít [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) ve svém vlastním datovém centru. Azure Stack umožňuje spravovat a využívat přitom ještě všechno, co místní výpočetní prostředky prostřednictvím služby Azure App Service a Azure Virtual Machines.

### <a name="when-to-choose-file-system-deployment"></a>Kdy použít nasazení systému souborů

- Potřebujete pouze nasazení aplikace do sdílené složky, ze kterého ostatní nasadí ho na jiné servery.
- Potřebujete jenom místní testovací nasazení.
- Chcete prozkoumat a upravit soubory aplikace potenciálně nezávisle na sobě před jejich odesláním do jiného cíl nasazení.

Další informace najdete v tématu [rychlý start – nasazení do místní složky](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Vlastní cíle (služba IIS, FTP)

Vlastní cílové umožňuje nasazení aplikace na jiný cíl než Azure App Service, Azure Virtual Machines nebo místního systému souborů. Můžete nasadit do systému souborů nebo libovolný jiný server (Internet nebo Intranet) ke kterým mají přístup, včetně těch v jiných cloudových službách. Můžete pracovat s rozhraním web nasazení (soubory nebo. PSČ) a protokolu FTP.

Při výběru vlastního cíle, Visual Studio vás vyzve k zadání názvu profilu a potom shromáždit další **připojení** informace, včetně cílového serveru nebo umístění, název serveru a přihlašovací údaje. Můžete řídit následující chování **nastavení** kartu:

- Konfiguraci, kterou chcete nasadit.
- Zda má být odebrána existující soubory z cílového umístění.
- Určuje, zda předkompilovat během publikování.
- Jestli se mají vyloučit soubory ve složce App_Data z nasazení.

Můžete vytvořit libovolný počet vlastních nasazení profilů v sadě Visual Studio, což umožňuje spravovat profily s různými nastaveními.

### <a name="when-to-choose-custom-deployment"></a>Kdy použít vlastní nasazení

- Použití cloudových služeb prostřednictvím poskytovatele služeb kromě Azure, který je přístupný prostřednictvím adresy URL.
- Chcete nasadit, pomocí přihlašovacích údajů než těch, které používáte v rámci sady Visual Studio, nebo ty přímo navázána na účtů Azure.
- Chcete odstranit soubory z cíle pokaždé, když nasazujete.

Další informace najdete v tématu [rychlý start – nasazení do webové stránky](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Další kroky

Kurzy:

- [Nasazení aplikace .NET Core pomocí nástroje publish](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace ASP.NET core do Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Nasazení ve Visual C++](/cpp/ide/deployment-in-visual-cpp)
- [Nasazení aplikací pro UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace v Node.js do Azure pomocí nasazení webu](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikování aplikace v Pythonu do Azure App Service](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
