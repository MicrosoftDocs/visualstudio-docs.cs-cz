---
title: IDebugCodeContext2::GetDocumentContext | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd0fa6dd8d587ade2ca06c3f39f65fb3a5fd295d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822186"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Získá kontext dokumentu, který odpovídá tento kontext kódu. Kontext dokumentu představuje pozici ve zdrojovém souboru, který odpovídá zdrojový kód, který vygeneroval tento pokyn.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDocumentContext(   
   IDebugDocumentContext2** ppSrcCxt  
);  
```  
  
```csharp  
int GetDocumentContext(   
   out IDebugDocumentContext2 ppSrcCxt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppSrcCxt`  
 [out] Vrátí [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objekt, který odpovídá kontext kódu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí kontext dokumentu můžete představit jako pozici ve zdrojovém souboru kontext kódu je pozice instrukce pro kód ve službě stream provádění.  
  
## <a name="see-also"></a>Viz také  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)