---
title: 'IDebugDocumentPositionOffset2:: GetRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a028a2c88fe44aa6a117ddb81cff5788eec1732e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200227"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Načte rozsah pro aktuální pozici dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwBegOffset`  
 [in, out] Posunutí počáteční pozice rozsahu Pokud tyto informace nejsou potřeba, nastavte tento parametr na hodnotu null.  
  
 `pdwEndOffset`  
 [in, out] Posunutí pro koncovou pozici rozsahu Pokud tyto informace nejsou potřeba, nastavte tento parametr na hodnotu null.  
  
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
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
