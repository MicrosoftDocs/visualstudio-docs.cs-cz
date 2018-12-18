---
title: Iactivescriptsitedebug – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793518"
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug – rozhraní
Implementace inteligentního hostitele `IActiveScriptSiteDebug` rozhraní provádět správu dokumentu a zapojit ladění. `IActiveScriptSite` Objekt obvykle představuje implementaci objektu `IActiveScriptSiteDebug` rozhraní. Pokud to uděláte, zavolejte `IActiveScriptSite::QueryInterface` metoda získat `IActiveScriptSiteDebug` rozhraní.  
  
 Kromě metod zděděno z `IUnknown`, `IActiveScriptSiteDebug` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Používá stroj jazyk delegovat `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Vrátí objekt ladění aplikace přidružené k této lokalitě skriptu.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Získá uzlu aplikace v rámci skriptu, který má být přidána dokumenty.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Umožňuje určit, jak se budou zpracovávat chyby spuštění inteligentního hostitele.|