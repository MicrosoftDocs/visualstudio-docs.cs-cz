---
title: Vytváření vlastních zobrazení dat v ladicím programu | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63dc11736e92013719fcda2bae0ba9599a8835aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569002"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Vytváření vlastních zobrazení dat v ladicím programu sady Visual StudioC#(Visual Basic, C++)

Ladicí program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poskytuje mnoho nástrojů pro kontrolu a úpravu stavu programu. Většina těchto nástrojů funguje pouze v režimu pozastavení.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Vytváření vlastních zobrazení dat v oknech proměnných a v datových tipech

 Mnohé z [oken ladicího programu](../debugger/debugger-windows.md), například okna **Automatické** hodnoty a **kukátka** , umožňují kontrolovat proměnné. Můžete přizpůsobit způsob, C++ jakým jsou typy, spravované objekty a vlastní typy zobrazeny v oknech proměnných ladicího programu a v části [datatipů](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Další informace najdete v tématech [vytváření vlastních zobrazení C++ objektů](../debugger/create-custom-views-of-native-objects.md) a [vytváření vlastních zobrazení spravovaných objektů](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Vytvořit vlastní vizualizace

 Vizualizace umožňují zobrazit obsah objektu nebo proměnné smysluplným způsobem. V ladicím programu sady Visual Studio se Vizualizér odkazuje na různá okna, která můžete otevřít pomocí ikony lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru") . Například Vizualizér HTML ukazuje, jak by byl řetězec jazyka HTML interpretován a zobrazen v prohlížeči. K vizualizacím můžete přistupovat z datových tipů, okna **kukátka** , okna **Automatické** hodnoty a okna **místních** hodnot. V dialogovém okně **QuickWatch** je také k dispozici Vizualizér. Další informace najdete v tématu [Vytvoření vlastních vizualizací](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Viz také:

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [okno Příkaz](../ide/reference/command-window.md)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
