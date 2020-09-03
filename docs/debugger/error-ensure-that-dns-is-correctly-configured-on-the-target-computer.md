---
title: Chyba – ověřte, zda je na cílovém počítači správně nakonfigurován server DNS | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e374e75caca3dec28800a2eac86d921c861888ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460822"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Chyba: Ověřte, zda je na cílovém počítači správně nakonfigurován server DNS.
Při pokusu o vzdálené ladění se může zobrazit následující chybová zpráva:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.
```

 K této chybě dojde, když cílový počítač nemůže přeložit název hostitelského počítače ladicího programu sady Visual Studio. V cílovém počítači ověřte nastavení DNS.

- Informace o zobrazení nastavení DNS v systémech Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 nebo Windows Server 2008 R2 získáte tak, že v nabídce **Start** kliknete na položku **pomoc a podpora**a pak vyhledáte **nastavení změnit protokol TCP/IP**.

- Další informace získáte, když přejdete na [Web Microsoft Windows](https://www.microsoft.com/windows/) a vyhledáte **nastavení TCP/IP pro změnu**.

  Pokud nemůžete vyřešit problém DNS, můžete zkusit spustit vzdálený ladicí program pod jiným účtem. K této chybě dochází pouze v případě, že používáte vzdálený ladicí program pod účtem místní systém nebo síťová služba. Pokud spustíte vzdálený ladicí program pod jiným účtem, může použít ověřování NTLM, které nevyžaduje DNS. . Postup najdete v tématu [Chyba: služba Visual Studio Remote Debugger v cílovém počítači se nemůže připojit zpět k tomuto počítači](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
