---
title: Visual C/C++ vlastní kompatibilita Vizualizátor
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430616"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ vlastní kompatibilita Vizualizátor

Počínaje verzí sady Visual Studio 2019 C++ obsahuje vylepšený ladicí program, který používá externí 64 proces pro hostování komponent náročných na paměť. V rámci této aktualizace je nutné aktualizovat některá rozšíření vyhodnocovacího filtruC++ C/Expression, aby byly kompatibilní s novým ladicím programem.

Pokud aktuálně používáte starší doplněk C/C++ EE nebo c/C++ vlastní vizualizér, můžete vypnout používání tohoto externího procesu tak, že v **nabídce nástroje** > **Možnosti** > **ladění**a pak zrušíte výběr **ladění zatížení. symboly v externím procesu (pouze nativní)** . Pokud zrušíte výběr této možnosti, dojde k výraznému nárůstu využití paměti v rámci procesu IDE (devenv. exe). Pokud tedy očekáváte ladění velkých projektů, doporučujeme pracovat s vlastníkem rozšíření, aby byl kompatibilní s touto možností ladění.

Pokud jste vlastníkem staršího doplňku C/C++ EE nebo c/C++ vlastní vizualizér, můžete najít další informace o tom, jak se zacházet v nahrávání rozšíření v pracovním procesu na [wikiwebu Concording Samples](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Můžete také najít [ukázku C/C++ vlastní Vizualizér](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).