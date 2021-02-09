---
title: Zobrazení oken | Microsoft Docs
description: Zobrazení systému Windows zobrazuje strom všech oken a ovládacích prvků. Použijte ho jako výchozí bod, abyste získali informace o systému Windows, které vás zajímají.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.windowsview
helpviewer_keywords:
- Windows view
ms.assetid: 154786ce-c803-4bfb-8198-f7962a900363
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 34a66e9c2728798330b52f87afe8ecdea8733508
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906329"
---
# <a name="windows-view"></a>Zobrazení oken
Při prvním otevření nástroje Spy + + zobrazí Windows zobrazení strom všech oken a ovládacích prvků v systému. Zobrazí se popisovač okna a název třídy. Aktuální okno plochy je v horní části stromu. Všechny ostatní okna jsou podřízené počítači a jsou uvedeny v závislosti na standardní hierarchii oken. Okna na stejné úrovni se zobrazí v seznamech expansible odsazených pod svými rodičemi.

 Následující obrázek ukazuje typické zobrazení Windows Spy + + s nejrozšířenější uzlem.

 ![Zobrazení Spy&#43;&#43; Windows](../debugger/media/spy--_windowsview.png "_WindowsView nástroje Spy + +") Windows Spy + + zobrazení oken

 Aktuální okno plochy je v horní části stromu. Všechna ostatní okna jsou podřízená část plochy a jsou uvedena v závislosti na standardní hierarchii oken, u oken na stejné úrovni seřazených podle pořadí Z. Můžete rozbalit nebo sbalit libovolný nadřazený uzel stromu kliknutím na symbol + nebo symbol vedle uzlu.

 Když má zobrazení systému Windows fokus, můžete pomocí nástroje Finder v [dialogovém okně hledání v okně](../debugger/window-search-dialog-box.md) zobrazit informace z libovolného okna otevřeného v systému.

## <a name="in-this-section"></a>V tomto oddílu
 [Postupy: používání vyhledávacího nástroje](../debugger/how-to-use-the-finder-tool.md) Ukazuje, jak tento nástroj skenuje okna pro vlastnosti nebo zprávy.

 [Postupy: hledání okna v zobrazení Windows](../debugger/how-to-search-for-a-window-in-windows-view.md) Vysvětluje, jak najít konkrétní okno v zobrazení systému Windows.

 [Postupy: zobrazení vlastností okna](../debugger/how-to-display-window-properties.md) m v postupech pro otevření dialogového okna vlastností okna.

## <a name="related-sections"></a>Související oddíly
 [Zobrazení nástroje Spy + +](../debugger/spy-increment-views.md) Vysvětluje zobrazení stromové struktury nástroje Spy + + pro Windows, zprávy, procesy a vlákna.

 [Pomocí nástroje Spy + +](../debugger/using-spy-increment.md) Zavádí nástroj Spy + + a vysvětluje, jak ho lze použít.

 [Dialogové okno Najít okno](../debugger/find-window-dialog-box.md) Slouží k zobrazení vlastností nebo zpráv z konkrétního okna.

 Okno [hledání oken](../debugger/window-search-dialog-box.md) Slouží k vyhledání uzlu pro konkrétní okno v zobrazení systému Windows.

 [Dialogové okno Vlastnosti okna](../debugger/window-properties-dialog-box.md) Slouží k zobrazení vlastností okna vybraného v zobrazení Windows.

 [Referenční dokumentace nástroje Spy + +](../debugger/spy-increment-reference.md) Obsahuje oddíly popisující jednotlivé nabídky a dialogová okna nástroje Spy + +.