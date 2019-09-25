---
title: 'CA1500: Názvy proměnných by neměly odpovídat názvům polí'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fbc3fbeac6d01b718af2022a09bddb92e9c7c2c6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234574"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Názvy proměnných by neměly odpovídat názvům polí

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Kategorie|Microsoft. udržovatelnost|
|Zásadní změna|Při vyvolání pro parametr, který má stejný název jako pole:<br /><br /> -Bez přerušení – Pokud se pole i metoda, která deklaruje parametr, nemůže zobrazit mimo sestavení, bez ohledu na změnu, kterou provedete.<br />-Rozdělení – Pokud změníte název pole a lze jej zobrazit mimo sestavení.<br />– Při změně názvu parametru a metody, která ji deklaruje, lze zobrazit mimo sestavení.<br /><br /> Při vyvolání pro místní proměnnou, která má stejný název jako pole:<br /><br /> -Bez přerušení – Pokud se pole nemůže zobrazit mimo sestavení, bez ohledu na změnu, kterou provedete.<br />-Nerušit – Pokud změníte název místní proměnné a nezměníte název tohoto pole.<br />-Rozdělení – Pokud změníte název pole a může se zobrazit mimo sestavení.|

## <a name="cause"></a>příčina

Metoda instance deklaruje parametr nebo místní proměnnou, jejíž název odpovídá poli instance deklarující typu. Pro zachycení místních proměnných, které porušují pravidlo, musí být testované sestavení sestaveno pomocí ladicích informací a přidružený soubor databáze programu (PDB) musí být k dispozici.

## <a name="rule-description"></a>Popis pravidla

V případě, že název pole instance odpovídá parametru nebo názvu místní proměnné, je pole instance dostupné pomocí `this` klíčového slova (`Me` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), které je uvnitř těla metody. Při údržbě kódu je snadné tento rozdíl zapomenout a předpokládat, že parametr nebo místní proměnná odkazují na pole instance, které vede k chybám. To je užitečné hlavně v případě dlouhých těla metod.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přejmenujte buď parametr nebo proměnnou, nebo pole.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

Následující příklad ukazuje dvě porušení pravidla.

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]