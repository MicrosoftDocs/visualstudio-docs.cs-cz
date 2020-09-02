---
title: 'IDebugBreakpointChecksumRequest2:: IsChecksumEnabled | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec878a08e6f22a461eee95f31db7fa2a1bc97886
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431560"
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, zda je povolen kontrolní součet pro tento dokument.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT IsChecksumEnabled(   
   BOOL *pfChecksumEnabled  
);  
```  
  
```csharp  
public int IsChecksumEnabled(   
   out int pfChecksumEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfChecksumEnabled`  
 mimo Vrátí hodnotu TRUE, pokud je povolen kontrolní součet; v opačném případě vrátí hodnotu FALSE.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)
