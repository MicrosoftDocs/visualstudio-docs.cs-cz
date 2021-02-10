---
title: Generovat refaktoring parametrů
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring automaticky vygenerovat parametr metody.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 33e2be19e3a5a83d89e722aa0c1a1154c8196939
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968031"
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
