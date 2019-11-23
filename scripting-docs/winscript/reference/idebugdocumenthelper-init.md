---
title: 'Idebugdocumenthelper –:: init | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576867"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Metoda `Init` inicializuje pomocný parametr dokumentu ladění s názvem a počátečními atributy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 pro Ladicí aplikace přidružená k tomuto dokumentu.  
  
 `pszShortName`  
 pro Řetězec zakončený hodnotou null, který obsahuje krátký název dokumentu.  
  
 `pszLongName`  
 pro Řetězec zakončený hodnotou null obsahující dlouhý název dokumentu.  
  
 `docAttr`  
 pro Určuje atributy textového dokumentu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda inicializuje pomocnou nápovědu k dokumentu ladění s názvem a počátečními atributy.  
  
 Tento dokument se ve stromové struktuře nezobrazuje, dokud se nevolá `IDebugDocumentHelper::Attach`.  
  
## <a name="see-also"></a>Viz také:  
 [Idebugdocumenthelper –:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
   [rozhraní idebugdocumenthelper –](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [TEXT_DOC_ATTR – konstanty](../../winscript/reference/text-doc-attr-constants.md)