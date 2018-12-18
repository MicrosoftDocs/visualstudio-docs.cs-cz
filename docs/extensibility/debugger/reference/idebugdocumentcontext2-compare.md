---
title: IDebugDocumentContext2::Compare | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af349d8568d50e2059ab33ad54b14f499c7b6afd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913459"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Porovná tento kontext dokumentu do daného pole kontextů dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `compare`  
 [in] Hodnota z [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) výčet, který určuje typ porovnání.  
  
 `rgpDocContextSet`  
 [in] Pole [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objekty, které představují dokumentu kontexty porovnávané hodnotě.  
  
 `dwDocContextSetLen`  
 [in] Délka pole kontexty dokumentu k porovnání.  
  
 `pdwDocContext`  
 [out] Vrátí index do `rgpDocContextSet` pole první kontext dokumentu, který vyhovuje porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` Pokud byla nalezena shoda. Vrátí `S_FALSE` Pokud nebyla nalezena žádná shoda. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objekty, které jsou předány jako pole musí být implementované stejné ladicího stroje, který implementuje `IDebugDocumentContext2` objekt volána na; v opačném případě porovnání není platný.  
  
## <a name="see-also"></a>Viz také  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)