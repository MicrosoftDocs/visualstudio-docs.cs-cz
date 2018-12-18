---
title: Idebugstackframesniffer – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794193"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer – rozhraní
Poskytuje způsob, jak vytvořit výčet rámce zásobníku logické známé součástí. Skriptovací stroje obvykle toto rozhraní implementovat. Používá správce ladění procesu toto rozhraní najít všechny rámce zásobníku přidružené dané vlákno.  
  
> [!NOTE]
>  Ladicí program volá toto rozhraní z vlákna, které vás zajímají. Skriptovací stroj musí identifikovat aktuální vlákno a vrátí enumerátor vhodné.  
  
## <a name="methods"></a>Metody  
 Kromě metod zděděno z `IUnknown`, `IDebugStackFrameSniffer` rozhraní poskytuje následující metody.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Vrátí enumerátor rámce zásobníku pro aktuální vlákno.|