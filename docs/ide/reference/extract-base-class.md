---
title: Extrakce základní třídy
description: Tento refaktoring extrahuje členy z vybrané třídy do nové základní třídy.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9d7a21bbd3e51ee6a6776ca728a545cbbb731cab
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466274"
---
# <a name="extract-base-class"></a>Extrakce základní třídy

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

Otevře se nové dialogové okno **Extrahovat základní třídu**, kde můžete zadat název základní třídy a její požadované umístění. Můžete vybrat členy, které chcete přenést do nové základní třídy, a zvolit, zda mají být členové abstrakcí, zaškrtnutím políčka ve sloupci vytvořit abstrakt.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
