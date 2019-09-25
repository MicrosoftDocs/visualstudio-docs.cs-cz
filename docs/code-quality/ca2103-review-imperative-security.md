---
title: 'CA2103: Zkontrolujte imperativní zabezpečení'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2792f1cccad26fe5bb073af800a2fcf0ebcb4b4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232987"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Zkontrolujte imperativní zabezpečení

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Metoda používá imperativní zabezpečení a může vytvářet oprávnění pomocí stavové informace nebo návratové hodnoty, která se může změnit, pokud je žádost aktivní.

## <a name="rule-description"></a>Popis pravidla
Imperativní zabezpečení používá spravované objekty k určení oprávnění a akcí zabezpečení během provádění kódu ve srovnání s deklarativním zabezpečením, které používá atributy k ukládání oprávnění a akcí v metadatech. Imperativní zabezpečení je velmi flexibilní, protože můžete nastavit stav objektu oprávnění a vybrat akce zabezpečení pomocí informací, které nejsou k dispozici, dokud nebudete mít čas spuštění. Společně s touto flexibilitou je riziko, že běhové informace, které použijete k určení stavu oprávnění, nezůstanou beze změny, dokud je tato akce platná.

Používejte deklarativní zabezpečení vždy, když je to možné. Deklarativní požadavky je snazší pochopit.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Zkontrolujte imperativní požadavky zabezpečení a ujistěte se, že stav oprávnění nezávisí na informacích, které se mohou měnit, pokud je použito oprávnění.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Pokud se oprávnění nespoléhá na změnu dat, je bezpečné potlačit upozornění od tohoto pravidla. Je však lepší změnit imperativní požadavek na jeho deklarativní ekvivalent.

## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](/dotnet/standard/security/secure-coding-guidelines)
- [Data a modelování](/dotnet/framework/data/index)