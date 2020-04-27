---
title: Úloha SGen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbf18c4477a164ec2e25a5ed4b2105f6fdad9130
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167433"
---
# <a name="sgen-task"></a>SGen – úloha

Vytvoří sestavení serializace XML pro typy v zadaném sestavení. Tato úloha zalomí nástroj generátoru serializátoru XML (*Sgen. exe*). Další informace najdete v tématu [Nástroj generátoru serializátoru XML (Sgen. exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `SGen` úkolu.

| Parametr | Popis |
|-----------------------------| - |
| `BuildAssemblyName` | Požadovaný parametr `String`.<br /><br /> Sestavení pro generování kódu serializace pro. |
| `BuildAssemblyPath` | Požadovaný parametr `String`.<br /><br /> Cesta k sestavení, pro který má být generován kód serializace. |
| `DelaySign` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, určuje, že chcete umístit pouze veřejný klíč do sestavení. Pokud `false`, určuje, že chcete sestavení plně podepsané.<br /><br /> Tento parametr nemá žádný vliv, pokud se nepoužívá `KeyFile` buď `KeyContainer` s parametrem nebo. |
| `KeyContainer` | Volitelný `String` parametr.<br /><br /> Určuje kontejner obsahující pár klíčů. Tím se sestavení podepíše vložením veřejného klíče do manifestu sestavení. Úloha pak podepíše konečné sestavení pomocí privátního klíče. |
| `KeyFile` | Volitelný `String` parametr.<br /><br /> Určuje dvojici klíčů nebo veřejný klíč, který se má použít k podepsání sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. |
| `Platform` | Volitelný `String` parametr.<br /><br /> Získá nebo nastaví platformu kompilátoru, která se používá k vytvoření výstupního sestavení. Tento parametr může mít hodnotu `x86`, `x64`nebo. `anycpu` Výchozí je `anycpu`. |
| `References` | Volitelný `String[]` parametr.<br /><br /> Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML. |
| `SdkToolsPath` | Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je *Resgen. exe*. |
| `SerializationAssembly` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje generované sestavení serializace. |
| `SerializationAssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje název vygenerovaného sestavení serializace. |
| `ShouldGenerateSerializer` | Požadovaný parametr `Boolean`.<br /><br /> Pokud `true`by úloha Sgen měla generovat sestavení serializace. |
| `Timeout` | Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue`, což značí, že není k dispozici žádný časový interval. |
| `ToolPath` | Volitelný `String` parametr.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (*Sgen. exe*). Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK odpovídající verzi rozhraní .NET Framework, která spouští nástroj MSBuild. |
| `Types` | Volitelný `String[]` parametr.<br /><br /> Získá nebo nastaví seznam konkrétních typů, pro které se má generovat Serializační kód. SGen vygeneruje kód serializace pouze pro tyto typy. |
| `UseProxyTypes` | Požadovaný parametr `Boolean`.<br /><br /> Pokud `true`, úloha Sgen generuje kód serializace pouze pro typ proxy webové služby XML. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
