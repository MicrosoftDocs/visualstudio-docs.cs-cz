---
title: 'Idebugdocumenthelper –:: GetScriptBlockInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a92aa00d7997ceccc583c88a070f6fbc7d4359d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576089"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Načte rozsah znaků a skriptovací modul odpovídající bloku skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 pro Zdrojový kontext pro blok skriptu.  
  
 `ppasd`  
 mimo Skriptovací modul pro tento blok skriptu.  
  
 `piCharPos`  
 mimo Umístění začátku bloku skriptu.  
  
 `cChars`  
 mimo Počet znaků v bloku skriptu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte rozsah znaků a skriptovací modul odpovídající bloku skriptu.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentHelper – rozhraní](../../winscript/reference/idebugdocumenthelper-interface.md)