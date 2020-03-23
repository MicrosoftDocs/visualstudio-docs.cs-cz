---
ms.openlocfilehash: 0fc18fab56f5b46ef097cdf699e4f0569dc190c9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143529"
---
Nasazení webu 3.6 pro hostitelské servery poskytuje další konfigurační funkce, které umožňují vytvoření souboru nastavení publikování z uživatelského prostředí.

1. Pokud je v systému Windows Server již nainstalovánweb Deploy 3.6, odinstalujte jej pomocí **Ovládacích panelů** > **Programy** > **Odinstalujte program**.

2. Dále nainstalujte web deploy 3.6 pro hostování serverů v systému Windows Server.

    Chcete-li nainstalovat nasazení webu pro hostitelské servery, použijte [Instalační službu webové platformy (WebPI).](https://www.microsoft.com/web/downloads/platform.aspx) (Chcete-li najít odkaz Instalační služby webové platformy ze služby IIS, vyberte **službu IIS** v levém podokně Správce serveru. Klepněte pravým tlačítkem myši na server a vyberte **správce Internetové informační služby (IIS).**

    V Instalační službě webové platformy najdete na kartě Aplikace **web deploy for hosting servers.**

3. Pokud jste ještě nenainstalovali **skripty a nástroje služby IIS pro správu,** nainstalujte je nyní.

    Přejděte na **Vyberte** > **nástroje pro správu****webového serveru (IIS)** > a vyberte roli **Skripty a nástroje pro správu služby IIS,** klepněte na tlačítko **Další**a nainstalujte roli.

    ![Instalace skriptů a nástrojů pro správu služby IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Skripty a nástroje jsou nutné k povolení generování souboru nastavení publikování.

4. (Nepovinné) Ověřte, zda je nasazení webu správně spuštěno otevřením **Ovládacích panelů > nástroje pro správu systému a zabezpečení > nástroje pro správu > služby** a ujistěte se, že je **spuštěna služba Agent Service pro nasazení webu** (název služby se liší ve starších verzích).

    Pokud služba agenta není spuštěna, spusťte ji. Pokud není k dispozici vůbec, přejděte do **Ovládacích panelů > Programy > Odinstalovat program**, **vyhledejte verzi aplikace Microsoft Web \<Deploy>**. **Zvolte, zda chcete změnit** instalaci a ujistěte se, že zvolíte Bude nainstalován na místní pevný **disk** pro součásti nasazení webu. Dokončete kroky instalace změny.