---
title: 'Postupy: ladění klientů a serverů modelu COM pomocí ladění RPC | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fda2a10cd559f940ab87e5cc8c26f5b47dbec194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837314"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Postupy: Ladění klientů a serverů modelu COM pomocí ladění RPC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít ladění vzdáleného volání procedur (RPC) pro ladění klientských a serverových aplikací modelu COM. Je nutné povolit ladění RPC pro použití. Když je povoleno ladění RPC, při krokování volání serveru z klienta se ladicí program připojí k serveru a umožní vám ladit jeho kód. Když je ladicí program připojen, můžete použít všechny funkce ladicího programu společně s procesy klienta i serveru.  
  
### <a name="to-enable-rpc-debugging"></a>Povolení ladění RPC  
  
1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).  
  
2. V dialogovém okně **Možnosti** klikněte na složku **ladění** .  
  
3. Klikněte na **nativní** stránku.  
  
4. Zaškrtněte políčko **ladění RPC** .  
  
    > [!NOTE]
    > Chcete-li ladit volání RPC, je nutné mít oprávnění správce nebo Power Users.  
  
    > [!NOTE]
    > Krok RPC do vzdáleného serveru se systémem Microsoft Windows Vista bude fungovat pouze v případě, že je k vzdálenému serveru připojen nativní ladicí program. V opačném případě selže volání RPC bez chybové zprávy. V opačném případě bude volání RPC dokončeno, ale krok do volání RPC nebude fungovat.  
  
## <a name="see-also"></a>Viz také  
 [Ladění serveru a kontejneru modelu COM](../debugger/com-server-and-container-debugging.md)   
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
