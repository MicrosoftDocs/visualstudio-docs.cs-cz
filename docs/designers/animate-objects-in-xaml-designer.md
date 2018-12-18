---
title: Animace objektů v Návrháři XAML
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: c8f8b1b62634c9da86a6aa152bd48cbd8c712198
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921401"
---
# <a name="animate-objects-in-xaml-designer"></a>Animace objektů v Návrháři XAML

Můžete vytvořit krátké animace, které přesun objektů nebo je objevovat a odhlášení.

Chcete-li začít, vytvořte *storyboard*. Scénář obsahuje jeden nebo více *časové osy*. Nastavit *klíčových snímků* na časové ose označit změny vlastností. Poté při spuštění animace Blend argument interpolaci změny vlastností po určenou dobu. Výsledkem je plynulý přechod. Můžete animace jakákoli vlastnost, která patří do objektu, a to ani v nevizuální vlastnosti.

Následující obrázek znázorňuje storyboard, s názvem **MoveUp**. Časová osa obsahuje klíčových snímků, které označit X a Y pomyslného obdélníku. Když je tato animace spuštěna, rámeček přesune z jednoho místa na jiný bez problémů.

![Scénáře MoveUp v Návrháři XAML](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png)

## <a name="see-also"></a>Viz také

- [Vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)