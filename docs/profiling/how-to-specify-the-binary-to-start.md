---
title: 'Postupy: určení binárního souboru spuštění | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87fc4102b3cbd3420f1e5c3b7ea4a067e0d95a0d
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844856"
---
# <a name="how-to-specify-the-binary-to-start"></a>Postupy: určení binárního souboru ke spuštění

K profilu binární soubory například knihovny DLL, je třeba zadat informace v  **\<cíl > stránky vlastností** dialogové okno. Tyto informace označuje, kde je volající aplikace projektu knihovny DLL.

1. V **prohlížeč výkonu**, klikněte pravým tlačítkem na cílový binární soubor a pak klikněte na tlačítko **vlastnosti**.

2. V **stránky vlastností** dialogové okno, klikněte **spusťte** vlastnosti.

3. Vyberte **přepsat vlastnosti projektu** zaškrtávací políčko.

4. V **spustitelný soubor spustit** textové pole, zadejte umístění souborů.

5. V **argumenty** textové pole, zadejte argumenty, které jsou nezbytné ke spuštění aplikace.

6. V **pracovní adresář** textové pole, zadejte umístění adresáře.

7. Click **OK**.

## <a name="see-also"></a>Viz také:

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)