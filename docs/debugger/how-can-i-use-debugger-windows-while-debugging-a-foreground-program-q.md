---
title: Použít okna ladicího programu při ladění aplikace v popředí | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 759d9a6a3beb55bf72a0f41a93cb26c8c15b0c5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734058"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Jak mohu použít okna ladicího programu během ladění programu na popředí?
## <a name="problem-description"></a>Popis problému
 Snažím se ladit problém s vykreslováním obrazovky. Chcete-li tento problém vyřešit, je nutné ponechat program v popředí, což znamená, že nemám přístup k ladicím systémům. Co mám udělat?

## <a name="solution"></a>Řešení
 Pokud máte druhý počítač, můžete použít vzdálené ladění. Při instalaci dvou počítačů můžete sledovat vykreslování obrazovky na vzdáleném počítači při provozování ladicího programu na hostiteli. Další informace o vzdáleném ladění naleznete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

## <a name="see-also"></a>Viz také:
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)