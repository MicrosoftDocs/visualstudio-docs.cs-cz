---
title: 'IDiaStackFrame:: get_functionStart | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_functionStart
ms.assetid: e3e6e88b-0594-4d82-9457-480239a2e85a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46e9046f53b1a7b6e7af4dc86e9e4ac693bf618a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190585"
---
# <a name="idiastackframeget_functionstart"></a>IDiaStackFrame::get_functionStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte příznak, který označuje, zda blok obsahuje vstupní bod funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrátí, `TRUE` zda rámec zásobníku obsahuje vstupní bod funkce. v opačném případě vrátí hodnotu `FALSE` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . Vrátí hodnotu, `S_FALSE` Pokud vlastnost není podporována. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
