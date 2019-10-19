---
title: Konstanty, výčty a kódy chyb aktivního skriptu | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e03bef99c2297d517aa5234db49820a2b9600ce7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572719"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Konstanty, výčty a kódy chyb aktivních skriptů
V této části jsou popsány výčty a kódy chyb používané skriptovacími moduly Windows.  
  
## <a name="constants"></a>Konstanty  
  
|Konstanta|Popis|  
|--------------|-----------------|  
|[SCRIPTTHREADID – konstanty](../../winscript/reference/scriptthreadid-constants.md)|Určuje typ vlákna.|  
  
## <a name="properties"></a>Vlastnosti  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE – vlastnost](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Slouží k určení, zda by měl skriptovací modul zůstat plně funkční, pokud existují nezpracované odkazy.|  
  
## <a name="enumerations"></a>Výčty  
  
|Výčet|Popis|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE – výčet](../../winscript/reference/scriptgctype-enumeration.md)|Typ uvolňování paměti, který má být proveden.|  
|[SCRIPTLANGUAGEVERSION – výčet](../../winscript/reference/scriptlanguageversion-enumeration.md)|Určuje možné verze skriptů.|  
|[SCRIPTSTATE – výčet](../../winscript/reference/scriptstate-enumeration.md)|Určuje stav skriptovacího modulu.|  
|||  
|[SCRIPTTHREADSTATE – výčet](../../winscript/reference/scriptthreadstate-enumeration.md)|Určuje stav vlákna ve skriptovacím stroji.|  
|[SCRIPTTRACEINFO – výčet](../../winscript/reference/scripttraceinfo-enumeration.md)|Představuje událost skriptu, která je sledována. Používá se v [metodě IActiveScriptSiteTraceInfo:: sendscripttraceinfo –](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING – výčet](../../winscript/reference/scriptuichandling-enumeration.md)|Představuje způsob, jakým by měl být zpracován ovládací prvek uživatelského rozhraní.|  
|[SCRIPTUICITEM – výčet](../../winscript/reference/scriptuicitem-enumeration.md)|Představuje typ položky uživatelského rozhraní. Používá se v [metodě IActiveScriptSiteUIControl:: getuibehavior –](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Chybové kódy  
  
|Kód chyby|Popis|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE – kód chyby](../../winscript/reference/script-e-propagate-error-code.md)|Chyba skriptu je šířena volajícímu, který může být v jiném vlákně.|  
|[SCRIPT_E_RECORDED – kód chyby](../../winscript/reference/script-e-recorded-error-code.md)|Mezi skriptovacím modulem a hostitelem byla předána chyba.|  
|[SCRIPT_E_REPORTED – kód chyby](../../winscript/reference/script-e-reported-error-code.md)|Skriptovací stroj oznámil hostiteli neošetřenou výjimku.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)