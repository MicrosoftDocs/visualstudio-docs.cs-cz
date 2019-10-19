---
title: 'Idebugapplication110 –:: CallableWaitForHandles | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575077"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Počká, dokud nebudou žádné ze zadaných popisovačů signalizaci, a umožnit tak odeslání volání mezi vlákny do tohoto vlákna. Tato metoda musí být volána z vlákna ladicího programu.  
  
> [!IMPORTANT]
> [Rozhraní idebugapplication110 –](../../winscript/reference/idebugapplication110-interface.md) je implementováno pomocí PDM v 11.0 a větší. Nachází se v souboru activdbg100.h.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handleCount`  
 Počet popisovačů, na které se má čekat.  
  
 `pHandles`  
 Sada obslužných rutin, na které se má čekat.  
  
 `pIndex`  
 Je-li hodnota HRESULT nastavena na hodnotu S_OK, je index `pHandles` pro popisovač, který byl signalizována.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplication110 – rozhraní](../../winscript/reference/idebugapplication110-interface.md)