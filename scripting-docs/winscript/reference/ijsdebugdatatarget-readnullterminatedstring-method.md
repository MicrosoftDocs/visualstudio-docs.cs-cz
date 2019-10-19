---
title: 'IJsDebugDataTarget:: Readnullterminatedstring – – metoda | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572399"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString – metoda
Přečte zadaný počet znaků z cíle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 pro Adresa, ze které se má číst.  
  
 `characterSize`  
 [in] velikost každého znaku v řetězci  
  
 `maxCharacters`  
 pro Maximální počet znaků, které mají být čteny. maxCharacters by měla být přiměřená. Žádná žádost o více než 128 MB paměti se nezdaří.  Pokud je řetězec větší než maxCharacters, výsledný řetězec se zkrátí po maxCharacters.  
  
 `pString`  
 mimo BSTR načtený z cíle.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Vrátí S_FALSE, pokud je zkrácený.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Jscript9diag. h  
  
## <a name="see-also"></a>Viz také:  
 [IJsDebugDataTarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)