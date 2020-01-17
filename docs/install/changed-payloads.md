---
title: Změna zatížení balíčku po vydání
description: Při vytváření rozložení se dozvíte, jak zjistit, jestli se po odeslání vydané verze nezměnily datové části balíčku.
ms.date: 05/22/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dec1478314e752ddace8fae822747e7c8e328b70
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114586"
---
# <a name="package-payload-changes"></a>Změny v datové části balíčku

Po odeslání již vydaných verzí může dojít ke změně některých datových částí balíčku. Když vy nebo někdo jiný vytvoří rozložení, může to mít za následek odlišné rozložení obsahu v závislosti na tom, kdy bylo rozložení vytvořeno.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Ověřte, že rozložení zahrnuje změny v datové části balíčku.

Zde je postup, jak zjistit, zda rozložení, které bylo dříve vytvořeno, získalo datové části balíčku, které byly upraveny po odeslání vydané verze:

1. Otevřete protokol instalace. Protokol je obvykle na `%TEMP%\dd_setup_[date].log`, kde `[date]`, když byla operace rozložení zahájena ve formátu `yyyyMMddHHmmss`.

2. Vyhledejte řádek v protokolu, který je strukturován jako následující text:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Pak vyhledejte řádky později v protokolu, které označují, že stahování proběhlo úspěšně pro [cesta]. Mohou vypadat podobně jako následující text:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Viz také:

* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizace na základě síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
