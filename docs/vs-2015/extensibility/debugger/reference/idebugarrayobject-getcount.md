---
title: IDebugArrayObject::GetCount | Dokumentace Microsoftu
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
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8951b19bc811234dc9003853c6bf227195787403
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797140"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá počet elementů v poli.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwElements`  
 [out] Vrátí počet.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda považuje všechny prvky objektu pole jednorozměrné pole, i když objekt pole je vícerozměrné. Mějme například pole `myarray[3][2][6]`, tato metoda vrátí 36 `pdwElements` parametru. Použití [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodu pro načtení jednotlivých prvků jeden po druhém.  
  
## <a name="see-also"></a>Viz také  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)

