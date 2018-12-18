---
title: Idebugapplication110 – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7c283e925db5b42b4d04bfc42ea087ecc22b6f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793971"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 – rozhraní
`IDebugApplication110` Rozhraní rozšiřuje funkce [idebugapplication – rozhraní](../../winscript/reference/idebugapplication-interface.md). Instance tohoto rozhraní můžete získat voláním QueryInterface na implementaci pro [idebugapplication – rozhraní](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Toto rozhraní je implementováno komponentou PDM verze 11.0 nebo novější. Nachází se v souboru activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplication110` Rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Synchronní zavolá na hlavní vlákno.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Provede asynchronní volání na hlavní vlákno.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Počká pro žádné zadaného popisovače signál současně volání mezi vlákny odeslání tohoto podprocesu. Tato metoda musí volat z vlákna ladicí program.|