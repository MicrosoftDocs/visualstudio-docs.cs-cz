---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87471571"
---
- Místo toho použijte zabezpečený serializátor a **nepovolujte útočníkovi zadání libovolného typu k deserializaci**. Další informace najdete v tématu [preferované alternativy](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).
- Proveďte serializovanou manipulaci s daty. Po serializaci kryptograficky podepisují Serializovaná data. Před deserializací ověřte kryptografický podpis. Chránit kryptografický klíč před zveřejněním a návrhem pro střídání klíčů.
- Tato možnost způsobí, že kód bude zranitelný vůči útokům DOS (Denial of Service) a možným útokům na vzdálené spuštění kódu v budoucnu. Další informace najdete v [příručce zabezpečení BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide). Omezí deserializovatelné typy. Implementujte vlastní <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> . Před deserializací nastavte `Binder` vlastnost na instanci vlastní <xref:System.Runtime.Serialization.SerializationBinder> ve všech cestách kódu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>Pokud je typ v přepsané metodě neočekávaný, vyvolejte výjimku pro zastavení deserializace.
