---
title: 'Postupy: sekvence speciálních znaků v nástroji MSBuild | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94fc8d858e2db9bd1e00bb8770cf52672a900ab0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178344"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Postupy: Zápis speciálních znaků pomocí escape sekvence v nástroji MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Některé znaky mají v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] souborech projektu zvláštní význam. Mezi příklady znaků patří středník (;) a hvězdičky (*). Úplný seznam těchto speciálních znaků naleznete v tématu [speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Aby bylo možné použít tyto speciální znaky jako literály v souboru projektu, musí být zadány pomocí syntaxe%*XX*, kde *XX* představuje šestnáctkovou hodnotu ASCII znaku.  
  
## <a name="msbuild-special-characters"></a>Speciální znaky nástroje MSBuild  
 Jeden z příkladů, kde se používají speciální znaky, jsou v `Include` atributu seznamů položek. Například následující seznam položek deklaruje dvě položky: `MyFile.cs` a `MyClass.cs` .  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Chcete-li deklarovat položku, která obsahuje středník v názvu, je nutné použít syntaxi%*XX* a zabránit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] v deklarování dvou samostatných položek. Například následující položka řídí středník a deklaruje jednu položku s názvem `MyFile.cs;MyClass.cs` .  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Použití speciálního znaku MSBuild jako literálního znaku  
  
- Použijte notaci%*XX* místo speciálního znaku, kde *XX* představuje hexadecimální hodnotu znaku ASCII. Chcete-li například použít hvězdičku (*) jako literální znak, použijte hodnotu `%2A` .  
  
## <a name="see-also"></a>Viz také  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md) [Položky](../msbuild/msbuild-items.md) nástroje MSBuild
