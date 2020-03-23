---
title: Generovat soukromé pole z konstruktoru
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
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094027"
---
# <a name="generate-private-field-from-constructor"></a>Generovat soukromé pole z konstruktoru

Toto refaktoring se vztahuje na: 

- C# 

- Visual Basic

**Co:** Generovat soukromé pole z konstruktoru. 

**Kdy:** Chcete rychle přidat soukromé pole z konstruktoru.

**Proč:** Psaní soukromých polí může být časově náročné a opakující se. Použití tohoto refaktoringu je rychlé a dělá program robustnější.

## <a name="how-to"></a>Postupy 

1. Umístěte kurzor na název parametru v rámci konstruktoru.

2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   
3. Vyberte možnost **Vytvořit a inicializovat pole**.

   ![Generovat soukromé pole z konstruktoru](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Viz také 

- [Refactoring](../refactoring-in-visual-studio.md)
