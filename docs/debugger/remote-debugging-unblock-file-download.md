---
title: Odblokovat stahování vzdálených nástrojů
description: Odblokuje stahování nástrojů Remote Tools v systému Windows Server, což může být časově náročné kvůli výchozímu nastavení zabezpečení IE.
ms.custom: SEO-VS-2020
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffefa70c59658382073a10db8ae1832b0d9b03c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934556"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Postupy: odblokování stahování nástrojů Remote Tools na Windows serveru

Výchozím nastavením zabezpečení v aplikaci Internet Explorer na Windows serveru může být časově náročné stahovat součásti, jako jsou třeba vzdálené nástroje.

* Konfigurace rozšířeného zabezpečení je povolena v aplikaci Internet Explorer, která zabraňuje otevření webů a přístupu k webovým prostředkům, pokud není doména obsahující prostředek výslovně povolená (tj. důvěryhodná). I když toto nastavení můžete zakázat, nedoporučujeme ho, protože může představovat bezpečnostní riziko.

* V systému Windows Server 2016 je ve výchozím nastavení na webu **Možnosti Internetu**  >    >    >    >  **soubory ke stažení** na vlastní úrovni internetu také zakázáno stahování souborů. Pokud se rozhodnete stáhnout vzdálené nástroje přímo na Windows serveru, musíte povolit stahování souborů.

Pro stažení nástrojů na Windows Server doporučujeme jednu z následujících akcí:

* Stáhněte si nástroje Remote Tools na jiný počítač, jako je třeba aplikace se sadou Visual Studio, a pak zkopírujte soubor *. exe* do Windows serveru.

* Spusťte vzdálený ladicí program [ze sdílené složky](../debugger/remote-debugging.md#fileshare_msvsmon) na počítači se systémem Visual Studio.

* Stáhněte si nástroje Remote Tools přímo na Windows Server a přijměte výzvy k přidání důvěryhodných lokalit. Moderní weby často obsahují mnoho prostředků třetích stran, což může vést k mnoha výzvám. Také může být nutné přidat všechny přesměrované odkazy ručně. Před zahájením stahování se můžete rozhodnout přidat některé důvěryhodné servery. Přejít na **Možnosti internetu > zabezpečení > důvěryhodné servery > lokality** a přidat následující lokality.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * o: prázdné

  Pro starší verze ladicího programu v my.visualstudio.com přidejte tyto další lokality, abyste se ujistili, že přihlášení proběhlo úspěšně:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Pokud se rozhodnete tyto domény přidat při stahování nástrojů Remote Tools, po zobrazení výzvy zvolte **Přidat** .

    ![Blokovaný obsah – dialogové okno](../debugger/media/remotedbg-blocked-content.png)

    Po stažení softwaru získáte další požadavky na udělení oprávnění k načtení různých skriptů a prostředků webu. Na my.visualstudio.com doporučujeme přidat další domény, abyste se ujistili, že přihlášení bylo úspěšné.