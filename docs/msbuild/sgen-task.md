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
ms.openlocfilehash: a97133892926e60adc1d9f0165415868732066ca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595121"
---
# <a name="sgen-task"></a>SGen – úloha
Vytvoří sestavení serializace XML pro typy v zadaném sestavení. Tato úloha zalomí nástroj generátoru serializátoru XML (*Sgen. exe*). Další informace najdete v tématu [Nástroj generátoru serializátoru XML (Sgen. exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `SGen`.

| Parametr | Popis |
|-----------------------------| - |
| `BuildAssemblyName` | Vyžaduje se `String` parametr.<br /><br /> Sestavení pro generování kódu serializace pro. |
| `BuildAssemblyPath` | Vyžaduje se `String` parametr.<br /><br /> Cesta k sestavení, pro který má být generován kód serializace. |
| `DelaySign` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, určuje, že chcete umístit pouze veřejný klíč do sestavení. Pokud `false`, určuje, že chcete sestavení plně podepsané.<br /><br /> Tento parametr nemá žádný vliv, pokud se nepoužívá buď s parametrem `KeyFile` nebo `KeyContainer`. |
| `KeyContainer` | Volitelný parametr `String`.<br /><br /> Určuje kontejner obsahující pár klíčů. Tím se sestavení podepíše vložením veřejného klíče do manifestu sestavení. Úloha pak podepíše konečné sestavení pomocí privátního klíče. |
| `KeyFile` | Volitelný parametr `String`.<br /><br /> Určuje dvojici klíčů nebo veřejný klíč, který se má použít k podepsání sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. |
| `Platform` | Volitelný parametr `String`.<br /><br /> Získá nebo nastaví platformu kompilátoru, která se používá k vytvoření výstupního sestavení. Tento parametr může mít hodnotu `x86`, `x64`nebo `anycpu`. Výchozí hodnota je `anycpu`. |
| `References` | Volitelný parametr `String[]`.<br /><br /> Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML. |
| `SdkToolsPath` | Volitelný parametr `String`.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je *Resgen. exe*. |
| `SerializationAssembly` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje generované sestavení serializace. |
| `SerializationAssemblyName` | Volitelný parametr `String`.<br /><br /> Určuje název vygenerovaného sestavení serializace. |
| `ShouldGenerateSerializer` | Vyžaduje se `Boolean` parametr.<br /><br /> Pokud `true`, úloha SGen by měla generovat sestavení serializace. |
| `Timeout` | Volitelný parametr `Int32`.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je ukončen spustitelný soubor úlohy. Výchozí hodnota je `Int.MaxValue`, což značí, že není k dispozici žádný časový interval. |
| `ToolPath` | Volitelný parametr `String`.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (*Sgen. exe*). Pokud tento parametr není zadán, úloha použije cestu instalace sady SDK odpovídající verzi rozhraní .NET Framework, která je spuštěna [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Types` | Volitelný parametr `String[]`.<br /><br /> Získá nebo nastaví seznam konkrétních typů, pro které se má generovat Serializační kód. SGen vygeneruje kód serializace pouze pro tyto typy. |
| `UseProxyTypes` | Vyžaduje se `Boolean` parametr.<br /><br /> Pokud `true`, úloha SGen generuje kód serializace pouze pro typ proxy webové služby XML. |

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
