---
title: Pravidla dokumentace
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- rules, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f4ec6a0dd154dae89145add26c60a8b1322a444
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808649"
---
# <a name="documentation-rules"></a>Pravidla dokumentace

Pravidla dokumentace podporují psaní dobře dokumentovaných knihoven pomocí správného používání [dokumentačních komentářů XML](/dotnet/csharp/codedoc) pro externě viditelná rozhraní API.

## <a name="in-this-section"></a>V této části

| Pravidlo | Popis |
| - | - |
| [CA1200: Nepoužívejte značky cref s předponou](../code-quality/ca1200.md) | Atribut [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) v dokumentaci XML označuje označení "odkaz na kód". Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost. Vyhněte se použití `cref` značek s předponami, protože brání kompilátoru v ověřování odkazů. Zároveň zabrání integrovanému vývojovému prostředí (IDE) sady Visual Studio najít a aktualizovat tyto odkazy na symboly během refaktoringu. |

## <a name="see-also"></a>Viz také

- [Pravidla analýzy kódu](../code-quality/code-analysis-for-managed-code-warnings.md)
