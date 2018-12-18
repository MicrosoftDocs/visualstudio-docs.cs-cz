---
title: 'Chyba: Nemáte oprávnění ke kontrole proces&#39;s identity | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f37cf6f6a1a72435b549942fa03d821c900718a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472023"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Chyba: Nemáte oprávnění ke kontrole proces&#39;s identity
Nemáte oprávnění ke kontrole identity procesu. To může být způsobeno konfiguraci vašeho systému.  
  
 Ladicí program nemohl ke kontrole identity procesu, což je potřebné informace pro ladění. Nejpravděpodobnější příčinou je zakázaná Terminálové služby. Ve výchozím nastavení je povolena služba Terminálové služby. Postupujte podle těchto kroků můžete znovu povolit.  
  
### <a name="to-enable-terminal-services"></a>Chcete-li povolit Terminálové služby  
  
1.  Klikněte na tlačítko **spustit** a potom zvolte **ovládací panely**.  
  
2.  V Ovládacích panelech vyberte **přepnout do klasického zobrazení**, v případě potřeby a potom dvakrát klikněte na **nástroje pro správu**.  
  
3.  V **nástroje pro správu** okna, klikněte dvakrát na **Správa počítače**.  
  
4.  V okně Správa počítače, rozbalte **služeb a aplikací** uzlu.  
  
5.  V části **služeb a aplikací**, klikněte na tlačítko **služby**.  
  
     V pravém podokně se zobrazí seznam služeb.  
  
6.  V **služby** seznamu, klikněte pravým tlačítkem na **Terminálové služby** a potom zvolte **vlastnosti**.  
  
7.  V **Terminálové služby vlastnosti** okno, přejděte na **Obecné** kartě a nastavte **typ spuštění** k **ruční**.  
  
8.  Click **OK**.  
  
9. Restartujte počítač.  
  
     Tento postup nepovolí automaticky vzdálené plochy. Pokud chcete povolit vzdálené plochy ve vašem počítači, proveďte následující další postup.  
  
### <a name="to-enable-remote-desktop"></a>Chcete-li povolit vzdálená plocha  
  
1.  Klikněte na tlačítko **spustit** a potom klikněte pravým tlačítkem na **Můj počítač**.  
  
2.  Zvolte **vlastnosti**.  
  
     **Vlastnosti systému** zobrazí se okno.  
  
3.  Klikněte na tlačítko **vzdáleného**.  
  
4.  V části **vzdálené plochy**, vyberte **povolit uživatelům vzdálené připojení k tomuto počítači**.  
  
5.  Click **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění chyby a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)