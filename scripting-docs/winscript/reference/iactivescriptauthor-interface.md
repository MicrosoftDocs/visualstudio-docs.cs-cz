---
title: Rozhraní Iactivescriptauthor – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576160"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor – rozhraní
Představuje služby vytváření obsahu, včetně IntelliSense a kompletování informací.  
  
 Kromě metod zděděných z `IUnknown` rozhraní `IActiveScriptAuthor` zpřístupňuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Přidá název položky na kořenové úrovni do oboru názvů modulu vytváření skriptů. *Položka kořenové úrovně* je objekt, který může obsahovat vlastnosti a metody a může také obsahovat zdroj události.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Přidá kód skriptletu jako podřízený objekt `IScriptNode` kořenové úrovně. V hostiteli může mít plně kvalifikovaný název skriptletu jenom dvě úrovně.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Přidá knihovnu typů do oboru názvů pro skript.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Vrací sadu dokončovacích znaků pro požadovaný kontext dokončení.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Vrátí skriptletu, který má zadané atributy.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Vrátí informace o typu a pozice ukotvení pro daný znak v bloku kódu. Poskytuje informace pro členské technologie IntelliSense, globální seznamy a popisy parametrů.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Vrátí informace o jazyce.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Vrátí `IScriptNode` kořen stromu skriptu autora.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Vrátí atributy textu skriptletu.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Vrátí atributy textu bloku skriptu.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Vrátí hodnotu, která označuje, zda má daný znak potvrdit příkaz doplňováním aplikací.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analyzuje text skriptu, přidá text do modulu vytváření skriptů pro vytváření a vytvoří objekt `IScriptEntry`, který odpovídá bloku skriptu.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Odebere objekt `NamedItem` z oboru názvů modulu vytváření skriptů.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Odebere knihovnu typů z oboru názvů modulu vytváření skriptů.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní pro vytváření aktivních skriptů](../../winscript/reference/active-script-authoring-interfaces.md)