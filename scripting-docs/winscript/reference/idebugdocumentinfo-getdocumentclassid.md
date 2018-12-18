---
title: IDebugDocumentInfo::GetDocumentClassId | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be3d29cf19752da18b76f31b4d12cecb05592c00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794223"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
Vrátí `CLSID` identifikace typu dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pclsidDocument`  
 [out] A `CLSID` identifikace typu dokumentu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje ladicí program IDE na vlastní prohlížeče hostitele k tomuto dokumentu.  
  
 Pokud dokument zobrazit data, vrátí hodnotu, která nemá `pclsidDocument` je `CLSID_NULL`.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumentinfo – rozhraní](../../winscript/reference/idebugdocumentinfo-interface.md)