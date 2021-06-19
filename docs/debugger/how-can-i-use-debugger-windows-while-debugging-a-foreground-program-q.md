---
title: Použití oken ladicího programu při ladění aplikace na popředí | Microsoft Docs
description: Pokud ladíte program, který musí zůstat v popředí, použijte vzdálené ladění, abyste zabránili jeho umístění na pozadí.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fce51a1a28a8e03692faeee3ed723627864f4031
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386823"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Jak mohu použít okna ladicího programu během ladění programu na popředí?
## <a name="problem-description"></a>Popis problému
 Pokouším se ladit problém obrazovek. Pokud chcete sledovat tento problém, musím program ponechat v popředí, což znamená, že nemám přístup k oknu ladění. Co mám udělat?

## <a name="solution"></a>Řešení
 Pokud máte druhý počítač, můžete použít vzdálené ladění. Při nastavení se dvěma počítači můžete sledovat obraz obrazovky na vzdáleném počítači, zatímco na hostiteli pracujete s ladicím programem. Další informace o vzdáleném ladění najdete v tématu [Vzdálené ladění.](../debugger/remote-debugging.md)

## <a name="see-also"></a>Viz také
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
