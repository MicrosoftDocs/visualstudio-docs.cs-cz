---
title: Extrahovat základní třídu
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8eb87ff8e3acc141c49a495b155fb769e03fb89b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402256"
---
# <a name="extract-base-class"></a>Extrahovat základní třídu

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Extrahuje základní třídu.

**Když:** Chcete extrahovat členy z vybrané třídy do nové základní třídy.

**Proč:** Ruční přijímání členů může být časově náročné a z pracovního postupu se můžete dostat. 

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor buď na název třídy, nebo na zvýrazněný člen.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vyberte **Načíst členy do nové základní třídy**.

    ![Extrahovat dialog základní třídy](media/extract-base-class.png)

Otevře se nové dialogové okno **Extrahovat základní třídu** , kde můžete zadat název základní třídy a její požadované umístění. Můžete vybrat členy, které chcete přenést do nové základní třídy, a zvolit, zda mají být členové abstrakcí, zaškrtnutím políčka ve sloupci vytvořit abstrakt.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
