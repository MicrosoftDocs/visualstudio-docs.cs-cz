---
title: Idebugapplicationthread – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793938"
---
# <a name="idebugapplicationthread-interface"></a>IDebugApplicationThread – rozhraní
Umožňuje strojů jazyka a hostitele, zadejte synchronizace vláken a spravovat informace o stavu ladění specifické pro vlákno. Rozšiřuje toto rozhraní `IRemoteDebugApplicationThread` rozhraní pro poskytování bez vzdáleného přístupu k vlákno.  
  
 Kromě metod zděděno z `IRemoteDebugApplicationThread`, `IDebugApplicationThread` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Poskytuje mechanismus pro volajícího, aby spuštění kódu v aplikaci vlákno.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Určuje, zda je tento přístup z více vláken aktuálně spuštěných vláken.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Určuje, zda je tento přístup z více vláken vlákno ladicí program.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Nastaví popis tohoto podprocesu.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Nastaví popis stavu přístup z více vláken.|