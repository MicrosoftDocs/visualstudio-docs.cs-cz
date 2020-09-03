---
title: Visual C/C++ – kompatibilita vlastního Vizualizátor
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72430616"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ – kompatibilita vlastního Vizualizátor

Od verze Visual Studio 2019 obsahuje jazyk C++ vylepšený ladicí program, který používá externí proces 64 pro hostování komponent náročných na paměť. V rámci této aktualizace je nutné aktualizovat některá rozšíření vyhodnocovacího filtru výrazů C/C++, aby byly kompatibilní s novým ladicím programem.

Pokud aktuálně používáte starší doplněk c/c++ EE nebo vlastní Vizualizér c/c++, můžete vypnout používání tohoto externího procesu tak, že v části nástroje provedete **Tools**  >  **Options**  >  **ladění**možností a pak zrušíte výběr možnosti **načíst ladicí symboly v externím procesu (pouze nativní)**. Pokud tuto možnost zrušíte, dojde k výraznému nárůstu využití paměti v rámci procesu IDE (devenv.exe). Pokud tedy očekáváte ladění velkých projektů, doporučujeme pracovat s vlastníkem rozšíření, aby byl kompatibilní s touto možností ladění.

Pokud jste vlastníkem staršího doplňku C/C++ EE nebo vlastního Vizualizér C/C++, můžete najít další informace o tom, jak se zacházet na načítání rozšíření v pracovním procesu na [wikiwebu Concording Samples](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Můžete také najít [ukázku vlastního Vizualizér C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).