---
title: Nasazení, publikování & upgradu balíčků řešení SharePointu
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444967"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Nasazení, publikování a upgrade balíčků řešení SharePointu
  Po vývoji řešení SharePoint u Sady Visual Studio můžete buď nasadit jeho soubor balíčku (.wsp) na místní sharepointový server, nebo ho publikovat na vzdáleném nebo místním sharepointovém serveru. Pokud nasadíte soubory, můžete přizpůsobit, jak jsou nasazeny soubory balíčku (.wsp).

> [!NOTE]
> V současné době lze na vzdálených serverech SharePoint publikovat pouze řešení v izolovaném prostoru. Další informace naleznete v [tématu Sandboxed řešení aspekty](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Nasazení, publikování a upgrade
 *Nasazení* znamená kopírování sharepointového souboru řešení vytvořeného z projektu SharePointu ve Visual Studiu místnímu hostiteli. V nasazeném řešení můžete nakonfigurovat kroky nasazení, jako je recyklace fondu Internetové informační služby (IIS), aktivace řešení po nasazení a tak dále. K nasazení použijte příkaz **Nasadit** v nabídce **Sestavení.** Další informace najdete v [tématu Postup: Úprava konfigurace nasazení SharePointu](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) a [Postup: Nasazení a publikování řešení SharePointu na místní sharepointový web](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Publikování* označuje nahrání souboru řešení SharePoint u izolovaného prostoru na vzdálený sharepointový web. to znamená, že lokalita umístěná v jiném systému. Soubor řešení v izolovaném prostoru služby SharePoint můžete také publikovat na místním webu služby SharePoint, ale bez ohledu na to, zda je web publikovaný na místní nebo vzdálený, nemůžete nakonfigurovat jeho kroky nasazení.

 *Inovace* označuje aktualizaci existujícího vzdáleně nebo místně publikovaného řešení SharePointu. Po provedení všech změn v řešení SharePoint v sadě Visual Studio změníte název souboru balíčku řešení, znovu publikujte řešení a poté upgradujte řešení po úspěšném opětovném publikování. Pokud znovu publikujete místně publikované řešení, můžete přepsat existující soubor řešení.

## <a name="deploy-packages"></a>Nasazení balíčků
 Soubory balíčků můžete nasadit na sharepointový server ve vývojovém počítači pro testování a ladění. Soubor balíčku, který můžete nainstalovat do jiného počítače, můžete také vytvořit výběrem přepínače **Publikovat do systému souborů** v dialogovém okně **Publikovat.** Balíček je vytvořen a zkopírován do zadané cesty k místnímu souboru. Chcete-li nasadit řešení SharePointu na místní server, použijte příkaz **Nasadit** v nabídce **Sestavení.** Další informace najdete v [tématu Postup: Nasazení a publikování řešení SharePointu na místním sharepointovém webu](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Informace o nasazení definice seznamu, přidání příjemce událostí a použití Návrháře funkcí a Návrháře balíčků naleznete [v tématu Návod: Nasazení definice seznamu úkolů projektu](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Přizpůsobení procesu nasazení
 V následující tabulce jsou uvedeny dvě konfigurace nasazení, které můžete použít při ladění a nasazení řešení služby SharePoint.

|Konfigurace nasazení|Popis|
|------------------------------|-----------------|
|Výchozí|Výchozí konfigurace nasazení. Jsou prováděny následující kroky nasazení:<br /><br /> 1. Spusťte příkaz před nasazením.<br />2. Recyklovat fond aplikací služby IIS.<br />3. Zasuňte roztok.<br />4. Přidejte roztok.<br />5. Aktivujte funkce.<br />6. Spusťte příkaz po nasazení.<br /><br /> Při odinstalaci balíčku jsou provedeny následující kroky odvolání.<br /><br /> 1. Recyklovat fond aplikací služby IIS.<br />2. Zasuňte roztok.|
|Žádná aktivace|Tato konfigurace nasazení běží ve stejných krocích jako výchozí konfigurace, ale přeskočí krok aktivace.|

 Můžete vytvořit vlastní konfigurace nasazení k dokončení jednoho kroku nebo změnit pořadí kroků v procesu nasazení. Další informace najdete v [tématu Postup: Úprava konfigurace nasazení sharepointového nasazení](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Můžete také přidat příkazy ke spuštění před a po nasazení. Další informace najdete v [tématu Postup: Nastavení příkazů nasazení služby SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publikování balíčků na vzdálený nebo místní server
 Chcete-li publikovat řešení SharePoint v izolovaném prostoru na vzdáleném serveru, zvolte na řádku nabídek možnost **Sestavit**, **Publikovat**a potom v dialogovém okně `https://someremoteserver.sharepoint.microsoftonline.com` **Publikovat** zvolte přepínač Publikovat na webu **služby SharePoint,** které poskytuje adresu URL vzdáleného serveru, například .

 Chcete-li publikovat řešení služby SharePoint na místním serveru, zvolte v dialogovém okně **Publikovat** možnost **Publikovat do systému souborů** a zadejte místní systémovou cestu.

 Po úspěšném publikování řešení na SharePoint, řešení se zobrazí v **Galerii řešení,** kde jej můžete aktivovat. Další informace naleznete v [tématu Postup: Nasazení, publikování a inovace řešení Služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Upgrade publikovaných balíčků
 Pokud po publikování provedete v sharepointovém projektu nějaké změny, musí být publikovaný balíček upgradován tak, aby zahrnoval změny. Chcete-li úspěšně upgradovat, balíček musí mít jedinečný název. Pokud je na webu služby SharePoint nalezen balíček se stejným názvem , zobrazí se chyba, která vás upozorní na konflikt názvu souboru a umožní vám přejmenovat balíček. Po opětovném publikování se nový balíček zobrazí na webu služby SharePoint a lze jej upgradovat. Upgradovaný balíček aktualizuje řešení pomocí dat ze staršího balíčku a pak aktivuje řešení v SharePointu. Další informace naleznete v [tématu Postup: Nasazení, publikování a inovace řešení Služby SharePoint na vzdáleném serveru](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Viz také
- [Balení a nasazení sharepointových řešení](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
