---
title: Když se po vydání změní datové části balíku
description: Při vytváření rozložení se dozvíte, jak zjistit, zda se datové části balíčků změnily po odeslání verze.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114586"
---
# <a name="package-payload-changes"></a>Změny v datové části balíčku

Některé datové části balíčků se mohou změnit po odeslání verze. Když vy nebo někdo jiný vytvoří rozložení, toto chování může mít za následek různé rozložení obsahu, v závislosti na tom, kdy bylo vytvořeno rozložení.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Ověření, zda rozložení obsahuje změny datové části balíčku

Zde je návod, jak zjistit, zda dříve vytvořené rozložení získalo datové části balíčku, které byly změněny po odeslání verze:

1. Otevřete protokol nastavení. Protokol je obvykle `%TEMP%\dd_setup_[date].log` na `[date]` kde je, když `yyyyMMddHHmmss` operace rozložení spuštěna ve formátu.

2. Vyhledejte řádek v protokolu, který je strukturován jako následující text:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Potom vyhledejte řádky později v protokolu, které označují, že stahování proběhlo úspěšně pro [cesta]. Mohou vypadat podobně jako následující text:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Viz také

* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
