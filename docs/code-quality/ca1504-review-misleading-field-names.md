---
title: 'CA1504: Revize zavádějících názvů polí'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dae321a15de10063352a00980879f35e10cfb9bb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887318"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Revize zavádějících názvů polí

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft.Maintainability|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Název pole instance začíná řetězcem "s_" a název `static` (`Shared` v [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pole začíná předponou "m_".

## <a name="rule-description"></a>Popis pravidla
 Názvy polí, které začínají předponou "s_" jsou spojeny s statických dat mnoha uživateli. Podobně jsou spojeny s data instance (člen) názvy polí, které začínají předponou "m_". Snadněji udržována kódu názvy by měly dodržovat obecně používaných konvence.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přejmenuje pole pomocí příslušné předpony. Pole souhlas s příponou aktuální přidáním nebo odebráním můžete také nastavit `static` modifikátor.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.