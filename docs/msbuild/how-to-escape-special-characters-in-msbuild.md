---
title: 'Postup: Escape Speciální znaky v MSBuild | Dokumenty společnosti Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633873"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Postup: Escape speciální znaky v MSBuild

Některé znaky mají zvláštní význam v souborech projektu MSBuild. Příklady znaků zahrnují středníky`;`( ) a`*`hvězdičky ( ). Úplný seznam těchto speciálních znaků naleznete v tématu [MSBuild speciální znaky](../msbuild/msbuild-special-characters.md).

Chcete-li použít tyto speciální znaky jako literály v souboru projektu, musí být určeny pomocí syntaxe `%<xx>`, kde `<xx>` představuje šestnáctkovou hodnotu znaku ASCII.

## <a name="msbuild-special-characters"></a>MSBuild speciální znaky

Jeden příklad, kde se používají `Include` speciální znaky, je v atributu seznamů položek. Například následující seznam položek deklaruje dvě položky: *MyFile.cs* a *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Pokud chcete deklarovat položku, která obsahuje středník `%<xx>` v názvu, musíte použít syntaxi k úniku středníku a zabránit MSBuild deklarování dvou samostatných položek. Například následující položka unikne středník a deklaruje jednu položku s názvem `MyFile.cs;MyClass.cs`.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Můžete také použít [vlastnost funkce](../msbuild/property-functions.md) escape řetězce. Například je to ekvivalentní výše uvedenému příkladu.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Použití speciálního znaku MSBuild jako literálu

Použijte zápis `%<xx>` místo speciálního znaku, `<xx>` kde představuje šestnáctkovou hodnotu znaku ASCII. Chcete-li například použít hvězdičku (`*`) jako literálový znak, použijte hodnotu `%2A`.

## <a name="see-also"></a>Viz také
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Items](../msbuild/msbuild-items.md)
