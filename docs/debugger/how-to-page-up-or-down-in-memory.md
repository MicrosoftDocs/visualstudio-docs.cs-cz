---
title: O stránku nahoru nebo dolů v paměti | Microsoft Docs
description: Pokud chcete zobrazit obsah paměti v okně paměti nebo v okně zpětný překlad při ladění v aplikaci Visual Studio, přečtěte si téma Jak přejít nahoru nebo dolů v paměti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fc586603caf18261654e5ec8ee437c0875616a7
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148881"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Postupy: O stránku nahoru nebo dolů v paměti

Když zobrazíte obsah paměti v okně **paměti** nebo v okně **zpětný překlad** , můžete pomocí svislého posuvníku přesunout nahoru nebo dolů v paměťovém prostoru.

### <a name="to-page-up-or-down-in-memory"></a>Pro stránku nahoru nebo dolů v paměti

1. Chcete-li posunout stránku dolů (přesunout na vyšší adresu paměti), klikněte na svislý posuvník pod posuvníkem.

2. Chcete-li stránku nahoru (přesunout na nižší adresu paměti), klikněte na svislý posuvník nad jezdcem.

   Všimněte si také, že svislý posuvník funguje nestandardním způsobem. Adresní prostor moderního počítače je velmi velký a je snadné ho ztratit tím, že se podíváme na miniaturu ScrollBar a přetáhnete ji do náhodného umístění. Z tohoto důvodu je palec "springloaded" a vždy zůstává ve středu posuvníku. V aplikacích s nativním kódem můžete stránku nahoru nebo dolů, ale nemůžete se pohybovat volně.

   Ve spravovaných aplikacích je zpětný překlad omezen na jednu funkci a můžete se posouvat normálně.

   Všimněte si, že v dolní části okna se zobrazí vyšší adresy. Chcete-li zobrazit vyšší adresu, je nutné přesunout dolů, ne.

#### <a name="to-move-up-or-down-one-instruction"></a>Přesun nahoru nebo dolů o jednu instrukci

- Klikněte na šipku v horní nebo dolní části svislého posuvníku.

## <a name="see-also"></a>Viz také
- [Okna paměti](../debugger/memory-windows.md)
- [Postupy: Použití okna zpětného překladu](../debugger/how-to-use-the-disassembly-window.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)