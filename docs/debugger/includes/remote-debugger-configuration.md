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
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312094"
---
1. Ve vzdáleném počítači Najděte a spusťte **vzdálený ladicí program** z nabídky **Start** . 
   
   Pokud nemáte oprávnění správce na vzdáleném počítači, klikněte pravým tlačítkem na aplikaci **vzdáleného ladicího programu** a vyberte **Spustit jako správce**. Jinak ho stačí spustit normálně.

   Pokud plánujete připojení k procesu, který je spuštěný jako správce nebo je spuštěný pod jiným uživatelským účtem (například IIS), klikněte pravým tlačítkem na aplikaci **vzdáleného ladicího programu** a vyberte **Spustit jako správce**. Další informace najdete v tématu [spuštění vzdáleného ladicího programu jako správce](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. Při prvním spuštění vzdáleného ladicího programu (nebo před jeho nakonfigurováním) se zobrazí dialogové okno **Konfigurace vzdáleného ladění** .  
  
    ![Konfigurace vzdáleného ladicího programu](../media/remotedebuggerconfwizardpage.png "Konfigurace vzdáleného ladicího programu")  
  
1. Pokud není nainstalované rozhraní API webových služeb systému Windows, které se stane pouze v systému Windows Server 2008 R2, vyberte tlačítko **instalovat** .  
  
1. Vyberte alespoň jeden typ sítě, na kterém chcete používat nástroje Remote Tools. Pokud jsou počítače připojené přes doménu, musíte zvolit první položku. Pokud jsou počítače připojené přes pracovní skupinu nebo domácí skupinu, podle potřeby vyberte druhou nebo třetí položku.  
  
1. Vyberte **Konfigurovat vzdálené ladění** a nakonfigurujte bránu firewall a spusťte vzdálený ladicí program.  
  
1. Po dokončení konfigurace se zobrazí okno **vzdáleného ladicího programu** .
  
    ![Okno vzdáleného ladicího programu](../media/remotedebuggerwindow.png "Okno vzdáleného ladicího programu")
  
    Vzdálený ladicí program nyní čeká na připojení. Použijte název serveru a číslo portu, které se zobrazí, chcete-li nastavit konfiguraci vzdáleného připojení v sadě Visual Studio.  
  
Pokud chcete zastavit vzdálený ladicí program, vyberte **soubor**  >  **ukončit**. Můžete ji restartovat z nabídky **Start** nebo z příkazového řádku:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
