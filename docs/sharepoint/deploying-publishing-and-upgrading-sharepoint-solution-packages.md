---
title: Nasazení, publikování a upgradování balíčků řešení služby SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 17578fbfb58d354f06e91c78f067d228b92860fe
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327200"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Nasazení, publikování a upgradování balíčků řešení služby SharePoint
  Až budete vyvíjet řešení služby SharePoint v sadě Visual Studio, můžete nasadit jeho souboru balíčku (WSP) na místním serveru SharePoint nebo jej publikujte do vzdáleného nebo místního serveru SharePoint. Pokud nasazujete soubory, můžete přizpůsobit, jak se nasadí soubory balíčku (WSP).  
  
> [!NOTE]  
>  V současné době mohou být publikovány pouze řešení v izolovaném prostoru na vzdálených serverech služby SharePoint. Další informace najdete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="deploy-publish-and-upgrade"></a>Nasazení, publikování a upgradování
 *Nasazení* odkazuje na kopírování soubor řešení služby SharePoint vytvořená z projektu služby SharePoint v sadě Visual Studio tak, aby místního hostitele. V nasazené řešení můžete nakonfigurovat jednotlivé kroky nasazení, třeba recyklace fondu Internetové informační služby (IIS), aktivaci řešení po nasazení a tak dále. K nasazení, použijte **nasadit** příkaz na **sestavení** nabídky. Další informace najdete v tématu [postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) a [postupy: nasazení a publikování řešení služby SharePoint na web služby SharePoint místní](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 *Publikování* odkazuje na nahrání souboru v izolovaném prostoru řešení služby SharePoint do vzdálené služby SharePoint webu; který je umístěný v jiném systému lokality. Soubor řešení v izolovaném prostoru služby SharePoint můžete také publikovat na místní web služby SharePoint, ale bez ohledu na to, zda je web publikovány do místního nebo vzdáleného, se nedají konfigurovat z kroků nasazení.  
  
 *Upgrade* odkazuje na aktualizace stávající vzdáleně nebo místně publikované řešení služby SharePoint. Po provedení změn jakékoli řešení služby SharePoint v sadě Visual Studio, můžete změnit název souboru balíčku na řešení, znovu publikovat řešení a pak upgradovat řešení po jeho úspěšně znovu publikuje uzamkl. Pokud jste znovu publikovat místně publikované řešení, můžete přepsat existující soubor řešení.  
  
## <a name="deploy-packages"></a>Nasazení balíčků
 Soubory balíčku na serveru SharePoint můžete nasadit ve svém vývojovém počítači pro testování a ladění. Můžete také vytvořit soubor balíčku, který můžete nainstalovat na jiném počítači tak, že zvolíte **publikovat do systému souborů** přepínač ve **publikovat** dialogové okno. Balíček je vytvořili a zkopírovali do Zadaná místní cesta k souboru. Chcete-li nasadit řešení služby SharePoint na místním serveru, použijte **nasadit** příkazu na **sestavení** nabídky. Další informace najdete v tématu [postupy: nasazení a publikování řešení služby SharePoint na místní web služby SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Další informace o nasazení definice seznamu, přidejte příjemce událostí a použít funkci Designer a návrháře balíčků naleznete v tématu [návod: nasazení definice seznamu úkolů projektu](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## <a name="customize-the-deployment-process"></a>Přizpůsobení procesu nasazení
 V následující tabulce jsou uvedeny dvě nasazení konfigurace, které můžete použít při ladění a nasazování řešení služby SharePoint.  
  
|Konfigurace nasazení|Popis|  
|------------------------------|-----------------|  
|Výchozí|Výchozí konfigurace nasazení. Následující kroky nasazení jsou prováděny:<br /><br /> 1.  Spusťte příkaz před nasazením.<br />2.  Recyklujte fond aplikací služby IIS.<br />3.  Odvolat řešení.<br />4.  Přidáte řešení.<br />5.  Aktivace funkce.<br />6.  Spusťte příkaz po nasazení.<br /><br /> Při odinstalaci balíčku, jsou provést následující kroky odvolání.<br /><br /> 1.  Recyklujte fond aplikací služby IIS.<br />2.  Odvolat řešení.|  
|Žádné aktivační|Tuto konfiguraci nasazení spustí stejný postup jako výchozí konfiguraci, ale přeskočí krok aktivace.|  
  
 Můžete vytvořit vlastní konfigurace nasazení dokončit jeden krok nebo změnit pořadí kroků v procesu nasazení. Další informace najdete v tématu [postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  

 Můžete také přidat příkazy, pomocí před a po nasazení. Další informace najdete v tématu [postupy: nastavení SharePoint – příkazy nasazení](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## <a name="publish-packages-to-a-remote-or-local-server"></a>Publikování balíčků vzdáleného nebo místního serveru
 Publikovat v izolovaném prostoru řešení služby SharePoint na vzdáleném serveru, na panelu nabídek vyberte **sestavení**, **publikovat**a pak na **publikovat** dialogovém okně vyberte **Publikovat na webu služby SharePoint** přepínač poskytuje URL vzdáleného serveru, jako například **https://someremoteserver.sharepoint.microsoftonline.com**.  
  
 K publikování řešení služby SharePoint na místním serveru, v **publikovat** dialogovém okně vyberte **publikovat do systému souborů** přepínač poskytuje na cestu v místním systému.  
  
 Po řešení úspěšně publikuje do služby SharePoint, řešení se zobrazí v **řešení Galerie** kde ji můžete aktivovat. Další informace najdete v tématu [postupy: nasazení, publikování a upgradování řešení služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### <a name="upgrade-published-packages"></a>Balíčky s upgradem publikované
 Pokud provedete změny projektu služby SharePoint v sadě Visual Studio po publikování, je nutné upgradovat zveřejněný balíček zahrnout změny. Chcete-li úspěšně upgradovat balíček musí mít jedinečný název. Pokud balíček se stejným názvem nachází na web služby SharePoint, - kterému může dojít při aktualizaci existující aplikace – chybové oznámení k názvu souboru konfliktu a umožňuje přejmenovat balíčku. Po znovu publikovat nového balíčku se zobrazí na webu služby SharePoint a může být upgradována. Aktualizovaného balíčku aktualizací řešení pomocí dat z starší balíček a potom aktivuje řešení ve službě SharePoint. Další informace najdete v tématu [postupy: nasazení, publikování a upgradování řešení služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Viz také:
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
