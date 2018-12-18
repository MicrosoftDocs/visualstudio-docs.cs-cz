---
title: IActiveScriptAuthor::RemoveNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0f3acc7d61d63ce4fb4fe53729ce43324b9718a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793272"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Odebere `NamedItem` objekt z oboru názvů vytváření modulu skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [v] Adresa vyrovnávací paměť, která identifikuje `NamedItem` objekt, který chcete odebrat.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`S_FALSE`|`NamedItem` Objekt se nenachází v oboru názvů vytváření modulu skriptu.|  
  
## <a name="remarks"></a>Poznámky  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) slouží k vložení `NamedItem` objektu do skriptu pro tvorbu názvů stroje.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptauthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)