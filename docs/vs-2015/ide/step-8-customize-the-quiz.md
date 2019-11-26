---
title: 'Krok 8: Přizpůsobení kvízu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ded65e85a2ae11e96c21fdd852ea12daa4bbcdf4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299991"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Přizpůsobení kvízu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V poslední části tutoriálu prozkoumáte několik způsobů, jak kvíz přizpůsobit a rozšíříte si již nabyté znalosti. Například se zamyslíte nad tím, jak program vytvoří problém náhodného dělení, jehož odpovědí není nikdy zlomek. Chcete-li získat další informace, převeďte `timeLabel` ovládacího prvku jinou barvu a poskytněte pomocnému kvízu.

### <a name="to-customize-the-quiz"></a>Přizpůsobení kvízu

- Pokud je v kvízu ponecháno pouze pět sekund, přepněte ovládací prvek **timeLabel** na červen nastavením jeho vlastnosti **BackColor** (`timeLabel.BackColor = Color.Red;`). Resetovat barvu při překročení kvízu.

- Dejte účastníkovi kvízu nápovědu pomocí přehrání zvuku při zadání správné odpovědi do ovládacího prvku NumericUpDown. (Pro každou událost ovládacího prvku `ValueChanged()` je nutné napsat obslužnou rutinu události, která se vyvolá vždy, když účastník kvízu změní hodnotu ovládacího prvku.)

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kurzu, přečtěte si [kurz 3: vytvoření vyhovující hry](../ide/tutorial-3-create-a-matching-game.md).

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si [Krok 7: Přidání problémů násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md).
