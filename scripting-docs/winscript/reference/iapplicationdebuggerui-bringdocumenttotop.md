---
title: 'Iapplicationdebuggerui –:: BringDocumentToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b51e7b588750fc72e61840c4748c006eea732c22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577799"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Přinese okno obsahující zadaný dokument ladění na začátek v uživatelském rozhraní ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddt`  
 pro Dokument ladění, který se má v uživatelském rozhraní ladicího programu přenést nahoru  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_INVALIDARG`|Dokument není znám.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda přinese okno obsahující zadaný dokument ladění na začátek v uživatelském rozhraní ladicího programu.  
  
## <a name="see-also"></a>Viz také:  
 [IApplicationDebuggerUI – rozhraní](../../winscript/reference/iapplicationdebuggerui-interface.md)