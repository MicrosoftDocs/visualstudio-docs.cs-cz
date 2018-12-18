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
ms.openlocfilehash: d89dbc0b752c2b8c538ec53769c166b6edbd802f
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50915137"
---
1. Na vzdáleném počítači, najít a spustit **vzdálený ladicí program** z **Start** nabídky. 
   
   Pokud nemáte oprávnění správce na vzdáleném počítači, klikněte pravým tlačítkem myši **vzdálený ladicí program** aplikaci a vyberte **spustit jako správce**. V opačném případě stačí spusťte normálně.

   Můžou existovat různé verze *msvsmon.exe* v *x64*, *x32*, či v jiných složkách. Ujistěte se, že spustíte verze potřebné k ladění aplikace. 
   
1. Při prvním spuštění vzdáleného ladicího programu (nebo předtím, než jste nakonfigurovali) **konfigurace vzdáleného ladění** zobrazí se dialogové okno.  
  
    ![Konfigurace vzdáleného ladicího programu](../media/remotedebuggerconfwizardpage.png "konfigurace vzdáleného ladicího programu")  
  
1. Pokud rozhraní API webových služeb Windows není nainstalována, který se pouze v systému Windows Server 2008 R2, vyberte **nainstalovat** tlačítko.  
  
1. Vyberte alespoň jeden síťový typ, který chcete použít nástroje remote tools na. Pokud jsou počítače připojené do domény, je třeba zvolit první položku. Pokud jsou tyto počítače připojeny přes domácí nebo pracovní skupině, vyberte druhý nebo třetí položka podle potřeby.  
  
1. Vyberte **konfigurovat vzdálené ladění** nakonfigurovat bránu firewall a spustit vzdálený ladicí program.  
  
1. Po dokončení konfigurace **vzdálený ladicí program** zobrazí se okno.
  
    ![Vzdálený ladicí program okno](../media/remotedebuggerwindow.png "okna vzdáleného ladicího programu")
  
    Vzdálený ladicí program je nyní čeká na připojení. Použijte název serveru a port číslo zobrazené nastavit konfiguraci vzdáleného připojení v sadě Visual Studio.  
  
Chcete-li zastavit vzdáleného ladicího programu, vyberte **souboru** > **ukončovací**. Můžete restartovat z **Start** nabídky, nebo z příkazového řádku:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
