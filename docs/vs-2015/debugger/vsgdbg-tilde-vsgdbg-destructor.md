---
title: 'VsgDbg:: ~ VsgDbg (destruktor) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200293"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (destruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Odstraní instanci `VsgDbg` třídy. Pokud se informace o grafech aktivně zaznamenávají, je soubor protokolu grafiky finalizován a uzavřen a prostředky, které byly použity při aktivním zaznamenávání grafických informací, jsou uvolněny.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Viz také  
 [VsgDbg::VsgDbg (konstruktor)](../debugger/vsgdbg-vsgdbg-constructor.md)
