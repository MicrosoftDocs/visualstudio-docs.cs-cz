---
title: Změna zatížení balíčku po vydání
description: Při vytváření rozložení se dozvíte, jak zjistit, jestli se po odeslání vydané verze nezměnily datové části balíčku.
ms.date: 05/22/2019
ms.topic: how-to
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e773ddf85df1d7f71b1ed929b8f942a5f3b36421
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295294"
---
# <a name="package-payload-changes"></a>Změny v datové části balíčku

Po odeslání již vydaných verzí může dojít ke změně některých datových částí balíčku. Když vy nebo někdo jiný vytvoří rozložení, může to mít za následek odlišné rozložení obsahu v závislosti na tom, kdy bylo rozložení vytvořeno.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Ověřte, že rozložení zahrnuje změny v datové části balíčku.

Zde je postup, jak zjistit, zda rozložení, které bylo dříve vytvořeno, získalo datové části balíčku, které byly upraveny po odeslání vydané verze:

1. Otevřete protokol instalace. Protokol je obvykle v `%TEMP%\dd_setup_[date].log` umístění, kde `[date]` je operace rozložení spuštěna ve `yyyyMMddHHmmss` formátu.

2. Vyhledejte řádek v protokolu, který je strukturován jako následující text:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Pak vyhledejte řádky později v protokolu, které označují, že stahování proběhlo úspěšně pro [cesta]. Mohou vypadat podobně jako následující text:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Viz také

* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
