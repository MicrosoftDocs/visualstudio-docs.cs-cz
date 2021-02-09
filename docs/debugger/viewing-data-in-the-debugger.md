---
title: Vytváření vlastních zobrazení dat v ladicím programu | Microsoft Docs
description: Seznamte se s různými způsoby, jak kontrolovat a upravovat stav programu v ladicím programu sady Visual Studio. Patří mezi ně okna Automatické hodnoty a kukátka, tipy a vizualizace.
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d51821597c68a9b8e0c97e4cac3c7dc7ec2b8cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884348"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Vytváření vlastních zobrazení dat v ladicím programu sady Visual Studio (C#, Visual Basic, C++)

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Ladicí program poskytuje mnoho nástrojů pro kontrolu a úpravu stavu programu. Většina těchto nástrojů funguje pouze v režimu pozastavení.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Vytváření vlastních zobrazení dat v oknech proměnných a v datových tipech

 Mnohé z [oken ladicího programu](../debugger/debugger-windows.md), například okna **Automatické** hodnoty a **kukátka** , umožňují kontrolovat proměnné. Můžete přizpůsobit, jak se typy C++, spravované objekty a vlastní typy zobrazují v oknech proměnných ladicího programu a v části [datatipů](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Další informace naleznete v tématu [vytváření vlastních zobrazení objektů C++](../debugger/create-custom-views-of-native-objects.md) a [vytváření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Vytvořit vlastní vizualizace

 Vizualizace umožňují zobrazit obsah objektu nebo proměnné smysluplným způsobem. V ladicím programu sady Visual Studio se Vizualizér odkazuje na různá okna, která můžete otevřít pomocí ikony lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru") . Například Vizualizér HTML ukazuje, jak by byl řetězec jazyka HTML interpretován a zobrazen v prohlížeči. K vizualizacím můžete přistupovat z datových tipů, okna **kukátka** , okna **Automatické** hodnoty a okna **místních** hodnot. V dialogovém okně **QuickWatch** je také k dispozici Vizualizér. Další informace najdete v tématu [Vytvoření vlastních vizualizací](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Okno Příkaz](../ide/reference/command-window.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
