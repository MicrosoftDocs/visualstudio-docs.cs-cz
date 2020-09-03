---
title: Přidat kontroly null pro všechny (parametry)
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74782305"
---
# <a name="add-null-checks-for-all-parameters"></a>Přidání kontrol hodnot null pro všechny parametry 

Tento refaktoring platí pro: 

- C# 

**Co:** Vytvoří a přidá `if` příkazy, které kontrolují hodnotu null všech nezaškrtnutých parametrů s možnou hodnotou null. 

**Když:** Chcete rychle přidat kontroly hodnoty null u všech použitelných parametrů metody.

**Proč:** Zápis prázdných kontrol pro mnoho parametrů může být časově náročný a opakující se. Použití tohoto refaktoringu je rychlé a díky tomu je program robustnější.  

## <a name="how-to"></a>Postupy 

1. Umístěte ukazatel myši na libovolný parametr v metodě.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   ![Rychlé akce a refaktoringy](media/add-null-checks-for-all-parameters.png)
   
3. Tuto možnost vyberte, pokud chcete **pro všechny parametry přidat kontroly hodnoty null**.

   ![Přidat kontroly null pro všechny](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Viz také 

- [Refactoring](../refactoring-in-visual-studio.md)
