---
title: Povolení aktualizací správců v aplikaci Visual Studio pomocí koncového bodu Microsoft Configuration Manager
titleSuffix: ''
description: Přečtěte si další informace o tom, jak nasadit aktualizace správce do sady Visual Studio.
ms.date: 03/04/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ae0bdde60cbf4c4c1eed00847c76ee797809b8db
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2021
ms.locfileid: "105617325"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Povolení aktualizací správců v aplikaci Visual Studio pomocí koncového bodu Microsoft Configuration Manager

Nástroj Microsoft Endpoint Configuration Manager (SCCM) může spravovat aktualizace sady Visual Studio 2017 a Visual Studio 2019 pomocí pracovního postupu správce aktualizací softwaru.

> [!NOTE]
> V případě jednoduchosti dokumentace se níže uvedený obsah bude vztahovat na produkty Visual Studio 2017 a Visual Studio 2019 souhrnně jako Visual Studio.

Když Microsoft publikuje novou aktualizaci sady Visual Studio na Content Delivery Network (CDN), Microsoft bude na Microsoft Update serverech publikovat současně odpovídající balíček aktualizace správce. Tím umožníte, aby správce distribuovat aktualizaci sady Visual Studio prostřednictvím [katalogu Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) nebo [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Configuration Manager lze nastavit tak, aby synchronizoval aktualizace správce sady Visual Studio z katalogu služby WSUS do serveru lokality a poté mohla stáhnout aktualizaci a distribuovat ji do klientských počítačů aplikace Visual Studio v rámci organizace. Další informace o tom, které opravy jsou k dispozici v jednotlivých vydáních sady Visual Studio, naleznete v [poznámkách k verzi](https://docs.microsoft.com/visualstudio/releases/2019/release-notes). 

Chcete-li distribuovat aktualizace správce sady Visual Studio prostřednictvím Configuration Manager, je nutné provést tyto dva kroky počáteční přípravy: 
1. Povolí Configuration Manager přijímat oznámení o aktualizacích pro správce sady Visual Studio. 
2. Povolit (nebo zakázat) klientským počítačům přijímat aktualizace správce sady Visual Studio z Configuration Manager.

Po provedení těchto kroků můžete pomocí možností správy aktualizace softwaru Configuration Manager nasadit aktualizace správce sady Visual Studio. Různé typy a charakteristiky aktualizací pro správce sady Visual Studio jsou popsány v tématu [použití aktualizací správce](../install/applying-administrator-updates.md), což poskytuje pokyny k tomu, jak a kdy by se měly distribuovat v celé organizaci. Další informace o funkcích a možnostech Configuration Manager najdete v tématu [nasazení aktualizací softwaru ve službě Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/deploy-use/deploy-software-updates). 

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Povolit Configuration Manager přijímání oznámení o aktualizacích pro správce sady Visual Studio 

Pokud chcete povolit Configuration Manager ke správě aktualizací pro správce sady Visual Studio, budete potřebovat: 

* Aktuální licencovaná verze Windows serveru, na které běží Microsoft Endpoint Configuration Manager (Current Branch) a Windows Server Update Services (WSUS). K nasazení těchto aktualizací nemůžete použít samotný server WSUS. musí se používat ve spojení s Configuration Manager. 

* Server WSUS nejvyšší úrovně v hierarchii a server lokality Configuration Manager nejvyšší úrovně musí mít přístup k adresám URL a portům sady Visual Studio, které jsou zde uvedené: [nainstalujte a použijte Visual Studio a služby Azure za bránou firewall nebo proxy server](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md).  

* Aby byly k dispozici balíčky aktualizací pro správce sady Visual Studio, musí být Configuration Manager koncového bodu Microsoft nakonfigurované pro příjem oznámení.  K tomu použijte následující postup a další informace najdete v tématu [Úvod do aktualizací softwaru ve službě Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/understand/software-updates-introduction).

  1. V konzole Configuration Manager vyberte možnost **Správa** (dole vlevo), vyberte položku **Konfigurace lokality** (vlevo uprostřed), poté vyberte možnost **lokality** a vyberte server lokality. 

  2. Na kartě **Domů** v horní části klikněte na tlačítko skupina **Nastavení** , vyberte možnost **Konfigurovat součásti lokality** a pak vyberte možnost **bod aktualizace softwaru**. 

  3. V dialogovém okně **Vlastnosti komponenty bodu aktualizace softwaru** : 

        * Na kartě **produkty** v hierarchii **vývojářské nástroje, modul runtime a distribuovat** lze zvolit verze sady Visual Studio, které chcete synchronizovat.   

        * Na kartě **klasifikace** se ujistěte, že je vybraná možnost aktualizace zabezpečení, balíčky funkcí a aktualizace.   

  4. V dalším kroku synchronizujte aktualizace softwaru se serverem WSUS výběrem **softwarové knihovny** (dole vlevo) a potom na kartě **Domů** v horní části vyberte tlačítko **synchronizovat aktualizace softwaru** . Synchronizace aktualizací softwaru zpřístupňuje dostupné aktualizace správců sady Visual Studio v nástroji a bude možné je nasadit z konzoly Configuration Manager.   

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Povolit (nebo zakázat) klientským počítačům možnost získávat aktualizace správců sady Visual Studio z Configuration Manager

Chcete-li povolit klientskému počítači, aby přijímali aktualizace správce sady Visual Studio, je nutné zajistit, aby byl správně nainstalován nástroj pro rozpoznávání klientů sady Visual Studio, a budete muset nastavit klíč registru, který klientovi umožní přijímat aktualizace správců.  

### <a name="visual-studio-client-detector-utility"></a>Nástroj pro rozpoznávání klientů Visual studia 

Na klientských počítačích musí být nainstalován nástroj pro rozpoznávání klienta sady Visual Studio, aby bylo možné aktualizace správce přijmout správně. Tento nástroj byl součástí všech nejnovějších verzí sady Visual Studio.  

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Kódování záměru správce na klientských počítačích 

Klientské počítače musí mít povolený příjem aktualizací správců. Tento krok je nezbytný k tomu, abyste se ujistili, že aktualizace nejsou neúmyslně nebo omylem nechtěně nahrály na nepodezřelé klientské počítače. 

Klíč **AdministratorUpdatesEnabled**   je určený pro správce ke kódování záměru správce. Tento klíč může být ve všech standardních umístěních sady Visual Studio, jak je popsáno v tématu [Nastavení výchozích hodnot pro podnikové nasazení v dokumentaci sady Visual Studio](https://docs.microsoft.com/visualstudio/install/set-defaults-for-enterprise-deployments) . Pro vytvoření a nastavení hodnoty tohoto klíče je nutný přístup správce na klientském počítači. 

* Chcete-li nakonfigurovat klientský počítač tak, aby přijímal aktualizace správce ****, nastavte   klíč REG_DWORD AdministratorUpdatesEnabled na hodnotu **1**. 
* Pokud  ****   klíč REG_DWORD AdministratorUpdatesEnabled **chybí nebo je nastaven na hodnotu 0**, aktualizace správce se zablokují pro použití v klientském počítači. 

## <a name="feedback-and-support"></a>Zpětná vazba a podpora
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Pomocí následujících metod můžete poskytnout zpětnou vazbu o aktualizacích správce sady Visual Studio nebo nahlásit problémy, které mají vliv na aktualizace:
* Přečtěte si pokyny k [řešení potíží s instalací a upgradem sady Visual Studio](../install/troubleshooting-installation-issues.md) .
* Položte otázky komunity na stránce [Visual Setup Q&Fórum](https://docs.microsoft.com/answers/topics/vs-setup.html).
* Přejít na [stránku podpory sady Visual Studio](https://visualstudio.microsoft.com/vs/support/)a ověřte, zda je váš problém uveden v části Nejčastější dotazy.  Můžete také vybrat tlačítko pro [odkaz na podporu](https://visualstudio.microsoft.com/vs/support/#talktous) pro nápovědu k chatu.
* [Poskytněte zpětnou vazbu k funkcím nebo nahlásit problém](https://aka.ms/vs/wsus/feedback) týmu sady Visual Studio pro toto prostředí.
* Obraťte se na správce technického účtu vaší organizace pro Microsoft.

## <a name="see-also"></a>Viz také
* [Použití aktualizací správců](../install/applying-administrator-updates.md)
* [Příručka pro správce sady Visual Studio](../install/visual-studio-administrator-guide.md)
* [Životní cyklus produktu Visual Studio a jeho údržba](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Zpráva k vydání verze pro Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Zpráva k vydání verze pro Visual Studio 2017](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Instalace sady Visual Studio](../install/install-visual-studio.md)
* [Nejčastější dotazy ke katalogu Microsoft Update](https://www.catalog.update.microsoft.com/faq.aspx)
* [Dokumentace k Microsoft Endpoint Configuration Manager (SCCM)](https://docs.microsoft.com/mem/configmgr)
* [Import aktualizací z katalogu Microsoft do Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS) – dokumentace](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
