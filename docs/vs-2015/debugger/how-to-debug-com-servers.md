---
title: 'Postupy: ladění serverů COM | Microsoft Docs'
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
- COM, debugging
- debugging [C++], COM servers
- single document interface (SDI), debugging
- COM servers, debugging
- debugging [C++], ADI applications
- container information
ms.assetid: 9f013c2b-0306-4b34-ba7f-d4445a874da1
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3552ff1ffb5d6b3e3789aebd3a8903bf82a66b16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205419"
---
# <a name="how-to-debug-com-servers"></a>Postupy: Ladění serverů modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladění aplikací serveru COM přináší jedinečnou sadu problémů, které se nedají vždycky snadno vyřešit.  
  
 Pokud nemáte nebo nechcete používat informace o ladění pro aplikaci typu kontejner, začněte ladit serverovou aplikaci pomocí procesu se třemi kroky.  
  
### <a name="to-debug-a-server-application-without-container-information"></a>Ladění serverové aplikace bez informací o kontejneru  
  
1. Spusťte ladění serveru jako normální aplikace.  
  
2. Nastavte zarážky podle potřeby.  
  
3. Spusťte aplikaci kontejneru.  
  
## <a name="see-also"></a>Viz také  
 [Ladění modelu COM a ActiveX](../debugger/com-and-activex-debugging.md)   
 [Postupy: ladění klientů a serverů modelu COM pomocí ladění RPC](../debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging.md)   
 [Ladění serveru a kontejneru modelu COM](../debugger/com-server-and-container-debugging.md)   
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
