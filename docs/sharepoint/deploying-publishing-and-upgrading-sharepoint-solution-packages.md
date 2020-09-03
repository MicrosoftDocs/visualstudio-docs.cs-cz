---
title: Nasazení, publikování & upgradu balíčků řešení služby SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444967"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Nasazení, publikování a Upgrade balíčků řešení služby SharePoint
  Po vývoji řešení služby SharePoint v aplikaci Visual Studio můžete buď nasadit soubor balíčku (. wsp) na místní server SharePoint nebo ho publikovat na vzdáleném nebo místním serveru SharePoint. Pokud soubory nasadíte, můžete přizpůsobit způsob nasazení souborů balíčku (. wsp).

> [!NOTE]
> V současné době je možné publikovat pouze řešení v izolovaném prostoru (sandbox) na vzdálených serverech SharePoint. Další informace najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Nasazení, publikování a upgrade
 *Nasazení* odkazuje na kopírování souboru řešení služby SharePoint sestaveného z projektu služby SharePoint v aplikaci Visual Studio na místního hostitele. V nasazeném řešení můžete nakonfigurovat kroky nasazení, například recyklovat fond Internetová informační služba (IIS), aktivovat řešení po nasazení a tak dále. K nasazení použijte příkaz **nasadit** v nabídce **sestavení** . Další informace naleznete v tématu [Postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) a [Postup: nasazení a publikování řešení služby SharePoint na místní web služby SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Publikování* odkazuje na nahrání souboru řešení služby SharePoint v izolovaném prostoru na vzdálený web služby SharePoint. To znamená web umístěný v jiném systému. Soubor řešení v izolovaném prostoru (sandbox) můžete také publikovat na místní SharePointový web, ale bez ohledu na to, jestli je web publikovaný na místní nebo vzdálený, nemůžete nakonfigurovat jeho kroky nasazení.

 *Upgrade* odkazuje na aktualizaci stávajícího nebo místně publikovaného řešení SharePointu. Po provedení jakýchkoli změn v řešení služby SharePoint v aplikaci Visual Studio změníte název souboru balíčku řešení, znovu publikujete řešení a potom po úspěšném opětovném publikování řešení provedete upgrade. Pokud publikujete místně publikované řešení znovu, můžete přepsat existující soubor řešení.

## <a name="deploy-packages"></a>Nasadit balíčky
 Soubory balíčku můžete nasadit na server služby SharePoint ve vývojovém počítači pro účely testování a ladění. Soubor balíčku, který můžete nainstalovat na jiný počítač, můžete také vytvořit tak, že v dialogovém okně **publikovat** kliknete na tlačítko možnosti **publikovat do systému souborů** . Balíček je vytvořen a zkopírován do zadané místní cesty k souboru. K nasazení řešení služby SharePoint na místní server použijte příkaz **nasadit** v nabídce **sestavení** . Další informace najdete v tématu [Postup: nasazení a publikování řešení služby SharePoint na místním webu služby SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Chcete-li se dozvědět, jak nasadit definici seznamu, přidat přijímač událostí a použít návrháře funkcí a návrháře balíčků, přečtěte si [Návod: nasazení definice seznamu úkolů projektu](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Přizpůsobení procesu nasazení
 V následující tabulce jsou uvedeny dvě konfigurace nasazení, které můžete použít při ladění a nasazení řešení služby SharePoint.

|Konfigurace nasazení|Popis|
|------------------------------|-----------------|
|Výchozí|Výchozí konfigurace nasazení. Provádí se následující kroky nasazení:<br /><br /> 1. Spusťte příkaz před nasazením.<br />2. recykluje fond aplikací IIS.<br />3. Odvolejte řešení.<br />4. Přidejte řešení.<br />5. Aktivujte funkce.<br />6. Spusťte příkaz po nasazení.<br /><br /> Při odinstalaci balíčku se provede následující kroky odvolání.<br /><br /> 1. recyklovat fond aplikací IIS.<br />2. Odvolejte řešení.|
|Bez aktivace|Tato konfigurace nasazení používá stejný postup jako výchozí konfigurace, ale přeskočí krok aktivace.|

 Můžete vytvořit vlastní konfigurace nasazení a provést jeden krok nebo změnit pořadí kroků v procesu nasazení. Další informace najdete v tématu [Postupy: Úprava konfigurace nasazení služby SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Můžete také přidat příkazy, které se spustí před a po nasazení. Další informace najdete v tématu [Postup: nastavení příkazů nasazení služby SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publikování balíčků na vzdáleném nebo místním serveru
 Chcete-li publikovat řešení služby SharePoint v izolovaném prostoru na vzdáleném serveru, v panelu nabídek zvolte možnost **sestavení**, **publikování**a potom v dialogovém okně **publikovat** zvolte možnost **publikovat na webu služby SharePoint** a zadejte adresu URL vzdáleného serveru, například `https://someremoteserver.sharepoint.microsoftonline.com` .

 Chcete-li publikovat řešení služby SharePoint na místním serveru, klikněte v dialogovém okně **publikovat** na přepínač **publikovat do systému souborů** a zadejte cestu k místnímu systému.

 Po úspěšném publikování řešení na SharePoint se toto řešení zobrazí v **Galerii řešení** , kde ji můžete aktivovat. Další informace najdete v tématu [Postup: nasazení, publikování a upgrade řešení služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Upgradovat publikované balíčky
 Pokud provedete změny v projektu služby SharePoint v aplikaci Visual Studio po jejím publikování, publikovaný balíček musí být upgradován, aby obsahoval změny. Aby bylo možné úspěšně upgradovat, musí mít balíček jedinečný název. Pokud se na webu služby SharePoint nachází balíček se stejným názvem, ke kterému může dojít při aktualizaci existující aplikace – dojde k chybě, která vás upozorní na konflikt názvů souborů a umožňuje přejmenovat balíček. Po opětovném publikování se nový balíček zobrazí na webu služby SharePoint a lze jej upgradovat. Upgradovaný balíček aktualizuje řešení pomocí dat ze staršího balíčku a pak toto řešení aktivuje na SharePointu. Další informace najdete v tématu [Postup: nasazení, publikování a upgrade řešení služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
