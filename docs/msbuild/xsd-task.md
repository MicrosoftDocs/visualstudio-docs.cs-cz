---
title: XSD – úloha | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630779"
---
# <a name="xsd-task"></a>XSD – úloha

Zabalí Nástroj definice schématu XML (*XSD. exe*), který generuje soubory schématu nebo třídy ze zdroje.

> [!NOTE]
> Od sady Visual Studio 2017 je C++ podpora projektů pro soubor *XSD. exe* zastaralá. Rozhraní API **Microsoft. VisualC. CppCodeProvider** můžete dál používat tak, že ručně přidáte *CppCodeProvider. dll* do globální mezipaměti sestavení (GAC).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **XSD** .

- **AdditionalOptions**

     Volitelný **řetězcový** parametr.

     Seznam možností, jak je uvedeno na příkazovém řádku. Například/\<možnost1 >/\<možnost2 >/\<možnost # >. Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **XSD** .

- **GenerateFromSchema**

  Volitelný **řetězcový** parametr.

  Určuje typy, které jsou generovány ze zadaného schématu.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti XSD.

  - **třídy** -  **/Classes**

  - **datová sada** -  **/DataSet**

- **Jazyk**

     Volitelný **řetězcový** parametr.

     Určuje programovací jazyk, který má být použit pro vygenerovaný kód.

     Vyberte z **cs** (C#, což je výchozí nastavení), **VB** (Visual Basic) nebo **js** (JScript). Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Hosting**

     Volitelný **řetězcový** parametr.

     Určuje runtime obor názvů pro generovaný typy.

- **Prostředky**

     Vyžaduje se `ITaskItem[]` parametr.

     Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.

- **SuppressStartupBanner**

     Volitelný **logický** parametr.

     Pokud `true`, zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.

- **TrackerLogDirectory**

     Volitelný **řetězcový** parametr.

     Určuje adresář pro protokol sledování.

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
