---
title: Procházení připojení služby SharePoint pomocí Průzkumníka serveru | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e897469eee33a1e4ee48b9096714b4213c099a8f
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325992"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Procházení připojení služby SharePoint pomocí Průzkumníka serveru
  Nyní je možné procházet místní připojení služby SharePoint v **Průzkumníka serveru**. Pomocí tohoto postupu lze procházet součástí webu služby SharePoint ve vašem systému. Součástí webu SharePoint, např. seznam definic a typy obsahu, se zobrazí v uzlu, který je pojmenován **připojení služby SharePoint** v zobrazení stromu **Průzkumníka serveru**. Chcete-li zobrazit **Průzkumníka serveru**, na řádku nabídek zvolte **zobrazení** > **Průzkumníka serveru**. Kromě zobrazení lokality součásti služby SharePoint, můžete odebrat položky, zobrazit jejich vlastnosti nebo aktualizujte zobrazení stromu pomocí příkazů v místní nabídce.  
  
> [!IMPORTANT]  
>  Procházet web služby SharePoint, musíte být správce kolekce webů služby SharePoint a spuštění sady Visual Studio jako správce místního počítače. Jinak, server se zobrazí v **Průzkumníka serveru**, ale nelze rozbalit její uzel. Pokud chcete ověřit, zda jste přihlášeni jako správce kolekce webů, otevřete web ve webovém prohlížeči, otevřete **Akce webu** nabídce zvolte **oprávnění lokality**a pak klikněte na **oprávnění: Team Lokality** vyberte **správci kolekce webů** příkaz **spravovat** skupinu na pásu karet. Název se zobrazí v textovém poli, pokud jste správce kolekce webů. Pokud **správci kolekce webů** příkaz nezobrazí ve skupině spravovat na pásu karet, nejsou správce kolekce webů a je nutné získat od správce webu příslušná oprávnění.  
  
## <a name="server-explorer-nodes"></a>Uzly Průzkumníka serveru
 Všechny komponenty webu služby SharePoint je reprezentována uzel v **Průzkumníka serveru** stromové zobrazení pod **připojení služby SharePoint**. Výchozí weby služby SharePoint příklady obsahu typu s názvem diskuse, která představuje diskusní typ, který se zobrazí v **diskusí** stránce webu služby SharePoint. Typ obsahu diskusní obsahuje několik polí. K zobrazení těchto polí v **Průzkumníka serveru**, rozbalte **ContentTypes** uzel a potom **diskusní** uzlu. V části jsou několik uzlů pole, jako je například textu, diskusní předmět a název.  
  
## <a name="node-shortcut-menu-commands"></a>Příkazy nabídky zástupce uzlu
 Každý uzel má místní nabídky, ke kterým přístup tak, že kliknete pravým tlačítkem na uzel nebo výběr ho a pak vyberete **Shift**+**F10** klíče. Příkazy uzlu může zahrnovat následující:  
  
|Název příkazu|Popis|  
|------------------|-----------------|  
|Aktualizace|Aktualizuje stromovém zobrazení zobrazit všechny změny, které může došlo od doby poslední uzel zobrazila.|  
|Odstranit|Odebere vybraný uzel stromovém zobrazení. **Poznámka:** tento příkaz je povolen pouze na uvedené v části připojení služby SharePoint **připojení služby SharePoint** uzlu.|  
|Vlastnosti|Zobrazí dostupné vlastnosti pro vybraný uzel v **vlastnosti** okno. Vlastnosti jsou všechny jen pro čtení, a ne každý uzel má vlastnosti, které jsou s ním spojená.|  
|Přidat připojení|Umožňuje zadat web služby SharePoint, kterou chcete procházet. K dispozici na **připojení služby SharePoint** uzlů a uzly dílčí lokality.|  
|Zobrazit v prohlížeči|Zobrazí vybraný seznam ve webovém prohlížeči. Tento příkaz je k dispozici na některé seznamy v části **uvádí** uzel, který je součástí **seznamy a knihovny**.|  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Přidání nebo odebrání připojení služby SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Popisuje kroky, které jsou požadovány pro přidání nového serveru SharePoint na **připojení služby SharePoint** uzlu v **Průzkumníka serveru**.|  
  
## <a name="see-also"></a>Viz také:
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
