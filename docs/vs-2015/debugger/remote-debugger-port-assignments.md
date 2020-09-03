---
title: Přiřazení portů vzdáleného ladicího programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2628d8929a0d2b6fd3561f88c81cfaa3b62564f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542100"
---
# <a name="remote-debugger-port-assignments"></a>Přiřazení portů vzdáleného ladicího programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Remote Debugger může běžet jako aplikace nebo jako služba na pozadí. Když je aplikace spuštěna jako aplikace, používá port, který je přiřazen ve výchozím nastavení následujícím způsobem:  
  
- Visual Studio 2015:4020  
  
- Visual Studio 2013:4018  
  
- Visual Studio 2012:4016  
  
  Jinými slovy, číslo portu přiřazené vzdálenému ladicímu programu se zvýší o 2 pro každou verzi. Můžete nastavit jiné číslo portu, které chcete. Vyvysvětlíme, jak se v pozdější části nastavují čísla portů.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port vzdáleného ladicího programu v 32 operačních systémech  
 TCP 4020 (v aplikaci Visual Studio 2015) je hlavní port a je vyžadován pro všechny scénáře. Můžete ji nakonfigurovat buď z příkazového řádku, nebo z okna vzdáleného ladicího programu.  
  
 V okně vzdáleného ladicího programu klikněte na tlačítko **Nástroje/možnosti**a nastavte číslo portu TCP/IP.  
  
 Na příkazovém řádku spusťte vzdálený ladicí program s přepínačem **/port** : **msvsmon/port \<port number> **.  
  
 Všechny přepínače příkazového řádku vzdáleného ladícího programu najdete v nápovědě pro vzdálené ladění (stisknutím klávesy **F1** nebo kliknutím na tlačítko **Nápověda/použití** v okně vzdáleného ladicího programu).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port vzdáleného ladicího programu v 64 operačních systémech  
 Po spuštění verze 64 vzdáleného ladicího programu se ve výchozím nastavení použije port 4020.  Při ladění 32 procesu se v 64 verze vzdáleného ladicího programu spustí 32 verze vzdáleného ladicího programu na portu 4021. Pokud spustíte 32 vzdálený ladicí program, použije 4020 a 4021 se nepoužije.  
  
 Tento port lze konfigurovat z příkazového řádku: **msvsmon/wow64port \<port number> **.  
  
## <a name="the-discovery-port"></a>Port zjišťování  
 UDP 3702 se používá k nalezení spuštěných instancí vzdáleného ladicího programu v síti (například dialogového okna **Najít** v dialogovém okně **připojit k procesu** ). Používá se jenom pro zjišťování počítače, na kterém běží vzdálený ladicí program, takže je volitelný, pokud máte nějaký jiný způsob, jak znát název počítače nebo IP adresu cílového počítače. Toto je standardní port pro zjišťování, takže číslo portu nelze nakonfigurovat.  
  
 Pokud nechcete povolit zjišťování, můžete spustit msvsmon z příkazového řádku se zakázaným zjišťováním:  **msvsmon/nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Porty vzdáleného ladicího programu v Azure  
 Následující porty používá vzdálený ladicí program v Azure. Porty v cloudové službě jsou namapované na porty na jednotlivém virtuálním počítači. Všechny porty jsou TCP.  

|**Připojení**|**Port v cloudové službě**|**Port na virtuálním počítači**|  
|-|-|-|
|Microsoft. WindowsAzure. plugins. Remotedebuggeru. Connector|30400|30398|  
|Microsoft. WindowsAzure. plugins. Remotedebuggeru. resílaer|31400|31398|  
|Nahrání Microsoft. WindowsAzure. plugins. Remotedebuggeru.|32400|32398|  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)
