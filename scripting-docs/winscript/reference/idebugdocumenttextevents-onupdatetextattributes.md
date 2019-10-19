---
title: 'Idebugdocumenttextevents –:: onUpdateTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateTextAttributes
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 044eec93516bc4e16044c4bf982b48d91269ebaa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575988"
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
Indikuje, že se změnily atributy textu přidružené k rozsahu pozice podkladového znaku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 pro Pozice znaku prvního znaku, který změnil atributy.  
  
 `cNumToUpdate`  
 pro Počet znaků v rozsahu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda označuje, že se změnily atributy textu přidružené k rozsahu pozice podkladového znaku.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentTextEvents – rozhraní](../../winscript/reference/idebugdocumenttextevents-interface.md)