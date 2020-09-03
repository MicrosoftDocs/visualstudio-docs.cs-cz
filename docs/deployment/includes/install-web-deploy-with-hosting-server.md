---
ms.openlocfilehash: a292b37a50bbf667fa5b23f18879cd79c3f76805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85292090"
---
Nasazení webu 3,6 pro hostitelské servery poskytuje další konfigurační funkce, které umožňují vytvořit soubor nastavení publikování z uživatelského rozhraní.

1. Pokud jste už nasazení webu v systému Windows Server nainstalovali, odinstalujte ji pomocí **ovládacího panelu**  >  **programy**  >  **Odinstalovat program**.

2. Dále nainstalujte Nasazení webu 3,6 pro hostitelské servery na Windows serveru.

    Chcete-li nainstalovat Nasazení webu pro hostitelské servery, použijte instalační program webové platformy (WebPI). (Pokud chcete najít odkaz instalace webové platformy ze služby IIS, vyberte **IIS** v levém podokně Správce serveru. V podokně Server klikněte pravým tlačítkem na server a vyberte **Správce služby Internetová informační služba (IIS)**. Pak použijte odkaz **získat nové součásti webové platformy** v okně **Akce** .) Můžete také získat instalační program webové platformy (WebPI) ze [souborů ke stažení](https://www.microsoft.com/web/downloads/platform.aspx).

    V instalačním programu webové platformy najdete na kartě aplikace **Nasazení webu 3,6 pro hostitelské servery** .

3. Pokud jste ještě nenainstalovali **skripty a nástroje správy služby IIS**, nainstalujte je nyní.

    Přejděte na **Vybrat**  >  Nástroje pro správu**webového serveru (IIS)** a  >  **Management Tools**pak vyberte role **skripty a nástroje správy služby IIS** , klikněte na **Další**a pak nainstalujte roli.

    ![Nainstalovat skripty a nástroje správy služby IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Aby bylo možné povolit generování souboru nastavení publikování, jsou skripty a nástroje nutné.

4. Volitelné Ověřte, zda Nasazení webu pracuje správně. Otevřete  **ovládací Panel > systém a zabezpečení > nástroje pro správu > služby**a pak se ujistěte, že:

    * **Služba webové Deployment Agent** je spuštěna (název služby se liší ve starších verzích).

    * **Služba webové správy** je spuštěná.

    Pokud není spuštěna jedna ze služeb agenta, restartujte **službu Web Deployment Agent**.

    Pokud služba Web Deployment Agent vůbec není přítomna, přečtěte si v části **Ovládací panely > programy > odinstalace programu**, najděte **nasazení webu \<version> Microsoft **. Vyberte **změnu** instalace a ujistěte se, že jste zvolili instalaci  **na místní pevný disk** pro součásti nasazení webu. Dokončete postup změny instalace.