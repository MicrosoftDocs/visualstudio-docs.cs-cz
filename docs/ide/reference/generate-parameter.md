---
title: Generovat refaktoring parametrů
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
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094364"
---
# <a name="generate-parameter"></a>Vygenerování parametru

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Automaticky generuje parametr metody.

**Kdy:** Odkazujete na proměnnou v metodě, která neexistuje v aktuálním kontextu a obdrží chybu; můžete vygenerovat parametr jako opravu kódu. 

**Proč:** Podpis metody můžete rychle upravit bez ztráty kontextu.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu proměnné a stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
1. Vyberte **Generovat parametr**.

   ![Vygenerování parametru](media/generate-parameter.png) 

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
