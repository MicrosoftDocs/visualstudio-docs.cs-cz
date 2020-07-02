---
title: 'CA1810: Inicializujte vloženou statickou pole typu odkazu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c4ad2f4db9290430bb8a378bd264078370ca7b66
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543829"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Inicializujte odkazový typ statického pole vloženě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Typ odkazu deklaruje explicitní statický konstruktor.

## <a name="rule-description"></a>Popis pravidla
 Pokud typ deklaruje explicitní statický konstruktor, kompilátor just-in-time (JIT) ke každé statické metodě a konstruktoru instance tohoto typu přidá kontrolu, zda již byl dříve statický konstruktor zavolán. Statická inicializace se aktivuje, když se přistupuje ke statickému členu nebo když je vytvořená instance typu. Statická inicializace však není aktivována, pokud deklarujete proměnnou typu, ale nepoužijete ji, což může být důležité, pokud se změní globální stav inicializace.

 Když jsou všechna statická data inicializována vložená a explicitní statický konstruktor není deklarován, kompilátory jazyka MSIL (Microsoft Intermediate Language) přidají `beforefieldinit` příznak a implicitní statický konstruktor, který inicializuje statická data, do definice typu MSIL. Když kompilátor JIT narazí na `beforefieldinit` příznak, většinou se nepřidá kontrola statického konstruktoru. Statická inicializace je zaručena v určitou dobu před tím, než dojde ke statickým polím, ale ne před vyvoláním statické metody nebo konstruktoru instance. Všimněte si, že statická inicializace může nastat kdykoli po deklarování proměnné typu.

 Kontroly statického konstruktoru mohou snížit výkon. Statický konstruktor se často používá pouze k inicializaci statických polí. v takovém případě je nutné zajistit, aby před prvním přístupem ke statickému poli došlo ke statické inicializaci. `beforefieldinit`Chování je vhodné pro tyto a většinu ostatních typů. Je nevhodný pouze v případě, že statická inicializace má vliv na globální stav a jedna z následujících hodnot je true:

- Vliv na globální stav je nákladný a není povinný, pokud se typ nepoužívá.

- K globálním dopadům na stav lze získat přístup bez přístupu ke statickým polím typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, inicializujte všechna statická data při deklaraci a statický konstruktor odeberte.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění, pokud výkon není obavou; nebo v případě, že změny globálních stavů, které jsou způsobeny statickou inicializací jsou nákladné nebo musí být zaručeny, aby vznikly před voláním statické metody typu nebo je vytvořena instance typu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, `StaticConstructor` , který porušuje pravidlo a typ, `NoStaticConstructor` , který nahrazuje statický konstruktor s vloženou inicializací pro splnění pravidla.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Všimněte si přidání `beforefieldinit` příznaku do definice MSIL pro `NoStaticConstructor` třídu.

 **Třída Public auto ANSI StaticConstructor** **rozšiřuje [mscorlib] System. Object** 
 **{** 
 **}//End třídy StaticConstructor** 
 **. Public auto NoStaticConstructor ANSI beforefieldinit** **rozšiřuje [mscorlib] System. Object** 
 **{** 
 **}//End třídy NoStaticConstructor** .
## <a name="related-rules"></a>Související pravidla
 [CA2207: Inicializujte statická pole s typem hodnoty vloženě](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
