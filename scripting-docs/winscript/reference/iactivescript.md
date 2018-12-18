---
title: IActiveScript – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793296"
---
# <a name="iactivescript"></a>IActiveScript
Poskytuje metody, které jsou nezbytné k chybě při inicializaci skriptovacího stroje. Skriptovací stroj musí implementovat `IActiveScript` rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informuje o skriptovací stroje systému [iactivescriptsite –](../../winscript/reference/iactivescriptsite.md) lokality od hostitele.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Načte objekt lokality, který je přidružený modul Windows Script.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Skriptovací stroj umístí do zadaného stavu.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Načte aktuální stav skriptovacího stroje.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Způsobí, že skriptovací stroj abandon všech aktuálně načtených skriptů, dojít ke ztrátě stavu a uvolnit všechny ukazatele rozhraní, které je jiné objekty, proto zadávání uzavřeném stavu.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Název položky kořenové úrovni přidá do oboru názvů skriptovacího stroje.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Knihovny typů přidá do oboru názvů pro skript.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Načte `IDispatch` rozhraní pro spouštění skriptu.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Načte identifikátor skriptovací stroj definované pro aktuálně prováděné vlákno.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Načte identifikátor skriptovací stroj definované pro vlákno přidružené k dané vlákno Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Načte aktuální stav vlákna skriptu.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Přerušuje provádění běžící vlákna skriptu.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Provede klonování aktuální skriptovacího stroje (minus všechny aktuální stav provádění), vrácení načíst skriptovací stroj, který má žádná lokalita v aktuální vlákno.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)