---
title: 'CA2103: Revize naléhavého zabezpečení | Dokumentace Microsoftu'
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
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dd075c4c6edc84422c6c09846d23ef0049d55002
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886550"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Revize naléhavého zabezpečení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Metoda používá imperativní zabezpečení a může vytvářet oprávnění pomocí stavové informace nebo návratové hodnoty, která se může změnit, pokud je žádost aktivní.

## <a name="rule-description"></a>Popis pravidla
 Imperativní zabezpečení používá k určení oprávnění a akce zabezpečení při provádění kódu, ve srovnání s deklarativní zabezpečení, která využívá atributy pro uložení oprávnění a akcí v metadatech spravovaných objektů. Imperativní zabezpečení je velmi flexibilní, protože můžete nastavit stav objektu oprávnění a výběr akce zabezpečení pomocí informace, které nejsou k dispozici až do spuštění. Spolu s, která se dodává flexibilitu riziko, že informace o modulu runtime, který používáte k určení, že stav oprávnění nezůstávat beze změny, dokud akce je v platnosti.

 Používejte deklarativní zabezpečení vždy, když je to možné. Jsou Jednoduší na porozumění deklarativní požadavky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Zkontrolujte požadavky imperativní zabezpečení, abyste měli jistotu, že stav oprávnění nevyžaduje informace, které můžete změnit tak dlouho, dokud se používá oprávnění.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, je-li oprávnění nevyžaduje se měnícími daty. Je však lepší změnit imperativní požadavek na ekvivalentní deklarativní.

## <a name="see-also"></a>Viz také
 [Pokyny pro zabezpečené kódování](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Data a modelování](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



