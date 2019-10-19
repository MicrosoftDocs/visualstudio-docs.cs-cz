---
title: 'Idebugdocumenthost –:: GetDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569421"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Vrátí rozsah znaků, které byly přidány pomocí metody `IDebugDocumentHelper::AddDeferredText` v původním hostitelském dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwTextStartCookie`  
 pro Soubor cookie definovaný hostitelem, který představuje počáteční pozici textu.  
  
 `pcharText`  
 [in, out] Znaková vyrovnávací paměť textu. Tato metoda nevrací znaky, pokud je tento parametr `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Vyrovnávací paměť atributu znaku. Tato metoda nevrací atributy, pokud je tento parametr `NULL`.  
  
 `pcNumChars`  
 [in, out] Určuje skutečný počet vrácených znaků nebo atributů. Před voláním této metody musí být tento parametr nastaven na hodnotu nula.  
  
 `cMaxChars`  
 pro Maximální počet znaků, který má být vrácen.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_NOTIMPL`|Metoda není implementována.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda může vracet `E_NOTIMPL`, pokud hostitel nevolá `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Tato metoda vrátí text z původního dokumentu. Hostitel nesleduje úpravy ani jiné změny v dokumentu.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugdocumenthost –](../../winscript/reference/idebugdocumenthost-interface.md)  
 [Idebugdocumenthelper –:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR – výčet](../../winscript/reference/source-text-attr-enumeration.md)