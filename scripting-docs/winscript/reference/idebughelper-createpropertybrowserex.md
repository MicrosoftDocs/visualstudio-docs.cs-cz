---
title: 'Idebughelper –:: CreatePropertyBrowserEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576504"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Vrátí prohlížeč vlastností, který zabalí VARIANTu a umožňuje vlastní převod hodnot VARIANT nebo typů VARTYPE na řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 pro Objekt, který poskytuje vlastní formátování pro varianty.  
  
 `ppdob`  
 mimo Prohlížeč vlastností.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí prohlížeč vlastností, který zabalí VARIANTu a umožňuje vlastní převod hodnot VARIANT nebo typů VARTYPE na řetězce.  
  
## <a name="see-also"></a>Viz také:  
 [Idebughelper –:: CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
   [rozhraní idebughelper –](../../winscript/reference/idebughelper-interface.md)  
 [IDebugProperty – rozhraní](../../winscript/reference/idebugproperty-interface.md)