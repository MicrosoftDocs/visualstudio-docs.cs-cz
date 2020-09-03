---
title: 'IDebugDisassemblyStream2:: GetCodeLocationId | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebb2280f814985e2352413921a00268d96761b7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196237"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vrátí identifikátor umístění kódu pro konkrétní kontext kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCodeContext`  
 pro Objekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , který se má převést na identifikátor.  
  
 `puCodeLocationId`  
 mimo Vrátí identifikátor umístění kódu. Viz poznámky.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí `E_CODE_CONTEXT_OUT_OF_SCOPE` , zda je kontext kódu platný, ale mimo obor.  
  
## <a name="remarks"></a>Poznámky  
 Identifikátor umístění kódu je specifický pro ladicí stroj (DE), který podporuje zpětný překlad. Tento identifikátor umístění se používá interně ke sledování pozic v kódu a obvykle je adresa nebo posun nějakého druhu. Jediným požadavkem je, že pokud je kontext kódu jednoho umístění menší než kontext kódu jiného umístění, pak odpovídající identifikátor umístění kódu prvního kontextu kódu musí být také menší než identifikátor umístění kódu druhého kontextu kódu.  
  
 Chcete-li načíst kontext kódu pro identifikátor umístění kódu, zavolejte metodu [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
