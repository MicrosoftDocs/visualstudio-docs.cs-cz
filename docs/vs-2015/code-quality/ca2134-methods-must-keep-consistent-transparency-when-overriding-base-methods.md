---
title: 'CA2134: Metody musejí zachovávat konzistentní transparentnost, při přepisování základních metod | Dokumentace Microsoftu'
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
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 218114a87b3f81fb4b422852b6d92f952474f668
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844195"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Metody musejí při přepisování základních metod zachovávat konzistentní transparentnost
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Toto pravidlo je vyvoláno, když metoda označená pomocí <xref:System.Security.SecurityCriticalAttribute> přepíše metodu, která je transparentní nebo označená <xref:System.Security.SecuritySafeCriticalAttribute>. Toto pravidlo vyvoláno, když metoda, která je transparentní nebo označená <xref:System.Security.SecuritySafeCriticalAttribute> přepíše metodu označenou atributem <xref:System.Security.SecurityCriticalAttribute>.

 Pravidlo je použito při přepisování virtuální metody nebo implementaci rozhraní.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je vyvoláno při pokusech změňte přístupnost zabezpečení metody dále celým řetězcem dědičnosti. Například pokud virtuální metodu v základní třídě je transparentní nebo bezpečně kritické, pak odvozené třídy musí ji přepište bezpečný a kritický nebo transparentní metoda. Naopak pokud virtuální je kritický pro zabezpečení, odvozené třídy musí přepsat ho na kritickou metodu zabezpečení. Stejné pravidlo platí i pro implementaci metody rozhraní.

 Když kód je JIT kompilaci místo za běhu, takže výpočtu transparentnosti nemá žádné informace o dynamické typu se vynucují pravidla transparentnosti. Výsledek výpočtu transparentnosti proto musí být schopen určit pouze statické typy se zkompilovaný pomocí kompilátoru JIT, bez ohledu na to dynamického typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte průhlednost metody, která je přepisování virtuální metody nebo implementaci rozhraní tak, aby odpovídaly průhlednost virtuální nebo metodu rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění tohoto pravidla. Porušení tohoto pravidla způsobí modul runtime <xref:System.TypeLoadException> pro sestavení, které používají transparentnosti úrovně 2.

## <a name="examples"></a>Příklady

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Viz také
 [Kód transparentní pro zabezpečení, úroveň 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)



