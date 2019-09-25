---
title: 'CA2311: Nedeserializovat dříve, než se nastaví NetDataContractSerializer.Binder'
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
- CA2311
- DoNotDeserializeWithoutFirstSettingNetDataContractSerializerBinder
ms.openlocfilehash: 8445c6260592bbaf109dd3786111fe64441a4da0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237689"
---
# <a name="ca2311-do-not-deserialize-without-first-setting-netdatacontractserializerbinder"></a>CA2311: Nedeserializovat dříve, než se nastaví NetDataContractSerializer.Binder

|||
|-|-|
|TypeName|DoNotDeserializeWithoutFirstSettingNetDataContractSerializerBinder|
|CheckId|CA2311|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Byla volána metoda deserializace nebo byla odkazována <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> bez sady vlastností. <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType>

## <a name="rule-description"></a>Popis pravidla

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Toto pravidlo najde <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> volání metody deserializace nebo odkazy <xref:System.Runtime.Serialization.NetDataContractSerializer> , které nemají svou <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> sadu. Pokud chcete <xref:System.Runtime.Serialization.NetDataContractSerializer> zakázat jakoukoli deserializaci bez ohledu na <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> vlastnost, zakažte toto pravidlo a [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)a povolte pravidlo [CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md).

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

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Řešení

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", nameof(typeName));
        }
    }
}

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        serializer.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", NameOf(typeName))
        End If
    End Function
End Class

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        serializer.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Související pravidla

[CA2310: Nepoužívejte nezabezpečený NetDataContractSerializer deserializace.](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md)

[CA2312: Ujistěte se, že je NetDataContractSerializer. Binder nastavený před deserializací.](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)