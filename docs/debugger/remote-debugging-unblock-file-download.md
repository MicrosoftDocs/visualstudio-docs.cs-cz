---
title: Odblokovat vzdálené nástroje pro stažení
ms.custom: ''
ms.date: 07/19/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0586b8f0699ec2eca5843d59df1b6ddd7cecbd3
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180715"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Postupy: odblokovat stáhnout nástroje remote tools v systému Windows Server

Výchozí nastavení zabezpečení v aplikaci Internet Explorer ve Windows serveru může být časově náročné ke stažení komponenty, například nástroje remote tools.

* Je povoleno rozšířené nastavení zabezpečení v Internet Exploreru, což brání websites otevírání a zpřístupňování webových prostředků, pokud nejsou explicitně povolená na doménu obsahující zdroj (to znamená, důvěryhodná). I když můžete toto nastavení zakážete, nedoporučujeme ji protože to může představovat bezpečnostní riziko.

* V systému Windows Server 2016, výchozí nastavení **Možnosti Internetu** > **zabezpečení** > **Internet**  >   **Vlastní úroveň** > **stáhne** také zakáže stahování souborů. Pokud chcete stáhnout remote tools přímo v systému Windows Server, je nutné povolit stahování souborů.

Pokud chcete stáhnout nástroje pro Windows Server, doporučujeme jednu z následujících akcí:

* Stáhnout nástroje remote tools na jiném počítači, jako je například jeden spuštěné Visual Studio a zkopírujte *.exe* soubor do systému Windows Server.

* Spustit vzdálený ladicí program [ze sdílené složky](../debugger/remote-debugging.md#fileshare_msvsmon) na svém počítači Visual Studio.

* Stáhnout nástroje pro vzdálenou přímo v systému Windows Server a přijímal výzvy k přidání důvěryhodných serverů. Moderní weby často zahrnují mnoho materiály třetích stran tak může dojít k mnoha výzvy. Kromě toho přesměrovaného odkazy muset přidat ručně. Můžete nastavit některé z důvěryhodných lokalit přidat před zahájením stahování. Přejděte na **Možnosti Internetu > zabezpečení > Důvěryhodné servery > servery** a přidejte následující weby.

  * VisualStudio.microsoft.com
  * download.visualstudio.microsoft.com
  * o: prázdné

  Pro starší verze ladicího programu na my.visualstudio.com přidejte tyto další lokality, abyste měli jistotu, že je tento přihlášení úspěšné:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * My.VisualStudio.com
  * login.microsoftonline.com
  * Login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * MSFT.STS.microsoft.com
  * auth.gfx.MS
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * Query.prod.CMS.RT.microsoft.com

    Pokud budete chtít přidat tyto domény při stahování nástroje remote tools a pak zvolte **přidat** po zobrazení výzvy.

    ![Dialogové okno o blokovaném obsahu pole](../debugger/media/remotedbg-blocked-content.png)

    Když si stáhnete software, získat některé další požadavky pro udělení oprávnění k načítání různých skriptů na webu a prostředky. Na my.visualstudio.com doporučujeme vám, že přidáte další domény, abyste měli jistotu, že je tento přihlášení úspěšné.