---
title: 'VsgDbg:: ~ VsgDbg (destruktor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734798"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (destruktor)
Odstraní instanci `VsgDbg` třídy. Pokud se informace o grafech aktivně zaznamenávají, je soubor protokolu grafiky finalizován a uzavřen a prostředky, které byly použity při aktivním zaznamenávání grafických informací, jsou uvolněny.

## <a name="syntax"></a>Syntax

```C++
~VsgDbg();
```

## <a name="see-also"></a>Viz také
- [VsgDbg::VsgDbg (konstruktor)](vsgdbg-vsgdbg-constructor.md)