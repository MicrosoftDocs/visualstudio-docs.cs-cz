---
title: 'CA2103: Kontrola imperativního zabezpečení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ade0d10e203752c7412929c6f5f44d9cbfaacfa6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521261"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Zkontrolujte imperativní zabezpečení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Metoda používá imperativní zabezpečení a může vytvářet oprávnění pomocí stavové informace nebo návratové hodnoty, která se může změnit, pokud je žádost aktivní.

## <a name="rule-description"></a>Popis pravidla
 Imperativní zabezpečení používá spravované objekty k určení oprávnění a akcí zabezpečení během provádění kódu ve srovnání s deklarativním zabezpečením, které používá atributy k ukládání oprávnění a akcí v metadatech. Imperativní zabezpečení je velmi flexibilní, protože můžete nastavit stav objektu oprávnění a vybrat akce zabezpečení pomocí informací, které nejsou k dispozici, dokud nebudete mít čas spuštění. Společně s touto flexibilitou je riziko, že běhové informace, které použijete k určení stavu oprávnění, nezůstanou beze změny, dokud je tato akce platná.

 Používejte deklarativní zabezpečení vždy, když je to možné. Deklarativní požadavky je snazší pochopit.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Zkontrolujte imperativní požadavky zabezpečení a ujistěte se, že stav oprávnění nezávisí na informacích, které se mohou měnit, pokud je použito oprávnění.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud se oprávnění nespoléhá na změnu dat, je bezpečné potlačit upozornění od tohoto pravidla. Je však lepší změnit imperativní požadavek na jeho deklarativní ekvivalent.

## <a name="see-also"></a>Viz také
 [Pokyny k zabezpečení kódování](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [a modelování dat](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
