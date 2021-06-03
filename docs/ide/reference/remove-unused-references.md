---
title: Odebrat nepoužívané odkazy
description: Naučte se vyčistit odkazy na projekt a balíčky NuGet, které neobsahují použití pomocí příkazu New Remove nepoužité odkazy.
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 707769229ad7bc1864a135bade1df918d4b27847
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352086"
---
# <a name="remove-unused-references"></a>Odebrat nepoužívané odkazy

Tento refaktoring platí pro:

- C#
- Visual Basic

**Co:** Umožňuje odebrat nepoužívané odkazy.

**Když:** Chcete vyčistit odkazy na projekt a balíčky NuGet, které nemají žádné použití. 

**Proč:** Odebrání odkazů na projekt, které nemají žádné využití, může přispět k úsporám místa a zkrácení doby spuštění aplikace, protože čas potřebný k načtení každého modulu trvá a vyhnout se tak, že se nepoužijí metadata načtení kompilátoru, která nikdy nebudou použita.

## <a name="how-to"></a>Postupy

1. Klikněte pravým tlačítkem na uzel název projektu nebo závislosti v Průzkumník řešení.

2. Vyberte **Odebrat nepoužívané odkazy**.

    ![Odebrat nepoužívané odkazy – příkaz](media/remove-unused-references-command.png)

3. Otevře se dialogové okno **Odebrat nepoužívané odkazy** se zobrazením odkazů, které neobsahují použití ve zdrojovém kódu. Nepoužívané odkazy budou předem vybrány pro odebrání s možností zachovat odkazy výběrem `Keep` z rozevírací nabídky akce.

    ![Odebrat nepoužívané dialogy odkazů](media/remove-unused-references-dialog.png)

5. Kliknutím `Apply` odeberete vybrané odkazy. 

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)