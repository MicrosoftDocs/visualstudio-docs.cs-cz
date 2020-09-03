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
ms.openlocfilehash: f9958ae93e2605ad3c89decb4ac9fabc18102148
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633873"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Postupy: sekvence speciálních znaků v nástroji MSBuild

Některé znaky mají v souborech projektu MSBuild zvláštní význam. Příklady znaků zahrnují středníky ( `;` ) a hvězdičky ( `*` ). Úplný seznam těchto speciálních znaků naleznete v tématu [speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md).

Aby bylo možné použít tyto speciální znaky jako literály v souboru projektu, musí být zadány pomocí syntaxe `%<xx>` , kde `<xx>` představuje šestnáctkovou hodnotu ASCII znaku.

## <a name="msbuild-special-characters"></a>Speciální znaky nástroje MSBuild

Jeden z příkladů, kde se používají speciální znaky, jsou v `Include` atributu seznamů položek. Například následující seznam položek deklaruje dvě položky: *MyFile.cs* a *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Chcete-li deklarovat položku, která obsahuje středník v názvu, je nutné použít `%<xx>` syntaxi pro řídicí středník a zabránit nástroji MSBuild v deklaraci dvou samostatných položek. Například následující položka řídí středník a deklaruje jednu položku s názvem `MyFile.cs;MyClass.cs` .

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Můžete také použít [funkci vlastnosti](../msbuild/property-functions.md) pro řídicí řetězce. Jedná se například o ekvivalent výše uvedeného příkladu.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Použití speciálního znaku MSBuild jako literálního znaku

Použijte notaci `%<xx>` místo speciálního znaku, kde `<xx>` představuje hexadecimální hodnotu znaku ASCII. Chcete-li například použít hvězdičku ( `*` ) jako literální znak, použijte hodnotu `%2A` .

## <a name="see-also"></a>Viz také
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Nástroji](../msbuild/msbuild.md)
- [Položky](../msbuild/msbuild-items.md)
