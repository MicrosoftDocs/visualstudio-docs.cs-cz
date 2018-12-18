---
title: 'CA5351: Nepoužívejte poškozené kryptografické algoritmy'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c00d4e8ebb385b987bb49a44af8b241883a566b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550970"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nepoužívejte poškozené kryptografické algoritmy

|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Kategorie|Microsoft.Cryptography|
|Narušující změna|Pevné|

> [!NOTE]
> Toto upozornění byl naposledy aktualizován. listopadu 2015.

## <a name="cause"></a>příčina

Funkce, jako hashování <xref:System.Security.Cryptography.MD5> a šifrovacích algoritmů, jako <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.RC2> můžete zveřejnit významné riziko a může vést k úniku citlivých informací pomocí technik triviální útoků, jako jsou například útoky hrubou silou a kolize hodnot hash.

Níže uvedeného seznamu kryptografických algoritmů, které se vztahují známé kryptografického útoku. Kryptografická hodnota hash algoritmu <xref:System.Security.Cryptography.MD5> terčem útoků kolize hodnot hash.  V závislosti na využití může vést ke kolizi hash k zosobnění, manipulaci nebo jiné typy útoků na systémech, které závisí na jedinečných kryptografických výstup hashovací funkce. Algoritmy šifrování <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.RC2> jsou v souladu s kryptografického útoku, které může vést k neúmyslnému zveřejnění šifrovaná data.

## <a name="rule-description"></a>Popis pravidla

Kryptografické algoritmy nejsou považované za bezpečné a jejich použití se nedoporučuje. Algoritmus hash MD5 je náchylný k kolizí známé útoky, když se liší v závislosti na kontextu použití konkrétní ohrožení zabezpečení.  Algoritmy hash používá k zajištění integrity dat (například podpis souboru nebo digitální certifikát) jsou snadno napadnutelný.  V tomto kontextu může útočník generovat dva samostatné druhy dat, tak, aby neškodné data se můžou nahradit se zlými úmysly daty a bez změna hodnoty hash nebo zrušení platnosti přidružený digitální podpis.

Pro šifrovací algoritmy:

- <xref:System.Security.Cryptography.DES> šifrování obsahuje malá velikost klíče, které by mohly být útokem hrubou silou za kratší dobu než den.

- <xref:System.Security.Cryptography.RC2> šifrování je náchylný k útok související s klíčem, pokud útočník zjistí matematické vztahy mezi všechny klíčové hodnoty.

Toto pravidlo aktivuje, když najde některý z výše uvedených kryptografické funkce ve zdrojovém kódu a vyvolá upozornění pro uživatele.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Použijte kryptograficky silnější možnosti:

- MD5, použijte hodnoty hash v [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) řady (například <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

- DES a RC2 <xref:System.Security.Cryptography.Aes> šifrování.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění tohoto pravidla, pokud je byly zkontrolovány podle kryptografického odborníka.

## <a name="pseudo-code-examples"></a>Příklady pseudo kódu

Následující ukázky pseudo kódu znázorňují vzor, zjistí toto pravidlo a je to možné alternativy.

### <a name="md5-hashing-violation"></a>MD5 Použití algoritmu hash porušení

```csharp
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();
```

Řešení:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="rc2-encryption-violation"></a>RC2 Porušení šifrování

```csharp
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();
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

### <a name="des-encryption-violation"></a>Šifrování DES porušení

```csharp
using System.Security.Cryptography;
...
DES encAlg = DES.Create();
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