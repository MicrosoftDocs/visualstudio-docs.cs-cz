---
title: 'Iapplicationdebuggerui –:: BringDocumentContextToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8648a4377e901908df20cdb5f413ee73ede5c1a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577815"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Přinese okno obsahující daný kontext dokumentu na začátek v uživatelském rozhraní ladicího programu a posune okno do kontextu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddc`  
 pro Kontext dokumentu, který se má přenést nahoru v uživatelském rozhraní ladicího programu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_INVALIDARG`|Kontext určený `pddc` není znám.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda přinese okno obsahující daný kontext dokumentu na začátek v uživatelském rozhraní ladicího programu a posune okno do kontextu.  
  
## <a name="see-also"></a>Viz také:  
 [IApplicationDebuggerUI – rozhraní](../../winscript/reference/iapplicationdebuggerui-interface.md)