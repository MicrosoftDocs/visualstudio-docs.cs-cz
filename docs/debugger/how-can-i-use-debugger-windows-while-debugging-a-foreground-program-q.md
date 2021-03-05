---
title: Použít okna ladicího programu při ladění aplikace v popředí | Microsoft Docs
description: Pokud ladíte program, který musí zůstat v popředí, použijte vzdálené ladění, abyste se vyhnuli vložení na pozadí.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 03a143ee2d04227171895bf2b14dff92545b9952
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155091"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Jak mohu použít okna ladicího programu během ladění programu na popředí?
## <a name="problem-description"></a>Popis problému
 Snažím se ladit problém s vykreslováním obrazovky. Chcete-li tento problém vyřešit, je nutné ponechat program v popředí, což znamená, že nemám přístup k ladicím systémům. Co mám udělat?

## <a name="solution"></a>Řešení
 Pokud máte druhý počítač, můžete použít vzdálené ladění. Při instalaci dvou počítačů můžete sledovat vykreslování obrazovky na vzdáleném počítači při provozování ladicího programu na hostiteli. Další informace o vzdáleném ladění naleznete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

## <a name="see-also"></a>Viz také
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
