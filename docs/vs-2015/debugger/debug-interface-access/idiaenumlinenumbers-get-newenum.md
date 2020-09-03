---
title: 'IDiaEnumLineNumbers:: get__NewEnum | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::get__NewEnum method
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 409f0234c4dbe81f6be0928caf458839baa2cefb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190129"
---
# <a name="idiaenumlinenumbersget__newenum"></a>IDiaEnumLineNumbers::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> verzi tohoto enumerátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 mimo Vrátí `IUnknown` rozhraní, které představuje <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> verzi tohoto enumerátoru.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
