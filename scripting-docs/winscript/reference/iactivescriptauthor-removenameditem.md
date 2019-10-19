---
title: 'Iactivescriptauthor –:: RemoveNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cade532d2ca276237981855cafe12804307d0bb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572843"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Odebere objekt `NamedItem` z oboru názvů modulu vytváření skriptů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 pro Adresa vyrovnávací paměti, která identifikuje objekt `NamedItem`, který se má odebrat.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`S_FALSE`|Objekt `NamedItem` není přítomen v oboru názvů modulu vytváření skriptů.|  
  
## <a name="remarks"></a>Poznámky  
 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) se používá k vložení objektu `NamedItem` do oboru názvů modulu vytváření skriptů.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptauthor –](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)