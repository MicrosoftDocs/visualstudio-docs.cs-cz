---
title: Přiřazení portů vzdáleného ladicího programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47a2b212ce3e98588a5dcf6ee75a479b01b5b302
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817848"
---
# <a name="remote-debugger-port-assignments"></a>Přiřazení portů vzdáleného ladicího programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Remote Debugger může běžet jako aplikace nebo jako službu na pozadí. Při spuštění jako aplikace, používá port, který je přiřazen ve výchozím nastavení následujícím způsobem:  
  
- Visual Studio 2015:4020  
  
- Visual Studio 2013:4018  
  
- Visual Studio 2012:4016  
  
  Jinými slovy číslo portu přiřazené vzdálený ladicí program je zvýšen o 2 pro každou vydanou verzí. Můžete nastavit jiné číslo portu, jako je. Vysvětlíme, jak nastavit čísla portů v další části.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Portu vzdáleného ladicího programu na 32bitové operační systémy  
 4020 TCP (ve Visual Studiu 2015) je hlavní port a pro všechny scénáře se vyžaduje. To můžete nakonfigurovat z příkazového řádku nebo v okně vzdáleného ladicího programu.  
  
 V okně vzdáleného ladicího programu klikněte na tlačítko **Nástroje / možnosti**a nastavte číslo portu TCP/IP.  
  
 Na příkazovém řádku spustit vzdálený ladicí program se **portu/** přepnout: **msvsmon/port \<číslo portu >**.  
  
 Můžete najít vzdálený ladicí program přepínače příkazového řádku v nápovědě vzdáleného ladění (stisknutím klávesy **F1** nebo klikněte na tlačítko **Nápověda / využití** v okně vzdáleného ladicího programu).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Portu vzdáleného ladicího programu na 64bitové operační systémy  
 Při spuštění 64bitovou verzi vzdáleného ladicího programu, ve výchozím nastavení používá 4020 port.  Pokud ladíte 32bitový proces, spustí 64bitovou verzi vzdáleného ladicího programu na portu 4021 32bitovou verzi vzdáleného ladicího programu. Při spuštění vzdáleného ladicího programu 32-bit, používá 4020 a 4021 nepoužívá.  
  
 Tento port jde nakonfigurovat z příkazového řádku: **Msvsmon/wow64port \<číslo portu >**.  
  
## <a name="the-discovery-port"></a>Port zjišťování  
 UDP 3702 slouží k vyhledání spuštěné instance vzdáleného ladícího programu v síti (například **najít** dialogového okna v **připojit k procesu** dialogového okna). Používá se pouze pro zjišťování počítači se systémem vzdálený ladicí program, takže je volitelný, pokud máte nějaké další způsob, jak zjistit název počítače nebo IP adresu cílového počítače. Jedná se standardním portem pro zjišťování, proto není možné nakonfigurovat číslo portu.  
  
 Pokud nechcete povolit zjišťování, můžete spustit msvsmon z příkazového řádku se zjišťováním zakázané: **Msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Porty vzdálené ladicí program v Azure  
 Vzdálený ladicí program v Azure používá následující porty. Porty v cloudové službě jsou mapovány na porty konkrétního virtuálního počítače. Jsou všechny porty TCP.  
  
||||  
|-|-|-|  
|**připojení**|**Port v cloudové službě**|**Port ve virtuálním počítači**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)



