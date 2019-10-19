---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577240"
---
# <a name="iactivescript"></a>IActiveScript
Poskytuje metody potřebné k inicializaci skriptovacího stroje. Skriptovací stroj musí implementovat rozhraní `IActiveScript`.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informuje skriptovací stroj [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) webu od hostitele.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Načte objekt lokality přidružený ke skriptovacímu stroji Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Umístí skriptovací stroj do zadaného stavu.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Načte aktuální stav skriptovacího stroje.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Způsobí, že skriptovací modul opustí libovolný aktuálně načtený skript, ztratí jeho stav a uvolní všechny ukazatele rozhraní, které má, a to tak, aby vstoupily do zavřeného stavu.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Přidá název položky na kořenové úrovni do oboru názvů skriptovacího stroje.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Přidá knihovnu typů do oboru názvů pro skript.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Načte rozhraní `IDispatch` spouštěného skriptu.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Načte identifikátor definovaný skriptovacím modulem pro aktuálně spuštěné vlákno.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Načte identifikátor definovaný skriptovacím modulem pro vlákno přidružené k danému vláknu Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Načte aktuální stav vlákna skriptu.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Přeruší provádění spuštěného vlákna skriptu.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Naklonuje aktuální skriptovací stroj (mínus aktuální stav spuštění) a vrátí načtený skriptovací stroj, který nemá v aktuálním vlákně žádný web.|  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace skriptovacích rozhraní systému Windows](../../winscript/reference/windows-script-interfaces-reference.md)