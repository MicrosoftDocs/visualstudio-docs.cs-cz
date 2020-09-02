---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778217"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nastaví adresu zatížení pro spustitelný soubor, který odpovídá symbolům v tomto úložišti symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `NewVal`  
 pro Načíst adresu pro spustitelný soubor.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnosti virtuální adresy symbolu (VA) se vypočítávají pomocí hodnoty této metody. Pokud je tato vlastnost nastavená na nenulovou hodnotu, virtuální adresy se nepočítají.  
  
> [!NOTE]
> Tato metoda musí být volána, když získáte objekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) a před tím, než začnete používat objekt, pokud potřebujete použít jakékoli virtuální vlastnosti na symbolech.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
