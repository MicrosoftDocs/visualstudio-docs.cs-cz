---
title: 'Postup: Přemístění instrumentovaných binárních souborů | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: cddbb0b3e27b841441937b7256ea32d722e25f5e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774897"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Postup: Přemístění instrumentovaných binárních souborů

Během instrumentace jsou do binárního souboru vloženy sondy pro měření výkonu aplikace. Pokud se rozhodnete přemístit instrumentovaný binární soubor, je kopie původníbinární soubor instrumentované a dát do zadaného umístění. Tato možnost je užitečná, pokud nechcete, aby profiler přejmenoval původní binární soubor. Pokud binární soubor není přemístěn, původní verze binárního souboru je přepsána.

## <a name="to-relocate-instrumented-binary"></a>Chcete-li přemístit instrumentované binární

1. V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na relaci výkonu a potom klepněte na příkaz **Vlastnosti**.

2. Na **stránkách vlastností**klepněte na **vlastnosti Binární.**

3. Zaškrtněte **políčko Přemístit instrumentované binární soubory.**

4. Zadejte umístění instrumentovaného binárního souboru.

## <a name="see-also"></a>Viz také

[Konfigurace výkonových relací](../profiling/configuring-performance-sessions.md)
[VSInstr](../profiling/vsinstr.md)
