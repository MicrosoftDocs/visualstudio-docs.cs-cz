---
title: 'Idebugdocumenthelper –:: CreateDebugDocumentContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.CreateDebugDocumentContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::CreateDebugDocumentContext
ms.assetid: aa4ec691-9fb1-4da7-8085-b40d8a062467
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24a039b5c4de410e67dc2dfb2859e1f4cc8b1739
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576992"
---
# <a name="idebugdocumenthelpercreatedebugdocumentcontext"></a>IDebugDocumentHelper::CreateDebugDocumentContext
Vytvoří nový kontext dokumentu ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateDebugDocumentContext(  
   ULONG                    iCharPos,  
   ULONG                    cChars,  
   IDebugDocumentContext**  ppddc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iCharPos`  
 pro Umístění začátku obsahu dokumentu ladění.  
  
 `cChars`  
 pro Počet znaků v kontextu.  
  
 `ppddc`  
 mimo Nový kontext dokumentu ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje hostiteli vytvořit nový kontext dokumentu ladění.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentHelper – rozhraní](../../winscript/reference/idebugdocumenthelper-interface.md)