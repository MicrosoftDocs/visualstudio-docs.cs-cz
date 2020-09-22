---
title: Přemístit instrumentované binární soubory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 13fa5c3413e620e43a695e205a0523dce23e90b4
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851343"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Postupy: přemístění instrumentních binárních souborů

Během instrumentace jsou testy vloženy do binárního souboru pro měření výkonu aplikace. Zvolením možnosti přemístit instrumentované binární soubory se zainstrumentuje a umístí se do zadaného umístění kopie původního binárního souboru. Tato možnost je užitečná v případě, že nechcete, aby Profiler přejmenoval původní binární soubor. Pokud binární soubor není přemístěný, původní verze binárního souboru bude přepsána.

## <a name="to-relocate-instrumented-binary"></a>Přemístění instrumentované binární

1. V **prohlížeč výkonu**klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.

2. Na **stránkách vlastností**klikněte na **binární** vlastnosti.

3. Zaškrtněte políčko **přemístit instrumentované binární soubory** .

4. Zadejte umístění pro instrumentované binární soubory.

## <a name="see-also"></a>Viz také

[Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md) 
 [VSInstr](../profiling/vsinstr.md)
