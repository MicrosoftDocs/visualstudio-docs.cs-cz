---
title: 'Iscriptentry –:: SetItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575373"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Nastaví název položky, která identifikuje objekt `IScriptEntry`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 pro Adresa vyrovnávací paměti, která obsahuje název položky. Název položky se používá hostitelem k identifikaci položky.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Metoda nebyla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pro `IScriptEntry` objekty vrátí tato metoda `S_OK`.  
  
 Pro `IScriptScriptlet` objekty (které jsou odvozeny z `IScriptEntry`) vrátí tato metoda `E_FAIL`. U `IScriptScriptlet` objektů je název položky nastavený pomocí [iactivescriptauthor –:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) a nedá se změnit.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iscriptentry –](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)