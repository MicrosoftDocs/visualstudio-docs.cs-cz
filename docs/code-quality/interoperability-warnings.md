---
title: Upozornění na přenositelnost a interoperabilitu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f09ccafb79a87dff5c18bb4af11a12e1b1729a4
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100497"
---
# <a name="portability-and-interoperability-warnings"></a>Upozornění na přenositelnost a interoperabilitu

Upozornění na přenositelnost podporují přenositelnost napříč různými platformami. Upozornění na interoperabilitu podporují interakci s klienty modelu COM.

## <a name="in-this-section"></a>V tomto oddílu

| Pravidlo | Popis |
| - | - |
| [CA1401: volání nespravovaných kódů by neměla být viditelná](../code-quality/ca1401.md) | Veřejná nebo chráněná metoda ve veřejném typu má atribut System.Runtime.InteropServices.DllImportAttribute (také implementováno pomocí klíčového slova Declare v Visual Basic). Tyto metody by neměly být vystaveny. |
| [CA1416: ověření kompatibility platformy](../code-quality/ca1416.md) | Použití rozhraní API závislých na platformě pro komponentu způsobí, že kód přestane fungovat napříč všemi platformami. |
| [CA1417: Nepoužívejte pro `OutAttribute` řetězcové parametry pro volání nespravovaného volání.](../code-quality/ca1417.md) | Řetězcové parametry předávané hodnotou s `OutAttribute` může destabilizovat modul runtime, pokud je řetězec interně řetězec. |
