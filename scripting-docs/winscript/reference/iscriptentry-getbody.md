---
title: 'Iscriptentry –:: GetBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba6019f4729f1b4a31933a4ca93c0eddf6159a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575490"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Vrátí text, který odpovídá textu `IScriptEntry` bloku skriptu, bloku funkce nebo skriptletu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstr`  
 mimo Text v těle jedné z následujících:  
  
- Blok skriptu `IScriptEntry`  
  
- Funkce `IScriptEntry` v bloku funkce  
  
- Obslužná rutina události `IScriptEntry` skriptletu  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 [IScriptEntry – rozhraní](../../winscript/reference/iscriptentry-interface.md)