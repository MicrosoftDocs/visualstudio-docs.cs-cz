---
title: 'Chyba: Ověřte, zda je na cílovém počítači správně nakonfigurován server DNS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35c258a018bec8bd38f8b43690c18b37ee9d6c39
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851937"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Chyba: Ověřte, zda je na cílovém počítači správně nakonfigurován server DNS.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při pokusu o provádět vzdálené ladění, může zobrazit následující chybová zpráva:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 K této chybě dojde, když cílový počítač nemůže přeložit název hostitelského počítače ladicího programu sady Visual Studio. V cílovém počítači ověřte nastavení DNS.  
  
- Informace o zobrazení nastavení DNS v systémech Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 nebo Windows Server 2008 R2 získáte tak, že v nabídce **Start** kliknete na položku **pomoc a podpora**a pak vyhledáte **nastavení změnit protokol TCP/IP**.  
  
- Další informace získáte, když přejdete na [Web Microsoft Windows](https://windows.microsoft.com/) a vyhledáte **nastavení TCP/IP pro změnu**.  
  
  Pokud nemůžete vyřešit problém DNS, můžete zkusit spustit vzdálený ladicí program pod jiným účtem. K této chybě dochází pouze v případě, že používáte vzdálený ladicí program pod účtem místní systém nebo síťová služba. Pokud spustíte vzdálený ladicí program pod jiným účtem, může použít ověřování NTLM, které nevyžaduje DNS. . Postup najdete v tématu [Chyba: služba Visual Studio Remote Debugger v cílovém počítači se nemůže připojit zpět k tomuto počítači](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
