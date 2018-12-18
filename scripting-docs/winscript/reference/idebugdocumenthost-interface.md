---
title: Idebugdocumenthost – rozhraní | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adaeb98f18a052106036a91885696dd4b4760dea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794250"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost – rozhraní
Zpřístupní funkce specifické pro hostitele, například k ladicího programu zvýrazňování syntaxe. `IDebugDocumentHelper::SetDebugDocumentHost` Metoda přijímá jako argument toto rozhraní.  
  
 Kromě metod zděděno z `IUnknown`, `IDebugDocumentHost` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Vrátí rozsah znaků, které byly přidány pomocí `IDebugDocumentHelper::AddDeferredText`, v původním dokumentu hostitele.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Vrací atributy textu pro blok textu dokumentu.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Hostitel upozorní, že se vytváří nový kontext dokumentu a umožňuje na hostiteli a volitelně vrátí objekt, který řídí nový kontext.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Vrátí úplnou cestu (včetně názvu souboru) dokumentu zdrojový soubor.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Vrací název dokumentu, bez informací o cestě.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Upozorní hostitele se uložila dokumentu zdrojový soubor a že by měl aktualizovat její obsah.|