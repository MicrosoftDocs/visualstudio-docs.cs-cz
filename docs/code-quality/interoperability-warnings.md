---
title: Upozornění na přenositelnost a interoperabilitu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- rules, portability
- interoperability rules
- rules, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a456f4a24339b6cba5aeec2c9fe64ad3ee278b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808597"
---
# <a name="portability-and-interoperability-rules"></a>Pravidla přenositelnosti a interoperability

Pravidla přenositelnosti podporují přenositelnost napříč různými platformami. Pravidla interoperability podporují interakci s klienty modelu COM.

## <a name="in-this-section"></a>V tomto oddílu

| Pravidlo | Popis |
| - | - |
| [CA1401: volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401.md) | Veřejná nebo chráněná metoda ve veřejném typu má atribut System.Runtime.InteropServices.DllImportAttribute (také implementováno pomocí klíčového slova Declare v Visual Basic). Tyto metody by neměly být vystaveny. |
| [CA1416: Ověřit kompatibilitu platformy](../code-quality/ca1416.md) | Použití rozhraní API závislých na platformě pro komponentu způsobí, že kód přestane fungovat napříč všemi platformami. |
| [CA1417: Nepoužívejte pro `OutAttribute` řetězcové parametry pro volání nespravovaného volání.](../code-quality/ca1417.md) | Řetězcové parametry předávané hodnotou s `OutAttribute` může destabilizovat modul runtime, pokud je řetězec interně řetězec. |
