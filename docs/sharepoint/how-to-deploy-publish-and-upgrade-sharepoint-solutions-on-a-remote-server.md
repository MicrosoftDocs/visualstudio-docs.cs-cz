---
title: Vzdálená nasazení, publikování & upgrade řešení SharePoint
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5de5128ff19472390e65aa5d9a437aee269ff897
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585781"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>Postupy: nasazení, publikování a upgrade řešení služby SharePoint na vzdáleném serveru
  Kromě nasazení řešení služby SharePoint do místního systému můžete publikovat řešení služby SharePoint v izolovaném prostoru na vzdálené weby nebo místní weby služby SharePoint. Proces vzdáleného publikování kopíruje soubor *. wsp* na server SharePoint, nainstaluje řešení a pak vám umožní toto řešení aktivovat. Můžete také upgradovat vzdálenou instalaci řešení SharePoint po provedení změn.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>Publikování řešení služby SharePoint v izolovaném prostoru na vzdáleném serveru SharePoint

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt služby SharePoint v izolovaném prostoru, který chcete publikovat, a pak zvolte **publikovat**.

2. V dialogovém okně **publikovat** zvolte možnost **publikovat na webu služby SharePoint** a potom zadejte adresu URL webu pro publikování online, například: `https://mytestsite.sharepoint.microsoftonline.com` .

3. Po publikování kliknutím na tlačítko **otevřít v prohlížeči otevřete stránku Galerie** řešení, kde můžete zobrazit seznam řešení na stránce **Galerie řešení** .

4. Klikněte na tlačítko **publikovat** .

5. Pokud se vyžaduje ověření uživatele, přihlaste se ke vzdálenému serveru.

     Průběh publikování se zobrazí v okně **výstupu** sady Visual Studio. Po dokončení procesu se na vzdáleném serveru SharePoint nainstaluje soubor řešení (*. wsp*). Musí se ale ještě aktivovat předtím, než se bude moct použít na SharePointu.

6. Na stránce **Galerie řešení** vyberte aplikaci SharePoint a pak na pásu karet klikněte na tlačítko **aktivovat** .

7. V dialogovém okně **aktivovat řešení** na pásu karet znovu klikněte na tlačítko **aktivovat** .

     Sloupec **stav** na stránce **Galerie řešení** indikuje, že je aplikace aktivní.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>Upgrade řešení služby SharePoint v izolovaném prostoru na vzdáleném serveru SharePoint
 Pokud je řešení SharePointu v izolovaném prostoru již Publikováno na vzdáleném serveru, následující postup vám umožní provést upgrade po provedení změn aplikace v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Přejmenujte balíček služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . To provedete tak, že v **Průzkumník řešení** otevřete balíček. Zobrazí se v **Průzkumníkovi balíčku**.

2. V **Průzkumníku balíčků**v poli **název** změňte název balíčku na jedinečný název.

3. Uložte projekt.

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **publikovat**.

5. V dialogovém okně **publikovat** zvolte možnost **publikovat na webu služby SharePoint** a potom v případě, že chybí adresa URL vzdáleného serveru, na kterém je řešení uloženo, zadejte.

6. Po publikování kliknutím na tlačítko **otevřít v prohlížeči otevřete stránku Galerie** řešení, kde můžete zobrazit seznam řešení na stránce **Galerie řešení** .

7. Klikněte na tlačítko **publikovat** .

8. Pokud se vyžaduje ověření uživatele, přihlaste se ke vzdálenému serveru.

     Pokud jste se v nedávné době přihlásili ke vzdálenému serveru, nemusí se ověřování vyžadovat.

     Pokud na serveru SharePoint stále existuje starší verze aplikace, která má stejný název, zobrazí se chyba, že na serveru SharePoint již existuje balíček se stejným názvem. Před publikováním musíte balíček přejmenovat na jedinečný název.

9. Zvolte novou aplikaci v SharePointu a pak na pásu karet klikněte na tlačítko **upgradovat** .

10. V dialogovém okně **řešení upgradu** na pásu karet znovu klikněte na tlačítko **upgradovat** . Sloupec **stav** na stránce **Galerie řešení** by nyní měl označovat, že je aplikace aktivní.

     Stará verze řešení se deaktivuje. nová verze řešení se upgraduje s daty udržovanými ze starého řešení a nové řešení se aktivuje na SharePointu.

## <a name="see-also"></a>Viz také
- [Postupy: nasazení a publikování řešení služby SharePoint na místní web služby SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [Vytváření balíčků řešení služby SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Postupy: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Postupy: Přidání a odebrání funkcí a položek do balíčku pomocí návrháře balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
