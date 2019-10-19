---
title: IActiveScriptError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4d3fe5ff90fc0d116814771308fa599052dba9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576905"
---
# <a name="iactivescripterror"></a>IActiveScriptError
Objekt implementující toto rozhraní je předán metodě [IActiveScriptSite:: OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) vždy, když skriptovací modul narazí na neošetřenou chybu. Hostitel pak zavolá metody tohoto objektu, aby získal informace o chybě, ke které došlo.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Načte informace o chybě.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Načte umístění ve zdrojovém kódu, kde došlo k chybě.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Načte řádek ve zdrojovém souboru, kde došlo k chybě.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní aktivních skriptů](../../winscript/reference/active-script-interfaces.md)