---
title: 'IDiaSymbol:: get_lexicalParent | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParent method
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b5f9da456282daca52d6c924b62f21e13545928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64809810"
---
# <a name="idiasymbolget_lexicalparent"></a>IDiaSymbol::get_lexicalParent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte odkaz na lexikální nadřízený symbol.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrátí objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje lexikální nadřízený symbol.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 Lexikálním rodičem symbolu je uzavírací funkce nebo modul. Například lexikální nadřízený parametr funkce nebo místní proměnná je funkce samotná, zatímco lexikální nadřízený prvek funkce je modul, ve kterém je definován.  
  
 Možné symboly, které se mohou zobrazit jako lexikální rodiče, jsou zdokumentovány v [lexikální hierarchii typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
