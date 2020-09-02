---
title: 'IDebugDocumentPosition2:: GetRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 189810280bd5db4573ba45c2335b8bb96a163abb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200259"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá rozsah této pozice dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBegPosition`  
 [in, out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , která se vyplní počáteční pozicí. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.  
  
 `pEndPosition`  
 [in, out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , která se vyplní koncovou pozicí. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Rozsah určený v umístění dokumentu pro zarážku umístění je používán ladicím modulem (DE) pro vyhledávání v příkazu, který ve skutečnosti přispívá ke kódu. Zvažte například následující kód:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Řádek 5 nepřispívá k laděnému programu bez kódu. Pokud ladicí program, který nastaví zarážku na řádku 5, chce, aby příkaz DE pro hledání v případě prvního řádku, který přispívá ke kódu, vyhledal určitou částku, ladicí program určí rozsah, který obsahuje další kandidátní řádky, kde je možné správně umístit zarážku. Příkaz DE by pak prochází tyto řádky, dokud nenalezne řádek, který by mohl přijmout zarážku.  
  
## <a name="see-also"></a>Viz také  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
