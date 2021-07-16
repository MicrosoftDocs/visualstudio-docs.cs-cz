---
description: Zničí instanci třídy VsgDbg.
title: VsgDbg::~VsgDbg (destruktor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ddc942d2ef3a33f1f8d843ff5657f76bb58104c4
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232385"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (destruktor)
Zničí instanci třídy `VsgDbg` . Pokud se aktivně zaznamenávají informace grafiky, soubor protokolu grafiky se finalizuje a zavře a uvolní se prostředky, které byly použity při aktivním zachytávání informací grafiky.

## <a name="syntax"></a>Syntax

```C++
~VsgDbg();
```

## <a name="see-also"></a>Viz také
- [VsgDbg::VsgDbg (konstruktor)](vsgdbg-vsgdbg-constructor.md)
