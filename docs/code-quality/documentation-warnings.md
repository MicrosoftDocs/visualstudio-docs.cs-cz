---
title: Upozornění k dokumentaci
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4946c69bbbe4bf1c240967ebd93ef58cfa79e333
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72807107"
---
# <a name="documentation-warnings"></a>Upozornění k dokumentaci

Upozornění dokumentace podporují psaní dobře dokumentovaných knihoven pomocí správného používání [dokumentačních komentářů XML](/dotnet/csharp/codedoc) pro externě viditelná rozhraní API.

## <a name="in-this-section"></a>V této části

| Pravidlo | Popis |
| - | - |
| [CA1200: Nepoužívejte značky cref s předponou](../code-quality/ca1200.md) | Atribut [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) v dokumentaci XML označuje označení "odkaz na kód". Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost. Vyhněte se použití `cref` značek s předponami, protože brání kompilátoru v ověřování odkazů. Zároveň zabrání integrovanému vývojovému prostředí (IDE) sady Visual Studio najít a aktualizovat tyto odkazy na symboly během refaktoringu. |

## <a name="see-also"></a>Viz také

- [Upozornění analýzy kódu](../code-quality/code-analysis-for-managed-code-warnings.md)
