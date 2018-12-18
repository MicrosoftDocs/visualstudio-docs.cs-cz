---
title: 'CA5350: Nepoužívejte slabé kryptografické algoritmy'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba5e70505db86b1497e625b216da955bba677245
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547851"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nepoužívejte slabé kryptografické algoritmy

|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Kategorie|Microsoft.Cryptography|
|Narušující změna|Pevné|

> [!NOTE]
> Toto upozornění byl naposledy aktualizován. listopadu 2015.

## <a name="cause"></a>příčina

Algoritmy šifrování, jako <xref:System.Security.Cryptography.TripleDES> a algoritmy hash jako <xref:System.Security.Cryptography.SHA1> a <xref:System.Security.Cryptography.RIPEMD160> jsou považovány za slabé.

Tyto kryptografické algoritmy se neposkytuje tolik zajištění zabezpečení jako Modernější protějšky. Kryptografické algoritmy hash <xref:System.Security.Cryptography.SHA1> a <xref:System.Security.Cryptography.RIPEMD160> zadejte méně kolizí odolnost než Modernější algoritmy hash. Šifrovací algoritmus <xref:System.Security.Cryptography.TripleDES> poskytuje méně bity zabezpečení než Modernější šifrovacích algoritmů.

## <a name="rule-description"></a>Popis pravidla

Algoritmy slabé šifrování a hashovací funkce se dnes používají pro z několika důvodů, ale by neměly být použít k zajištění důvěrnosti údajů, které chrání.

Toto pravidlo aktivuje, když zjistí, 3DES, SHA1 nebo RIPEMD160 algoritmy v editoru kódu a vyvolá upozornění pro uživatele.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Použijte kryptograficky silnější možnosti:

- Pro šifrování TripleDES, použijte <xref:System.Security.Cryptography.Aes> šifrování.

- Pro funkce hash SHA1 nebo RIPEMD160, použijte těch, které jsou v [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) řady (třeba <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačit upozornění tohoto pravidla, když úroveň ochrany, třeba dat nevyžaduje záruky zabezpečení.

## <a name="pseudo-code-examples"></a>Příklady pseudo kódu

V době době psaní tohoto textu znázorňuje následující ukázka kódu pseudo vzor, zjistí toto pravidlo.

### <a name="sha-1-hashing-violation"></a>Porušení hashovací algoritmus SHA-1

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();
```

Řešení:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="ripemd160-hashing-violation"></a>RIPEMD160 Hashování porušení

```csharp
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();
```

Řešení:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="tripledes-encryption-violation"></a>Porušení šifrování TripleDES

```csharp
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

Řešení:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```