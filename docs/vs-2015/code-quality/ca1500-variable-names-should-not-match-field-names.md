---
title: 'CA1500: názvy proměnných by neměly odpovídat názvům polí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5753cc660d626098d234fbce93c0bf0269e52bb3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919040"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Názvy proměnných by neměly odpovídat názvům polí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio naleznete v tématu [CA1500: názvy proměnných by neměly odpovídat názvům polí](/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names).

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Kategorie|Microsoft. udržovatelnost|
|Narušující změna|Při vyvolání pro parametr, který má stejný název jako pole:<br /><br /> -Bez přerušení – Pokud se pole i metoda, která deklaruje parametr, nemůže zobrazit mimo sestavení, bez ohledu na změnu, kterou provedete.<br />-Rozdělení – Pokud změníte název pole a lze jej zobrazit mimo sestavení.<br />– Při změně názvu parametru a metody, která ji deklaruje, lze zobrazit mimo sestavení.<br /><br /> Při vyvolání pro místní proměnnou, která má stejný název jako pole:<br /><br /> -Bez přerušení – Pokud se pole nemůže zobrazit mimo sestavení, bez ohledu na změnu, kterou provedete.<br />-Nerušit – Pokud změníte název místní proměnné a nezměníte název tohoto pole.<br />-Rozdělení – Pokud změníte název pole a může se zobrazit mimo sestavení.|

## <a name="cause"></a>příčina
 Metoda instance deklaruje parametr nebo místní proměnnou, jejíž název odpovídá poli instance deklarující typu. Pro zachycení místních proměnných, které porušují pravidlo, musí být testované sestavení sestaveno pomocí ladicích informací a přidružený soubor databáze programu (PDB) musí být k dispozici.

## <a name="rule-description"></a>Popis pravidla
 Když název pole instance odpovídá parametru nebo názvu místní proměnné, pole instance je dostupné pomocí klíčového slova `this` (`Me` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) v těle metody. Při údržbě kódu je snadné tento rozdíl zapomenout a předpokládat, že parametr nebo místní proměnná odkazují na pole instance, které vede k chybám. To je užitečné hlavně v případě dlouhých těla metod.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přejmenujte buď parametr nebo proměnnou, nebo pole.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dvě porušení pravidla.

 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
