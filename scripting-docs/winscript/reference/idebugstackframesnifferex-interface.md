---
title: Idebugstackframesnifferex – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56d6e63c41db274634b2593989800ea0392b93a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794181"
---
# <a name="idebugstackframesnifferex-interface"></a>IDebugStackFrameSnifferEx – rozhraní
Poskytuje způsob, jak vytvořit výčet rámce zásobníku logické známé součástí. Skriptovací stroje obvykle toto rozhraní implementovat. Používá správce ladění procesu toto rozhraní najít všechny rámce zásobníku přidružené dané vlákno.  
  
> [!NOTE]
>  Toto rozhraní je volat z vlákna, které vás zajímají. Implementace rozhraní musí identifikovat aktuální vlákno a vrátí enumerátor vhodné.  
  
 Kromě metod zděděno z `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Vrátí enumerátor rámce zásobníku pro aktuální vlákno.|