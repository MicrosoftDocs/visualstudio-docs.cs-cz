---
title: Upozornění dokumentace
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
ms.openlocfilehash: 00b42dc20b228e30a9b2632a0525a1ec8a9ddbb1
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079209"
---
# <a name="documentation-warnings"></a>Upozornění dokumentace

Upozornění dokumentace podporují psaní dobře dokumentovaných knihoven pomocí správného používání [dokumentačních komentářů XML](https://docs.microsoft.com/dotnet/csharp/codedoc) pro externě viditelná rozhraní API.

## <a name="in-this-section"></a>V tomto oddílu

| Pravidlo | Popis |
| - | - |
| [CA1200: Nepoužívejte značky cref s předponou.](../code-quality/ca1200.md) | Atribut [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) v dokumentaci XML označuje označení "odkaz na kód". Určuje, zda je vnitřní text značky prvkem kódu, jako je například typ, metoda nebo vlastnost. Vyhněte `cref` se použití značek s předponami, protože brání kompilátoru v ověřování odkazů. Zároveň zabrání integrovanému vývojovému prostředí (IDE) sady Visual Studio najít a aktualizovat tyto odkazy na symboly během refaktoringu. |

## <a name="see-also"></a>Viz také:

- [Upozornění analýzy kódu](../code-quality/code-analysis-for-managed-code-warnings.md)
