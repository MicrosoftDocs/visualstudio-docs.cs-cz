---
title: Iactivescripterrordebug – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ff2dda33c1e406f87a157173c41015acf96e62a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793317"
---
# <a name="iactivescripterrordebug-interface"></a>IActiveScriptErrorDebug – rozhraní
Poskytuje informace o kontextu dokumentu pro chyby při kompilaci a výjimky v době běhu. `IActiveScriptError::QueryInterface` Metoda podporuje `IActiveScriptErrorDebug` rozhraní.  
  
 Kromě metod zděděno z `IActiveScriptError`, `IActiveScriptErrorDebug` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Poskytuje kontext dokumentu pro tuto chybu.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Poskytuje rámce zásobníku, která je používána pro chyby za běhu.|