---
title: 'IDiaSymbol:: get_isVirtualInheritance | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72906b92-dd4a-42e3-9b24-b77628fa48c1
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60126527e4c581979d5686696c7f2cbf6ae720eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200705"
---
# <a name="idiasymbolget_isvirtualinheritance"></a>IDiaSymbol::get_isVirtualInheritance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje, zda `this` ukazatel ukazuje na datový člen s virtuální dědičností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT get_isVirtualInheritance(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Ukazatel na `BOOL` , který určuje, zda `this` ukazatel ukazuje na datový člen s virtuální dědičností.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
