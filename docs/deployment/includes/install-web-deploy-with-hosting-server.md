---
ms.openlocfilehash: 1e6c6714720d652fff266e3e852d01982c98e34a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173871"
---
Nasazení webu 3,6 pro hostitelské servery poskytuje další konfigurační funkce, které umožňují vytvořit soubor nastavení publikování z uživatelského rozhraní.

1. Pokud již máte v systému Windows Server nainstalované nasazení webu 3,6, odinstalujte ji pomocí **ovládacího panelu**  >  **programy**  >  **Odinstalovat program**.

2. Dále nainstalujte Nasazení webu 3,6 pro hostitelské servery na Windows serveru.

    Chcete-li nainstalovat Nasazení webu pro hostitelské servery, použijte instalační program webové platformy (WebPI). (Pokud chcete najít odkaz instalace webové platformy ze služby IIS, vyberte **IIS** v levém podokně Správce serveru. V podokně Server klikněte pravým tlačítkem na server a vyberte **Správce služby Internetová informační služba (IIS)**. Pak použijte odkaz **získat nové součásti webové platformy** v okně **Akce** .) Můžete také získat instalační program webové platformy (WebPI) ze [souborů ke stažení](https://www.microsoft.com/web/downloads/platform.aspx).

    V instalačním programu webové platformy najdete na kartě aplikace **Nasazení webu 3,6 pro hostitelské servery** .

3. Pokud jste ještě nenainstalovali **skripty a nástroje správy služby IIS**, nainstalujte je nyní.

    Přejděte na **Vybrat**  >  Nástroje pro správu**webového serveru (IIS)** a  >  **Management Tools**pak vyberte role **skripty a nástroje správy služby IIS** , klikněte na **Další**a pak nainstalujte roli.

    ![Nainstalovat skripty a nástroje správy služby IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Aby bylo možné povolit generování souboru nastavení publikování, jsou skripty a nástroje nutné.

4. Volitelné Ověřte, zda je Nasazení webu spuštěn správně. Otevřete **ovládací Panel > systém a zabezpečení > nástroje pro správu > služby** a ujistěte se, že je spuštěna **Webová Deployment Agent služba** (název služby se liší ve starších verzích).

    Pokud služba agenta není spuštěná, spusťte ji. Pokud není vůbec k dispozici, přečtěte si v **Ovládacích panelech > programy > odinstalace programu**, vyhledejte **Microsoft \<version> nasazení webu **. Vyberte **změnu** instalace a ujistěte se, že jste zvolili instalaci **na místní pevný disk** pro součásti nasazení webu. Dokončete postup změny instalace.