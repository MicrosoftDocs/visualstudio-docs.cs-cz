---
title: Úkol XSD | Dokumenty společnosti Microsoft
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 217e045a731efa1fe3ba1dda63e89eca685d4b75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630779"
---
# <a name="xsd-task"></a>XSD – úloha

Zalomí nástroj definice schématu XML (*xsd.exe*), který generuje soubory schématu nebo třídy ze zdroje.

> [!NOTE]
> Počínaje Visual Studio 2017, C++ podpora projektu pro *xsd.exe* je zastaralé. Rozhraní **API Microsoft.VisualC.CppCodeProvider** můžete stále používat ručním přidáním souboru *CppCodeProvider.dll* do souboru GAC.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **XSD.**

- **Další možnosti**

     Volitelný **parametr String.**

     Seznam možností určených na příkazovém řádku. Například /\<option1\<> /\<option2> / option#>. Tento parametr slouží k určení možností, které nejsou reprezentovány žádným jiným parametrem úlohy **XSD.**

- **GenerateFromSchema**

  Volitelný **parametr String.**

  Určuje typy, které jsou generovány ze zadaného schématu.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti XSD.

  - **třídy** - **/třídy**

  - **datová sada** - **/datová sada**

- **Jazyk**

     Volitelný **parametr String.**

     Určuje programovací jazyk, který se má použít pro generovaný kód.

     Vyberte si z **CS** (C#, což je výchozí), **VB** (Visual Basic) nebo **JS** (JScript). Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Namespace**

     Volitelný **parametr String.**

     Určuje runtime obor názvů pro generovaný typy.

- **Zdrojů**

     Požadovaný parametr `ITaskItem[]`.

     Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a vydávány úkoly.

- **PotlačitStartupBanner**

     Volitelný **logický** parametr.

     Pokud `true`aplikace zabraňuje zobrazení zprávy o autorských právech a čísle verze při spuštění úlohy.

- **TrackerLogDirectory**

     Volitelný **parametr String.**

     Určuje adresář protokolu sledování.

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
