---
title: Iactivescriptsitedebugex – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793626"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx – rozhraní
Toto rozhraní spolu s implementovat `IActiveScriptSiteDebug` rozhraní Pokud píšete hostitele, který je potřeba získat oznámení o chybě běhu v aplikaci a volitelně připojení k aplikaci pro ladění. Proces Debug Manager poskytuje oznámení prostřednictvím `IActiveScriptDebug` případě pouze za běhu skriptu ladicí program je v počítači nalezen. Pokud žádné těsně za běhu skriptu ladicí program je nalezen, PDM poskytuje oznámení prostřednictvím `IActiveScriptDebugEx` místo.  
  
 Pokud chcete získat upozornění Chyba spuštění, musí váš hostitel zpracovávat [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). Založená na akci uživatele, můžete se rozhodnout, zda připojit ladicí program interní a vraťte, nebo pro návrat počáteční v ladicím programu OnScriptErrorDebug `pfEnterDebugger` parametr.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informuje o tom, že hostitel o Chyba spuštění skriptu proces ladění Manager nemůže nalézt externí ladicí program pouze v době.|