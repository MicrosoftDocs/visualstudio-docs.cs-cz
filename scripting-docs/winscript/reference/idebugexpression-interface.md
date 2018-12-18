---
title: Idebugexpression – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794490"
---
# <a name="idebugexpression-interface"></a>IDebugExpression – rozhraní
Představuje asynchronně vyhodnocený výraz. Skriptovací stroje obvykle toto rozhraní implementovat. Ladicí program IDE se většinou používá toto rozhraní povolit okno s okamžité spuštění nebo okno kukátka.  
  
> [!NOTE]
>  `IDebugExpression` Rozhraní je k dispozici pouze z rámce zásobníku.  
  
 Kromě metod zděděno z `IUnknown`, `IDebugExpression` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Zahájí vyhodnocování výrazu.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Zruší výraz.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Určuje operaci byla dokončena.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Vrátí výsledek vyhodnocení výrazu jako řetězec a operace návratovou hodnotu.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Vrátí výsledek vyhodnocení výrazu jako vlastnost ladění a operace návratovou hodnotu.|