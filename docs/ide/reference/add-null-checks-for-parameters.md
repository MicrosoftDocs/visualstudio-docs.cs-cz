---
title: Přidat nulové kontroly pro všechny (parametry)
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74782305"
---
# <a name="add-null-checks-for-all-parameters"></a>Přidání kontrol hodnot null pro všechny parametry 

Toto refaktoring se vztahuje na: 

- C# 

**Co:** Vytvoří a `if` přidá příkazy, které kontrolují neplatnost všech nulovatelných, nekontrolovaných parametrů. 

**Kdy:** Chcete rychle přidat nulové kontroly pro všechny parametry příslušné metody.

**Proč:** Psaní null kontroly pro mnoho parametrů může být časově náročné a opakující se. Použití tohoto refaktoringu je rychlé a dělá program robustnější.  

## <a name="how-to"></a>Postupy 

1. Umístěte ukazatel myši na libovolný parametr v metodě.

2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

   ![Rychlé akce a refaktoringy](media/add-null-checks-for-all-parameters.png)
   
3. Vyberte možnost **Přidat nulové kontroly pro všechny parametry**.

   ![Přidat nulové kontroly pro všechny](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Viz také 

- [Refactoring](../refactoring-in-visual-studio.md)
