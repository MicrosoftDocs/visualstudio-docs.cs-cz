---
title: Tipy pro ladění vláken v nativním kódu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 7dde94e28f378f0630a78f32ae5e58533729ce0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72728996"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>Tipy k ladění vláken v nativním kódu
Tady je několik tipů, které můžete použít při ladění vláken v nativním kódu:

- Obsah bloku informací o vlákně můžete zobrazit zadáním v okně `@TIB` **kukátka** nebo dialogovém okně **QuickWatch** .

- Můžete zobrazit poslední kód chyby pro aktuální vlákno zadáním `@Err` v okně **kukátka** nebo dialogovém okně **QuickWatch** .

- Funkce běhové knihovny jazyka C (CRT) mohou být užitečné pro ladění vícevláknové aplikace. Další informace najdete v tématu [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg).

## <a name="see-also"></a>Viz také
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)