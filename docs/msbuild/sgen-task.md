---
title: Úkol SGen | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 4305f27435d97c346ce623a21b37f011fd8da0cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632300"
---
# <a name="sgen-task"></a>SGen – úloha

Vytvoří sestavení serializace XML pro typy v zadaném sestavení. Tato úloha zalomí nástroj generátor serializátorů XML (*Sgen.exe).* Další informace naleznete v tématu [XML Serializer Generator tool (Sgen.exe).](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe)

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `SGen` úkolu.

| Parametr | Popis |
|-----------------------------| - |
| `BuildAssemblyName` | Požadovaný parametr `String`.<br /><br /> Sestavení generovat serializační kód pro. |
| `BuildAssemblyPath` | Požadovaný parametr `String`.<br /><br /> Cesta k sestavení generovat serializační kód pro. |
| `DelaySign` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, určuje, že chcete umístit pouze veřejný klíč do sestavení. Pokud `false`, určuje, že chcete plně podepsané sestavení.<br /><br /> Tento parametr nemá žádný vliv, `KeyFile` `KeyContainer` pokud není použit s parametrem nebo. |
| `KeyContainer` | Volitelný `String` parametr.<br /><br /> Určuje kontejner obsahující pár klíčů. To podepíše sestavení vložením veřejného klíče do manifestu sestavení. Úkol pak podepíše konečné sestavení pomocí soukromého klíče. |
| `KeyFile` | Volitelný `String` parametr.<br /><br /> Určuje dvojici klíčů nebo veřejný klíč, který se má použít k podepsání sestavení. Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem. |
| `Platform` | Volitelný `String` parametr.<br /><br /> Získá nebo nastaví platformu kompilátoru slouží ke generování výstupní sestavení. Tento parametr může mít `x86` `x64`hodnotu `anycpu`, , nebo . Výchozí je `anycpu`. |
| `References` | Volitelný `String[]` parametr.<br /><br /> Určuje sestavení, která je odkazováno dle typy vyžadujících serializace XML. |
| `SdkToolsPath` | Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, například *resgen.exe*. |
| `SerializationAssembly` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje generované sestavení serializace. |
| `SerializationAssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje název generovaného sestavení serializace. |
| `ShouldGenerateSerializer` | Požadovaný parametr `Boolean`.<br /><br /> Pokud `true`by úloha SGen měla generovat sestavení serializace. |
| `Timeout` | Volitelný `Int32` parametr.<br /><br /> Určuje dobu v milisekundách, po jejímž uplynutí je spustitelný soubor úlohy ukončen. Výchozí hodnota `Int.MaxValue`je , označující, že neexistuje žádné časové období. |
| `ToolPath` | Volitelný `String` parametr.<br /><br /> Určuje umístění, ze kterého bude úloha načítat základní spustitelný soubor (*sgen.exe*). Pokud tento parametr není zadán, úloha používá instalační cestu sady SDK odpovídající verzi rozhraní, ve které je spuštěno službu MSBuild. |
| `Types` | Volitelný `String[]` parametr.<br /><br /> Získá nebo nastaví seznam konkrétních typů pro generování serializačního kódu. SGen bude generovat serializační kód pouze pro tyto typy. |
| `UseProxyTypes` | Požadovaný parametr `Boolean`.<br /><br /> Pokud `true`úloha SGen generuje kód serializace pouze pro typy proxy webových služeb XML. |

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.ToolTaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.ToolTask> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [ToolTaskExtension base class](../msbuild/tooltaskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
