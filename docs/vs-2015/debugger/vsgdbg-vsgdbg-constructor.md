---
title: 'VsgDbg:: VsgDbg (konstruktor) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157442"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (konstruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoří instanci `VsgDbg` třídy s nebo bez přípravy komponenty v aplikaci diagnostiky grafiky pro aktivní zachycení a zaznamenání informací o grafice na základě zadaného logického parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bDefaultInit`  
 `true` Chcete-li určit, že komponenta v aplikaci diagnostiky grafiky je připravena k aktivnímu zachycení a zaznamenání informací o grafice; `false` Chcete-li určit, že aplikace by neměla být připravena k aktivnímu zachytávání a záznamu grafiky v tuto chvíli.  
  
## <a name="remarks"></a>Poznámky  
 Při volání konstruktoru s `bDefaultInit` nastavením na je `true` název souboru protokolu grafiky určen tak, jak `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` jsou definovány symboly preprocesoru a před tím, než `vsgcapture.h` je součástí vaší aplikace.  
  
 Při volání konstruktoru s `bDefaultInit` nastavením na je `false` možné připravit komponentu v aplikaci diagnostiky grafiky na aktivní zachycování a zaznamenávání informací grafiky na pozdější dobu voláním `Init` funkce.  
  
## <a name="see-also"></a>Viz také  
 [VsgDbg:: ~ VsgDbg (destruktor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [For](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
