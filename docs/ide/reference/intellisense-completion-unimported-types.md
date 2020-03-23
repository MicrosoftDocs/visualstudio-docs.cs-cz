---
title: Dokončení technologie IntelliSense pro neimportované typy
description: Jak používat dokončení technologie IntelliSense pro typy, které `using` jste ještě neimportovali se směrnicí.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094257"
---
# <a name="intellisense-completion-for-unimported-types"></a>Dokončení technologie IntelliSense pro neimportované typy

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Technologie IntelliSense poskytuje dokončení pro neimportované typy.

**Kdy:** Chcete přidat typ, který již má závislost v projektu, ale příkaz importu ještě nebyl přidán do souboru. 

**Proč:** Není nutné ručně přidávat příkaz importu do souboru.

## <a name="how-to"></a>Postupy

1. Jakmile začnete používat typ, který má závislost v projektu, IntelliSense vám dá návrhy.
2. Stiskněte **klávesu Tab**. 

   Příkaz importu bude přidán do souboru.

   ![Dokončení technologie IntelliSense pro neimportované typy](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
