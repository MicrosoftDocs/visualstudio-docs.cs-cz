---
title: Zachovat fokus při procházení vaší aplikace | Microsoft Docs
Description: Vzdálené ladění použijte, pokud chcete, aby se váš program při ladění problému s aktivací okna zachoval na fokus.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d533d524effe5ba055116d926d7cc5ba9632a6b
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398321"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>Jak zachovám fokus při procházení vaší aplikace?
## <a name="description"></a>Popis
 Má program problém s aktivací okna. Rozkrokování programu pomocí ladicího programu je v konfliktu s možností reprodukování problému, protože program neustále ztratí fokus. Existuje nějaký způsob, jak se tomu vyhnout?

## <a name="solution"></a>Řešení
 Pokud máte druhý počítač, použijte vzdálené ladění. Program můžete provozovat na vzdáleném počítači a spustit ladicí program na hostiteli. Další informace naleznete v tématu [How to: SELECT a Remote Computer](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100)).

## <a name="see-also"></a>Viz také
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)