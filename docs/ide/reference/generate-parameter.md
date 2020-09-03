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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094364"
---
# <a name="generate-parameter"></a>Vygenerování parametru

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Automaticky generuje parametr metody.

**Když:** Odkazujete na proměnnou v metodě, která v aktuálním kontextu neexistuje, a zobrazí se chyba. můžete vygenerovat parametr jako opravu kódu. 

**Proč:** Signaturu metody můžete rychle upravit bez ztráty kontextu.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu proměnné a stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
1. Vyberte možnost **Generovat parametr**.

   ![Vygenerování parametru](media/generate-parameter.png) 

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
