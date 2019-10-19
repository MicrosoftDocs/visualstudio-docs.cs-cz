---
title: 'Iactivescriptdebug –:: EnumCodeContextsOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aedfe5d40d8f4086e30f3a62c070b8ccd5ef2388
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572780"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Používá inteligentní hostitel k delegování metody `IDebugDocumentContext::EnumCodeContexts`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 pro Zdrojový kontext zadaný pro `IActiveScriptParse::ParseScriptText` nebo `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 pro Posun znaku vzhledem k začátku textu skriptu.  
  
 `uNumChars`  
 pro Počet znaků v tomto kontextu.  
  
 `ppescc`  
 mimo Enumerátor kontextů kódu v zadaném rozsahu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Inteligentní hostitelé používají tuto metodu k delegování metody `IDebugDocumentContext::EnumCodeContexts`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptdebug –](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)