---
title: 'CA2238: Implementujte správně metody serializace | Dokumentace Microsoftu'
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
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3222deaeac97df8b954853f21eaff40a8244d8ca
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864280"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Implementujte správně metody serializace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio 2017, najdete v části [CA2238: implementujte správně metody serializace](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly) na webu docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Kategorie|Microsoft.Usage|  
|Narušující změna|Rozdělení - metoda je viditelná mimo sestavení.<br /><br /> Pevné – Pokud metoda není viditelná mimo sestavení.|  
  
## <a name="cause"></a>příčina  
 Metoda, která zpracovává událost serializace, nemá správný podpis, návratový typ nebo viditelnost.  
  
## <a name="rule-description"></a>Popis pravidla  
 Metoda je určený obslužnou rutinu události serializace s použitím jedné z následujících atributů událost serializace:  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
  Obslužné rutiny událostí serializace vyžadovat jeden parametr typu <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, vrátí `void`a mít `private` viditelnost.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Chcete-li opravit porušení tohoto pravidla, opravte podpis, návratový typ nebo viditelnost obslužné rutiny události serializace.  
  
## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění  
 Nepotlačujte upozornění na toto pravidlo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje správně deklarované serializace obslužných rutin událostí.  
  
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]  
  
## <a name="related-rules"></a>Související pravidla  
 [CA2236: Volejte metody třídy Base na typech ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementujte správně ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementovat serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Poskytujte metody deserializace pro nepovinné pole](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Zabezpečte serializační konstruktory](../code-quality/ca2120-secure-serialization-constructors.md)

