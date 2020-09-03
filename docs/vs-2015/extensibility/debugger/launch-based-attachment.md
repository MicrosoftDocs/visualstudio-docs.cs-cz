---
title: Příloha na základě spuštění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09a6b39bef9ba6af098bf92d779a490e22492209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203159"
---
# <a name="launch-based-attachment"></a>Příloha založená na spuštění
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Příloha založená na spouštění programu je automatická. V případě, že je proces hostující program spuštěný pomocí modelu SDM, je příloha založená na spuštění následující jako cesta podobná metodě ručního připojení. Informace najdete v tématu [připojení k programu](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Proces připojení  
 Hlavním rozdílem je posloupnost událostí za voláním **připojení** , a to následujícím způsobem:  
  
1. Odešle objekt události **IDebugEngineCreateEvent2** do SDM. Podrobnosti najdete v tématu [posílání událostí](../../extensibility/debugger/sending-events.md).  
  
2. Zavolejte `IDebugProgram2::GetProgramId` metodu na rozhraní **IDebugProgram2** předané metodě **Attach** .  
  
3. Odešle objekt události **IDebugProgramCreateEvent2** , který oznamuje službě SDM, že byl vytvořen místní objekt **IDebugProgram2** , který reprezentuje program do de.  
  
4. Odešle objekt události [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , který oznamuje SDM, že se pro proces, který se spustil, vytvoří nové vlákno.  
  
## <a name="see-also"></a>Viz také  
 [Odeslání požadovaných událostí](../../extensibility/debugger/sending-the-required-events.md)   
 [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
