---
title: 'VsgDbg:: ~ VsgDbg (destruktor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 53d969e6be772b446598c9c3644582684be488a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861345"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (destruktor)
Odstraní instanci `VsgDbg` třídy. Pokud se informace o grafech aktivně zaznamenávají, je soubor protokolu grafiky finalizován a uzavřen a prostředky, které byly použity při aktivním zaznamenávání grafických informací, jsou uvolněny.

## <a name="syntax"></a>Syntax

```C++
~VsgDbg();
```

## <a name="see-also"></a>Viz také
- [VsgDbg::VsgDbg (konstruktor)](vsgdbg-vsgdbg-constructor.md)