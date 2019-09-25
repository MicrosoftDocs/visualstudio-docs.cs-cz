---
title: 'CA5350: Nepoužívejte slabé kryptografické algoritmy'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aecd052e86a4c0366a1a43cb985ad50ab8862d8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236965"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nepoužívejte slabé kryptografické algoritmy

|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Kategorie|Microsoft.Cryptography|
|Zásadní změna|Nenarušující|

> [!NOTE]
> Toto upozornění se naposledy aktualizovalo od listopadu 2015.

## <a name="cause"></a>příčina

Šifrovací algoritmy <xref:System.Security.Cryptography.TripleDES> jako a algoritmy <xref:System.Security.Cryptography.SHA1> hash, jako jsou a <xref:System.Security.Cryptography.RIPEMD160> , se považují za slabé.

Tyto kryptografické algoritmy neposkytují žádné záruky zabezpečení jako pokročilejší protějšky. Kryptografické algoritmy <xref:System.Security.Cryptography.SHA1> hash a <xref:System.Security.Cryptography.RIPEMD160> poskytují méně kolizí proti kolizi než moderní algoritmy hash. Šifrovací algoritmus <xref:System.Security.Cryptography.TripleDES> poskytuje méně bitů zabezpečení než více moderních šifrovacích algoritmů.

## <a name="rule-description"></a>Popis pravidla

Slabé algoritmy šifrování a funkce hash jsou dnes používány z mnoha důvodů, ale neměly by se používat ke zaručení důvěrnosti dat, která chrání.

Pravidlo se aktivuje, když v kódu nalezne algoritmy 3DES, SHA1 nebo RIPEMD160 a vyvolá uživateli upozornění.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Používejte kryptograficky silnější možnosti:

- Pro šifrování TripleDES použijte <xref:System.Security.Cryptography.Aes> šifrování.

- V případě funkcí hash SHA1 nebo RIPEMD160 používejte funkce v rodině [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) (např. <xref:System.Security.Cryptography.SHA512> <xref:System.Security.Cryptography.SHA384> <xref:System.Security.Cryptography.SHA256>,).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačí upozornění od tohoto pravidla, pokud úroveň ochrany potřebná pro data nevyžaduje záruku zabezpečení.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

V době psaní tohoto pravidla znázorňuje následující příklad pseudo kódu ilustrující vzor zjištěný tímto pravidlem.

### <a name="sha-1-hashing-violation"></a>Porušení hodnoty hash SHA-1

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();
```

Řešení

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="ripemd160-hashing-violation"></a>Porušení hodnoty hash RIPEMD160

```csharp
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();
```

Řešení

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="tripledes-encryption-violation"></a>Narušení šifrování TripleDES

```csharp
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

Řešení

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```