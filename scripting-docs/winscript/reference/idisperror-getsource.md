---
title: 'Idisperror –:: GetSource | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07c87585a92415f0b910210a56efa47e6f91417b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573089"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Vrátí programový identifikátor závislý na jazyce pro třídu nebo aplikaci, která chybu vyvolala.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrSource`  
 mimo Řetězec, který obsahuje programový identifikátor, ve formuláři `progname.objectname`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda slouží k určení třídy nebo aplikace, kde došlo k výjimce. Programový identifikátor může být vrácen v jazyce určeném identifikátorem národního prostředí (LCID) dodaným v okamžiku vyvolání.  
  
> [!NOTE]
> Tato metoda není implementována.  
  
## <a name="see-also"></a>Viz také:  
 [IDispError – rozhraní](../../winscript/reference/idisperror-interface.md)