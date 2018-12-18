---
title: Rozhraní IActiveScriptSiteDebug32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793659"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 rozhraní
Implementace inteligentního hostitele `IActiveScriptSiteDebug32` rozhraní provádět správu dokumentu a zapojit ladění. `IActiveScriptSite` Objekt obvykle představuje implementaci objektu `IActiveScriptSiteDebug32` rozhraní. Pokud to uděláte, zavolejte `IActiveScriptSite::QueryInterface` metoda získat `IActiveScriptSiteDebug32` rozhraní.  
  
 Kromě metod zděděno z `IUnknown`, `IActiveScriptSiteDebug32` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Vrátí objekt ladění aplikace přidružené k této lokalitě skriptu.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Používá stroj jazyk delegovat `IDebugCodeContext::GetSourceContext`.|