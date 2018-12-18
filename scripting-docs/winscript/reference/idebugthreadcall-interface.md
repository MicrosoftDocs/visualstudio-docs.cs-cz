---
title: Idebugthreadcall – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794235"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall – rozhraní
`IDebugThreadCall` Rozhraní je implementováno obvykle součást, která provádí volání mezi vlákny s `IDebugThread` zařazování implementace zajišťuje správce ladění procesu (PDM).  
  
 Volání PDM `IDebugThreadCall` rozhraní v požadované vláken a `IDebugThreadCall` rozhraní odešle zprávu volání požadované implementace. `IDebugThreadCall` Rozhraní vrhá informace o parametrech, které jsou parametry předané do příslušné horní.  
  
 `IDebugThreadCall` Rozhraní je objekt podprocesy.  
  
## <a name="methods"></a>Metody  
 Kromě metod zděděno z `IUnknown`, `IDebugThreadCall` rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Zpracovává volání spuštění kódu v jiné vlákno.|