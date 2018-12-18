---
title: Iactivescriptauthor – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793323"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor – rozhraní
Představuje vytváření služeb, včetně technologie IntelliSense a kolace informací.  
  
 Kromě metod zděděno z `IUnknown`, `IActiveScriptAuthor` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Přidá název položky kořenové úrovně do skriptu pro tvorbu názvů stroje. A *kořenovou položku* je objekt obsahující vlastnosti a metody a může obsahovat také zdroje událostí.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Přidá skriptlet kód jako podřízená kořenové úrovni `IScriptNode` objektu. Na hostiteli plně kvalifikovaný název skriptletu může mít pouze dvě úrovně.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Knihovny typů přidá do oboru názvů pro skript.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Vrací sadu znaků dokončení pro požadovaný dokončení kontextu.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Vrátí skriptlet, který má zadané atributy.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Vrátí typ informace a pozice ukotvení pro daného znaku v bloku kódu. To poskytuje informace pro člen, IntelliSense, globálních seznamů a tipy pro parametr.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Vrátí jazyk informace.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Vrátí `IScriptNode` kořen stromu skriptu vytvářením obsahu.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Vrátí text atributy skriptletu.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Vrátí text atributy blok skriptu.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Vrátí hodnotu, která určuje, zda by měl daného znaku potvrzení dokončování aplikací.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analyzuje text skriptu, přidá text vytváření skriptu vytváření modul a vytvoří `IScriptEntry` objekt, který odpovídá blok skriptu.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Odebere `NamedItem` objekt z oboru názvů vytváření modulu skriptu.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Odebere ze skriptu pro tvorbu názvů modul knihovny typů.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro vytváření aktivních skriptů](../../winscript/reference/active-script-authoring-interfaces.md)