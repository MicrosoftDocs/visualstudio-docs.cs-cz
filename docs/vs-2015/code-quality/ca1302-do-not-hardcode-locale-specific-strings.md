---
title: 'CA1302: Nekódujte pevně řetězce závislé národní prostředí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 23f2b807d66662691afaa4805a50b34255a39bdb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842414"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Nekódujte pevně řetězce závislé na národním prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategorie|Microsoft.Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Metoda používá řetězcový literál, který představuje část cesty k určitým složkám systému.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> Výčet obsahuje členy, které odkazují na speciální systémové složky. Umístění těchto složek mohou mít různé hodnoty v různých operačních systémech, uživatel může změnit některé z míst a místa jsou lokalizována. Příklad speciální složky je systémová složka, která je "C:\WINDOWS\system32" na [!INCLUDE[winxp](../includes/winxp-md.md)] ale "C:\WINNT\system32" na [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Metoda vrátí umístění, které jsou přidružené k <xref:System.Environment.SpecialFolder> výčtu. Umístění, které jsou vráceny pomocí <xref:System.Environment.GetFolderPath%2A> jsou lokalizované a vhodné pro aktuálně spuštěný počítač.

 Toto pravidlo tokenizes, které se načítají pomocí cesty ke složkám <xref:System.Environment.GetFolderPath%2A> metoda do úrovní samostatný adresář. Každý řetězcového literálu je ve srovnání s tokeny. Pokud se najde shoda, se předpokládá, že metoda je vytváření řetězec, který označuje umístění systému, který je přidružený k tokenu. Přenositelnost a lokalizovatelnosti <xref:System.Environment.GetFolderPath%2A> metody k získání umístění speciální systémové složky namísto použití řetězcových literálů.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, načtěte umístění pomocí <xref:System.Environment.GetFolderPath%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud řetězcového literálu se nepoužívá k odkazování na jedno z umístění systému, které je přidružené <xref:System.Environment.SpecialFolder> výčtu.

## <a name="example"></a>Příklad
 Následující příklad vytvoří cesta běžné složka dat aplikace, které toto pravidlo generuje upozornění na tři. V dalším kroku příklad načte pomocí cesty <xref:System.Environment.GetFolderPath%2A> metody.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1303: Nepředávejte literály jako lokalizované parametry](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)



