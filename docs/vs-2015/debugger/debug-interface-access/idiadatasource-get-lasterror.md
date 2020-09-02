---
title: 'IDiaDataSource:: get_lastError | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ad0570436dda6ac9ae52325c891b32a563cf6f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547361"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte název souboru pro poslední chybu načtení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 mimo Vrátí řetězec, který obsahuje název souboru. pdb přidružený k Poslední chybě načtení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí poslední kód chyby způsobený operací Load. Vrátí, `E_INVALIDARG` zda `pRetVal` je parametr `NULL` .  
  
## <a name="example"></a>Příklad  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Viz také  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
