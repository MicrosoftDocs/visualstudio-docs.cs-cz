---
title: IDebugDocumentPosition2::GetFileName | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5426a09148742d23b4181c5d96e85e608ae9637f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771446"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá název souboru zdrojového souboru, který obsahuje umístění dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetFileName(   
   BSTR* pbstrFileName  
);  
```  
  
```csharp  
int GetFileName(   
   out string pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrFileName`  
 [out] Vrátí název souboru zdrojového souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Zdrojový soubor nemusí mít vždy název souboru (zdrojový soubor neexistuje na disku, například).  
  
## <a name="see-also"></a>Viz také  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

