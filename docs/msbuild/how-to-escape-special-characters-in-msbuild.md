---
title: 'Postupy: sekvence speciálních znaků v nástroji MSBuild | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 955739372605b9e4f9fe58f73669322e2724de31
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595004"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Postupy: sekvence speciálních znaků v nástroji MSBuild

Některé znaky mají zvláštní význam v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] soubory projektu. Mezi příklady znaků patří středník (`;`) a hvězdičky (`*`). Úplný seznam těchto speciálních znaků naleznete v tématu [speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md).

Aby bylo možné použít tyto speciální znaky jako literály v souboru projektu, musí být určeny pomocí syntaxe `%<xx>`, kde `<xx>` představuje šestnáctkovou hodnotu ASCII znaku.

## <a name="msbuild-special-characters"></a>Speciální znaky nástroje MSBuild

Jeden z příkladů, kde se používají speciální znaky, jsou v atributu `Include` seznamů položek. Například následující seznam položek deklaruje dvě položky: *MyFile.cs* a *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Chcete-li deklarovat položku, která obsahuje středník v názvu, je nutné použít syntaxi `%<xx>` pro odřídící středník a zabránit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] v deklaraci dvou samostatných položek. Například následující položka řídí středník a deklaruje jednu položku s názvem `MyFile.cs;MyClass.cs`.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Můžete také použít [funkci vlastnosti](../msbuild/property-functions.md) pro řídicí řetězce. Jedná se například o ekvivalent výše uvedeného příkladu.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Použití speciálního znaku MSBuild jako literálního znaku

Místo speciálního znaku použijte `%<xx>` Notation, kde `<xx>` představuje hexadecimální hodnotu znaku ASCII. Chcete-li například použít hvězdičku (`*`) jako literální znak, použijte hodnotu `%2A`.

## <a name="see-also"></a>Viz také:
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Položky](../msbuild/msbuild-items.md)
