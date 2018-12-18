---
title: Cv_access_e – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4491aa77eaf27915dcda1654ef00dca351804ff1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745645"
---
# <a name="cvaccesse"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Určuje obor viditelnost (úroveň přístupu) členské funkce a proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementy  
 CV_private  
 Člen má soukromý přístup.  
  
 CV_protected  
 Člen chrání přístup.  
  
 CV_public  
 Člen má veřejný přístup.  
  
## <a name="remarks"></a>Poznámky  
 `friend` Specifikátor přístupu zde není obsažena vzhledem k tomu, že se obvykle používá funkce bez členů, které mají přístup k soukromým a chráněným elementy třídy. Použití [idiasymbol::get_symtag –](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metodu pro hledání symbolů se `SymTagFriend` přístup.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: cvconst.h  
  
## <a name="see-also"></a>Viz také  
 [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol::get_access –](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)



