---
title: Idebugasyncoperation – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793983"
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation – rozhraní
Implementuje správce ladění procesu `IDebugAsyncOperation` rozhraní. Volá modul jazyka `IDebugApplication::CreateAsyncDebugOperation` metoda získat odkaz na tomto rozhraní. Můžete použít modul jazyka `IDebugAsyncOperation` rozhraní k poskytování přístupu asynchronní operaci synchronní ladění.  
  
 Kromě metod zděděno z `IUnknown`, `IDebugAsyncOperation` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Vrátí synchronní ladění operaci přidružené k tomuto objektu.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Způsobí, že na začátek asynchronní operace.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Zruší operace.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Určuje, pokud ladění operace byla dokončena.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Poskytuje návratovou hodnotu a parametr návratové objektu z operace synchronní ladění.|