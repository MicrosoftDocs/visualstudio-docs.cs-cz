---
title: Ujistěte se, že je na cílovém počítači správně nakonfigurovaný server DNS | Microsoft Docs
description: K této chybě dojde, když cílový počítač nemůže přeložit název hostitelského počítače ladicího programu sady Visual Studio.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf61e50cc1a6a831625d9cb7c0b12a286e20239f
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466248"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Chyba: Ověřte, zda je na cílovém počítači správně nakonfigurován server DNS.
Při pokusu o vzdálené ladění se může zobrazit následující chybová zpráva:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 K této chybě dojde, když cílový počítač nemůže přeložit název hostitelského počítače ladicího programu sady Visual Studio. V cílovém počítači ověřte nastavení DNS.

- Informace o zobrazení nastavení DNS v systémech Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 nebo Windows Server 2008 R2 získáte tak, že v nabídce **Start** kliknete na položku **pomoc a podpora** a pak vyhledáte **nastavení změnit protokol TCP/IP**.

- Další informace získáte, když přejdete na [Web Microsoft Windows](https://www.microsoft.com/windows/) a vyhledáte **nastavení TCP/IP pro změnu**.

  Pokud nemůžete vyřešit problém DNS, můžete zkusit spustit vzdálený ladicí program pod jiným účtem. K této chybě dochází pouze v případě, že používáte vzdálený ladicí program pod účtem místní systém nebo síťová služba. Pokud spustíte vzdálený ladicí program pod jiným účtem, může použít ověřování NTLM, které nevyžaduje DNS. . Postup najdete v tématu [Chyba: služba Visual Studio Remote Debugger v cílovém počítači se nemůže připojit zpět k tomuto počítači](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
