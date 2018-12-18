---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 40fd8e2d19d3949ff26811956ae3d203871e5510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793269"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Používá inteligentního hostitele delegovat `IDebugDocumentContext::EnumCodeContexts` metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 [v] Kontext zdroje v souladu s `IActiveScriptParse::ParseScriptText` nebo `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [v] Znak posunuto vzhledem ke spuštění skriptu textu.  
  
 `uNumChars`  
 [v] Počet znaků v tomto kontextu.  
  
 `ppescc`  
 [out] Enumerátor kontexty kódu v zadaném rozsahu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Inteligentního hostitele pomocí této metody můžete delegovat `IDebugDocumentContext::EnumCodeContexts` metoda.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptdebug – rozhraní](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)