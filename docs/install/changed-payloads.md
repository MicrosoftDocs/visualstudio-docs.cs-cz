---
title: Změna zatížení balíčku po vydání
description: Při vytváření rozložení se dozvíte, jak zjistit, jestli se po odeslání vydané verze nezměnily datové části balíčku.
ms.date: 05/22/2019
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 135a89534b17a509d75616b0819dae112901fef3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419247"
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
