---
title: Iactivescriptdebug – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e21f4c99da886bc4907acf8b0934e1b46d57689
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942085"
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug – rozhraní
Implementované skriptovacích strojů ukládaných tuto podporu ladění. Obvykle, objekt, který implementuje `IActiveScriptDebug` rozhraní také implementuje `IActiveScript` rozhraní. Pokud tomu tak, `IActiveScript::QueryInterface` metodu k získání `IActiveScriptDebug` rozhraní.  
  
 `IActiveScriptDebug` Rozhraní poskytuje prostředky pro:  
  
- Inteligentní hostitele s převzetím správy dokumentu.  
  
- Správce ladění procesu synchronizace ladění více skriptovací stroje.  
  
  Kromě metod zděděných z `IUnknown`, `IActiveScriptDebug` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Vrátí text atributy pro libovolný blok textu skriptu.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Vrátí text atributy pro libovolného skriptletu.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Deleguje se do `IDebugDocumentContext::EnumCodeContexts`.|