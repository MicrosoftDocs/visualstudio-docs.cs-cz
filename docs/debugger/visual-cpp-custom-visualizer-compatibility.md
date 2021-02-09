---
title: Visual C/C++ – kompatibilita vlastního Vizualizátor
description: Nová funkce v aplikaci Visual Studio 2019 nemusí být kompatibilní se staršími doplňky C/C++ Expression vyhodnocovací doplňky a vlastními vizualizacemi. Podrobnosti najdete v tomto článku.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32ad6b4b699f9cfe02739f341a4f9ddf29360f37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884309"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ – kompatibilita vlastního Vizualizátor

Od verze Visual Studio 2019 obsahuje jazyk C++ vylepšený ladicí program, který používá externí proces 64 pro hostování komponent náročných na paměť. V rámci této aktualizace je nutné aktualizovat některá rozšíření vyhodnocovacího filtru výrazů C/C++, aby byly kompatibilní s novým ladicím programem.

Pokud aktuálně používáte starší doplněk c/c++ EE nebo vlastní Vizualizér c/c++, můžete vypnout použití tohoto externího procesu tak, že v části **nástroje** provedete  >    >  **ladění** možností a pak zrušíte výběr možnosti **načíst symboly ladění v externím procesu (pouze nativní)**. Pokud tuto možnost zrušíte, dojde k výraznému nárůstu využití paměti v rámci procesu IDE (devenv.exe). Pokud tedy očekáváte ladění velkých projektů, doporučujeme pracovat s vlastníkem rozšíření, aby byl kompatibilní s touto možností ladění.

Pokud jste vlastníkem staršího doplňku C/C++ EE nebo C/C++ vlastní vizualizér, najdete další informace o tom, jak zacházet s načtením rozšíření v pracovním procesu na [wikiwebu Concord pro Ukázky rozšiřitelnosti](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Můžete také najít [ukázku vlastního Vizualizér C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).