---
title: Aktivních skriptů konstanty, výčty a kódy chyb | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791991"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Konstanty, výčty a kódy chyb aktivních skriptů
Tato část popisuje, výčty a kódy chyb používá v systému Windows skriptovací stroje.  
  
## <a name="constants"></a>Konstanty  
  
|Konstanta|Popis|  
|--------------|-----------------|  
|[Scriptthreadid – konstanty](../../winscript/reference/scriptthreadid-constants.md)|Určuje typ přístup z více vláken.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[Scriptprop_hostkeepalive – vlastnost](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Použít k určení, zda skriptovacího stroje by měly být udržovány plně funkční, pokud existují nevyřízené odkazy.|  
  
## <a name="enumerations"></a>Výčty  
  
|Výčet|Popis|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE – výčet](../../winscript/reference/scriptgctype-enumeration.md)|Typ kolekce paměti k provedení.|  
|[SCRIPTLANGUAGEVERSION – výčet](../../winscript/reference/scriptlanguageversion-enumeration.md)|Určuje možné skriptování verze.|  
|[SCRIPTSTATE – výčet](../../winscript/reference/scriptstate-enumeration.md)|Určuje stav skriptovací stroje.|  
|||  
|[SCRIPTTHREADSTATE – výčet](../../winscript/reference/scriptthreadstate-enumeration.md)|Určuje stav vlákna v skriptovacího stroje.|  
|[SCRIPTTRACEINFO – výčet](../../winscript/reference/scripttraceinfo-enumeration.md)|Představuje skriptu událost, která jsou trasovány. Používány [iactivescriptsitetraceinfo::sendscripttraceinfo – metoda](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING – výčet](../../winscript/reference/scriptuichandling-enumeration.md)|Představuje způsob, že by měly být zpracovány kontrolní mechanismus uživatelského rozhraní.|  
|[SCRIPTUICITEM – výčet](../../winscript/reference/scriptuicitem-enumeration.md)|Představuje typ položky uživatelského rozhraní. Používány [iactivescriptsiteuicontrol::getuibehavior – metoda](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Kódy chyb  
  
|Kód chyby|Popis|  
|----------------|-----------------|  
|[Script_e_propagate – kód chyby](../../winscript/reference/script-e-propagate-error-code.md)|Chyba skriptu je rozšířen volajícího, což může být v jiném podprocesu.|  
|[Script_e_recorded – kód chyby](../../winscript/reference/script-e-recorded-error-code.md)|Byla předána chyba mezi skriptovací stroj a hostitelem.|  
|[Script_e_reported – kód chyby](../../winscript/reference/script-e-reported-error-code.md)|Skriptovací stroj ohlásil k neošetřené výjimce k hostiteli.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)