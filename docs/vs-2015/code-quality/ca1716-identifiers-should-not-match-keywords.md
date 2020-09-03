---
title: 'CA1716: identifikátory by neměly odpovídat klíčovým slovům | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 67a3588a857a0eea7d338217f975ed593dfdad52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543699"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Identifikátory by se neměly shodovat s klíčovými slovy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategorie|Microsoft. pojmenování|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Název oboru názvů, typ nebo člen viritual nebo člen rozhraní odpovídá rezervovanému klíčovému slovu v programovacím jazyce.

## <a name="rule-description"></a>Popis pravidla
 Identifikátory pro obory názvů, typy a členy virtuálních a rozhraní by neměly odpovídat klíčovým slovům, která jsou definována jazyky, které cílí na modul CLR (Common Language Runtime). V závislosti na použitém jazyce a klíčovém slovu, chybách kompilátoru a nejednoznačnosti může být knihovna obtížné použít.

 Toto pravidlo kontroluje klíčová slova v následujících jazycích:

- Visual Basic

- C#

- C++/CLI

  Porovnávání bez rozlišování velkých a malých písmen se používá pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] klíčová slova a pro ostatní jazyky se používá porovnání rozlišující malá a velká písmena.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Vyberte název, který se nezobrazuje v seznamu klíčových slov.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete potlačit upozornění z tohoto pravidla, pokud jste přesvědčeni, že identifikátor Nezaměňujte uživatele rozhraní API a že je knihovna použitelná ve všech dostupných jazycích v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .
