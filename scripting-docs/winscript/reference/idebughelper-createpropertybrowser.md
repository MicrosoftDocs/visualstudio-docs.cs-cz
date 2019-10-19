---
title: 'Idebughelper –:: CreatePropertyBrowser | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99aa03470b49d02ee9f0ac1548bd1f8e27d0ab34
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562498"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Vrátí prohlížeč vlastností, který zabalí VARIANTu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvar`  
 pro Kořenová varianta, kterou chcete procházet.  
  
 `bstrName`  
 pro Zadejte název kořenového adresáře.  
  
 `pdat`  
 pro Vlákno, na kterém se mají vyžádat vlastnosti. Pokud má tento parametr hodnotu NULL, není zařazování provedeno.  
  
 `ppdob`  
 mimo Prohlížeč vlastností.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí prohlížeč vlastností, který zabalí VARIANTu.  
  
## <a name="see-also"></a>Viz také:  
 [Idebughelper –:: CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)    
 @No__t_1 [rozhraní idebughelper –](../../winscript/reference/idebughelper-interface.md)  
 [IDebugProperty – rozhraní](../../winscript/reference/idebugproperty-interface.md)