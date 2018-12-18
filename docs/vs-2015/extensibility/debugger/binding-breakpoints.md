---
title: Vytváření vazeb zarážek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f8061b8d9a9cf3f29889405ea8004a79a0af8216
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807365"
---
# <a name="binding-breakpoints"></a>Vytváření vazeb zarážek
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pokud uživatel nastaví zarážku, třeba stisknutím kombinace kláves F9, rozhraní IDE výrobky zpracovává žádost a vyzve ladicí relaci vytvořit zarážky.  
  
## <a name="setting-a-breakpoint"></a>Nastavením zarážky  
 Nastavením zarážky je dvoustupňový proces, protože kód nebo data ovlivněná zarážky nemusí být ještě k dispozici. Nejprve musí být popsány zarážku a pak, jako kód nebo data k dispozici, se musí být vázán na tento kód nebo data, následujícím způsobem:  
  
1.  Zarážka je požadován z odpovídající ladicí stroj (DEs) a pak je zarážka vázána na kód nebo data, jakmile je k dispozici.  
  
2.  Požadavek zarážky se odešle na relaci ladění, která odešle do všech relevantních DEs. Žádné DE, který vybere pro zpracování zarážka vytvoří odpovídající čekajících zarážek.  
  
3.  Ladicí relaci čekajících zarážek shromažďuje a odesílá zpět do balíčku pro ladění (ladění součástí aplikace Visual Studio).  
  
4.  Ladění balíčku zobrazí výzvu k relaci ladění pro vazbu čekající zarážka kódu nebo data. Ladicí relaci odešle tento požadavek na všechny relevantní DEs.  
  
5.  Pokud je DE je schopen navázat zarážku, odešle, že zarážku vázán události zpět do relace ladění. Pokud ne, místo toho odešle událost chyby zarážky.  
  
## <a name="pending-breakpoints"></a>Čekajících zarážek  
 Čekající zarážkou můžete svázat do víc umístění kódu. Například řádek zdrojového kódu pro šablony jazyka C++ lze svázat pořadí každý kód generován ze šablony. Relace ladění můžete použít vázané událost zarážky se vytvořit výčet kód kontexty vázán na zarážku v době, kdy byla vyslána události. Kontexty více kódu mohou být vázány později, tak DE mohou odesílat že více zarážka vázána události pro každý požadavek vazby. Zavedenými však má odeslat jenom jednu událost chyby zarážky každý požadavek vazby.  
  
## <a name="implementation"></a>Implementace  
 Prostřednictvím kódu programu, balíček ladění volá ladicí relace správci a dá jí [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) rozhraní, která obaluje [BP_REQUEST_INFO](../../extensibility/debugger/reference/bp-request-info.md) strukturou, který popisuje zarážky, která se má nastavit. I když zarážky můžou být v mnoha formách, takže v konečném důsledku převedou do kódu nebo datového kontextu.  
  
 SDM předá toto volání na každý relevantní DE voláním jeho [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) metody. Pokud je DE vybere možnost zpracování zarážku, vytvoří a vrátí [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) rozhraní. SDM shromažďuje těchto rozhraní a předá zpět do balíčku pro ladění jako jediný `IDebugPendingBreakpoint2` rozhraní.  
  
 Zatím bylo vygenerováno žádné události.  
  
 Ladit balíček poté se pokusí vytvořit vazbu čekající zarážka kódu nebo dat voláním [svázat](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), které je implementované DE.  
  
 Pokud je vázán k zarážce, odešle je DE [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) rozhraní události do balíčku pro ladění. Ladění balíčku používá toto rozhraní se vytvořit výčet všech kontextech kódu (nebo jeden datový kontext) vázán na zarážku voláním [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), který vrátí jeden nebo více [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) rozhraní. [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) rozhraní vrátí [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) rozhraní, a [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) vrátí [BP_ RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) sjednocení obsahující kontext kódu nebo data.  
  
 Pokud DE není schopen navázat zarážku, odešle jediného [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) rozhraní události do balíčku pro ladění. Ladění balíčku načte typ chyby (chyba nebo upozornění) a informačních zpráv voláním [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)následovaný [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) a [ GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Tím se vrátí [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) struktura obsahující typ chyby a zprávy.  
  
 Pokud se Zavedenými zpracovává zarážky, ale nelze vytvořit vazbu, je vrácena chyba typu `BPET_TYPE_ERROR`. Ladění balíčku odpoví tím, že zobrazuje dialogové okno chyby a rozhraní IDE umístí piktogram vykřičník uvnitř piktogram zarážky vlevo od řádku zdrojového kódu.  
  
 Pokud se Zavedenými zpracovává zarážku, nejde vytvořit vazbu ji, ale některé jiné DE může vázat, vrátí upozornění. Integrované vývojové prostředí jsou reaguje tak, že otázku piktogram uvnitř piktogram zarážky vlevo od řádku zdrojového kódu.  
  
## <a name="see-also"></a>Viz také  
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)

