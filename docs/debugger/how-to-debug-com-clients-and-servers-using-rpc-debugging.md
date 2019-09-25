---
title: Ladění modelu COM klientů a serverů pomocí ladění RPC | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cca09e917cddffd0d1d844db14ae8a4ca4f0088
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211073"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Postupy: Ladění klientů a serverů modelu COM pomocí ladění RPC
Ladění vzdáleného volání (procedur RPC) můžete použít k ladění aplikace modelu COM klient/server. Je nutné povolit RPC Ladění ji používat. S povoleným laděním RPC, při krokování s vnořením volání serveru z klienta, ladicí program připojí k serveru a umožňuje ladit svůj kód. Když je připojen ladicí program, můžete použít všechny funkce ladicího programu s klientem a serverem procesy.

### <a name="to-enable-rpc-debugging"></a>Pokud chcete povolit ladění RPC

1. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.

2. V **možnosti** dialogové okno, klikněte na tlačítko **ladění** složky.

3. Klikněte na tlačítko **nativní** stránky.

4. Vyberte **RPC Ladění** zaškrtávací políčko.

    > [!NOTE]
    > Chcete-li ladit volání RPC, musí mít oprávnění správce nebo Power Users.

    > [!NOTE]
    > RPC krokování s vnořením do serveru pro vzdálený, na kterém běží systém Microsoft Windows Vista bude fungovat jenom v případě, že nativní ladicí program je připojen ke vzdálenému serveru. V opačném případě se nezdaří volání protokolu RPC bez chybovou zprávu. V opačném případě se dokončí volání protokolu RPC, ale Krok dovnitř nebudou fungovat volání protokolu RPC.

## <a name="see-also"></a>Viz také
- [Ladění serveru a kontejneru modelu COM](../debugger/com-server-and-container-debugging.md)
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)