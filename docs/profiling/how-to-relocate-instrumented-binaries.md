---
title: 'Postupy: přemístění instrumentovaných binárních souborů | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a060506f818ac000611fc0c29988ed324ae89226
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843650"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Postupy: přemístění instrumentovaných binárních souborů

Během instrumentace sondy vloženy do binárního souboru k měření výkonu aplikace. Výběrem přesunovat instrumentované binární je kopii původní binární instrumentovány a put v zadaném umístění. Tato možnost je užitečná, pokud nechcete, aby profileru přejmenovat vašeho původního binární. Pokud není přemístění binárního souboru, původní verze binárního souboru se přepíše.

## <a name="to-relocate-instrumented-binary"></a>Instrumentované binární přesunovat

1. V **prohlížeč výkonu**, klikněte pravým tlačítkem na výkonnostní relace a pak klikněte na tlačítko **vlastnosti**.

2. V **stránky vlastností**, klikněte **binární** vlastnosti.

3. Vyberte **přemístění instrumentovaných binárních souborů** zaškrtávací políčko.

4. Zadejte umístění pro instrumentované binární.

## <a name="see-also"></a>Viz také:

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)  
[VSInstr](../profiling/vsinstr.md)
