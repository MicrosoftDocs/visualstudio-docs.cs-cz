---
title: CA5351 nepoužívá poškozené kryptografické algoritmy | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ad4698fe469176ae8ed590c44b4efbb4ccf39de2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545051"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nepoužívejte poškozené kryptografické algoritmy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Kategorie|Microsoft. kryptografie|
|Narušující změna|Bez přerušení|

> [!NOTE]
> Toto upozornění se naposledy aktualizovalo od listopadu 2015.

## <a name="cause"></a>Příčina
 Funkce hash, jako jsou <xref:System.Security.Cryptography.MD5> a algoritmy šifrování, jako jsou <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.RC2> můžou vystavit významné riziko a můžou vést k expozici citlivých informací prostřednictvím technik triviálních útoků, jako jsou útoky hrubou silou a kolize hodnot hash.

 Níže uvedený seznam kryptografických algoritmů podléhá známým kryptografickým útokům. Kryptografický algoritmus hash <xref:System.Security.Cryptography.MD5> podléhá útokům kolizí hash.  V závislosti na využití může kolizí hash vést k zosobnění, manipulaci nebo jiným druhům útoků na systémy, které spoléhají na jedinečný kryptografický výstup funkce hash. Šifrovací algoritmy <xref:System.Security.Cryptography.DES> a <xref:System.Security.Cryptography.RC2> jsou předmětem kryptografických útoků, které mohou vést k neúmyslnému zveřejnění šifrovaných dat.

## <a name="rule-description"></a>Popis pravidla
 Nefunkční kryptografické algoritmy nejsou považovány za zabezpečené a jejich použití by se mělo nedoporučuje. Algoritmus hash MD5 je náchylný ke známým útokům na kolizi, i když se konkrétní chyba zabezpečení liší v závislosti na kontextu použití.  K zajištění integrity dat (např. signatura souboru nebo digitální certifikát) jsou obzvláště ohroženy algoritmy hash.  V tomto kontextu by útočníci mohli vygenerovat dvě samostatná data, což by mohlo nahradit neškodná data, a to beze změny hodnoty hash nebo zrušení platnosti přidruženého digitálního podpisu.

 Pro šifrovací algoritmy:

- <xref:System.Security.Cryptography.DES>šifrování obsahuje malou velikost klíče, což může být hrubě vynuceně za méně než jeden den.

- <xref:System.Security.Cryptography.RC2>šifrování je náchylné k útokům související s klíčem, kde útočník nalezne matematické vztahy mezi všemi hodnotami klíče.

  Toto pravidlo se aktivuje, když nalezne některou z výše uvedených kryptografických funkcí ve zdrojovém kódu a vyvolá uživateli upozornění.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Používejte kryptograficky silnější možnosti:

- V případě MD5 použijte hodnoty hash v rodině [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) (např., <xref:System.Security.Cryptography.SHA512> <xref:System.Security.Cryptography.SHA384> <xref:System.Security.Cryptography.SHA256> ).

- V případě DES a RC2 použijte <xref:System.Security.Cryptography.Aes> šifrování.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla, pokud není zkontrolováno kryptografickým odborníkem.

## <a name="pseudo-code-example"></a>Příklad kódu pseudo-code
 Následující ukázka pseudo kódu znázorňuje vzor zjištěný tímto pravidlem a možné alternativy.

### <a name="md5-hashing-violation"></a>Narušení hash MD5

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>Řešení

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>RC2 narušení šifrování RC2

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

```

### <a name="solution"></a>Řešení

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```

### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Narušení šifrování

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

```

### <a name="solution"></a>Řešení

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```