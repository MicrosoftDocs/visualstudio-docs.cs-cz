---
title: Idebugdocumenttext – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 763678b08c22fe34ec6ffebbe670fb8b50af6576
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843454"
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText – rozhraní
Poskytuje přístup k verzi dokumentu ladění prostého textu. Toto rozhraní používá následující konvence:  
  
- Pozice znaku a čísla řádků jsou od nuly.  
  
- Pozice znaku představují posun znak; není představují bajtů nebo word posunů. Pro Win32 je pozice znaku Unicode posun.  
  
  Kromě metod zděděných z `IDebugDocument`, `IDebugDocumentText` rozhraní poskytuje následující metody.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Vrací atributy dokumentu.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Vrátí počet řádků a počtu znaků v dokumentu.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Vrátí pozici znaku odpovídající první znak řádku.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Vrátí číslo řádku a volitelně odsazení znaku v rámci řádku, který odpovídá dané pozici znaku.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Načte znaky a/nebo znak atributy přidružené k pozici znaku rozsahu.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Vrátí pozici znaku oblast odpovídající kontext dokumentu.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Vytvoří objekt kontextu dokumentu odpovídající pozice rozsahu zadaný znak.|