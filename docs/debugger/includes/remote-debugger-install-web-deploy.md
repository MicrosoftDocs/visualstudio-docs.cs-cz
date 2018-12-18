---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811914"
---
1. Pokud máte v úmyslu nasadit vaše aplikace s nasazením webu v sadě Visual Studio, nainstalujte nejnovější verzi nástroje nasazení webu na serveru.

    Chcete-li nainstalujte nástroj nasazení webu, použijte [instalačního programu webové platformy (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Chcete-li najít odkaz na Web Platform Installer ze služby IIS, vyberte **IIS** v levém podokně Správce serveru. Klikněte pravým tlačítkem na server a vyberte **Správce Internetové informační služby (IIS)**.)

    Instalace webové platformy najdete v kartě aplikace Webdeploy. Můžete také získat instalační program přímo z [Microsoft Download Center](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc). 

2. Ověřte, že nasazení webu běží správně tak, že otevřete **ovládací panely > systém a zabezpečení > Nástroje pro správu > služby** a ujistěte se, že **webová služba agenta nasazení** běží () název služby se liší ve starších verzích).

    Pokud služba agent není spuštěna, spusťte ji. Pokud není k dispozici na všech, přejděte na **ovládací panely > programy > odinstalovat program**, Najít **Microsoft Web Deploy <version>** . Zvolit **změnu** instalace a ujistěte se, že jste zvolili **se nainstaluje na místní pevný disk** pro součásti nasazení webu. Dokončete instalaci změnit.