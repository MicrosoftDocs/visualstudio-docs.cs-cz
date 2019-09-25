---
title: 'CA2310: Nepoužívat nezabezpečený deserializátor NetDataContractSerializer'
ms.date: 05/01/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: 5335e72307ea201ad77d6e59b267572d4d9aae56
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237709"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Nepoužívat nezabezpečený deserializátor NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

<xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> Byla volána nebo odkazována metoda deserializace.

## <a name="rule-description"></a>Popis pravidla

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Toto pravidlo vyhledá <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> volání nebo odkazy metody deserializace. Pokud chcete provést deserializaci pouze v případě <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> , že je vlastnost nastavena na hodnotu omezit typy, zakažte toto pravidlo a místo toho povolte pravidla [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) a [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) .

## <a name="how-to-fix-violations"></a>Jak opravit porušení

- Pokud je to možné, použijte místo toho zabezpečený serializátor a **nepovolujte útočníkovi zadání libovolného typu k deserializaci**. Mezi bezpečnější serializátory patří:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>– Nikdy nepoužívejte <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Pokud je nutné použít překladač typů, omezte deserializovatelné typy na očekávaný seznam.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET – použijte TypeNameHandling. None. Pokud je nutné použít jinou hodnotu pro TypeNameHandling, omezte deserializovatelné typy na očekávaný seznam pomocí vlastního ISerializationBinder.
  - Vyrovnávací paměti protokolů
- Proveďte serializovanou manipulaci s daty. Po serializaci kryptograficky podepisují Serializovaná data. Před deserializací ověřte kryptografický podpis. Chránit kryptografický klíč před zveřejněním a návrhem pro střídání klíčů.
- Omezí deserializovatelné typy. Implementujte vlastní <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Před deserializací pomocí <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> nastavte vlastnost na instanci vašeho vlastního <xref:System.Runtime.Serialization.SerializationBinder>. Pokud je typ <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> v přepsané metodě neočekávaný, vyvolejte výjimku pro zastavení deserializace.
  - Pokud omezíte deserializovatelné typy, možná budete chtít zakázat toto pravidlo a povolit pravidla [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) a [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Rules [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) a [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) Help <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> zajistí, že vlastnost je vždy nastavena před deserializací.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Související pravidla

[CA2311: Nepovedlo se deserializovat bez předchozího nastavení NetDataContractSerializer. Binder.](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Ujistěte se, že je NetDataContractSerializer. Binder nastavený před deserializací.](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
