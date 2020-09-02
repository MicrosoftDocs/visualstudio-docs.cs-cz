---
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5c1225d75ea857fe34906daeb4792524fde4bc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538808"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přijímá zpětná volání z procesu hledání symbolů DIA, což umožňuje, aby bylo omezení uloženo na proces vyhledávání.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Kromě metod v rozhraní [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) toto rozhraní zpřístupňuje následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Určuje, zda je v původním adresáři pro ladění hledán soubor. pdb.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Určuje, zda je v cestě, kde je umístěn soubor. exe, povolen soubor. pdb.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Určuje, zda je povoleno hledání informací o ladění ze souborů. dbg.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Určuje, zda je v kořenovém adresáři systému povoleno hledání souborů. pdb.|  
  
## <a name="remarks"></a>Poznámky  
 Klientská aplikace implementuje toto rozhraní a poskytuje odkaz na něj ve volání metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) . Nezapomeňte implementovat i všechny metody v rozhraní [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2. h  
  
 Knihovna: diaguids. lib  
  
 KNIHOVNA DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
