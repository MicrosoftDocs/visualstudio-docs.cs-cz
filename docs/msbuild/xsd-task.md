---
title: XSD – úloha | Microsoft Docs
description: Přečtěte si, jak MSBuild používá úlohu XSD k zabalení nástroje definice schématu XML xsd.exe, který generuje soubory schématu nebo třídy ze zdroje.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7227fff5dd4c58e1bce81ef8cad5c32f854abf55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960322"
---
# <a name="xsd-task"></a>XSD – úloha

Zabalí Nástroj definice schématu XML (*xsd.exe*), který generuje soubory schématu nebo třídy ze zdroje.

> [!NOTE]
> Od sady Visual Studio 2017 je podpora projektů C++ pro *xsd.exe* zastaralá. Rozhraní API **Microsoft. VisualC. CppCodeProvider** můžete dál používat ručním přidáním *CppCodeProvider.dll* do globální mezipaměti sestavení (GAC).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy **XSD** .

- **AdditionalOptions**

     Volitelný **řetězcový** parametr.

     Seznam možností, jak je uvedeno na příkazovém řádku. Například/ \<option1>  / \<option2>  / \<option#> . Pomocí tohoto parametru můžete zadat možnosti, které nejsou reprezentované žádným jiným parametrem úlohy **XSD** .

- **GenerateFromSchema**

  Volitelný **řetězcový** parametr.

  Určuje typy, které jsou generovány ze zadaného schématu.

  Zadejte jednu z následujících hodnot, z nichž každá odpovídá možnosti XSD.

  - **třídy**  -  **/Classes**

  - **datová sada**  -  **/DataSet**

- **Jazyk**

     Volitelný **řetězcový** parametr.

     Určuje programovací jazyk, který má být použit pro vygenerovaný kód.

     Vyberte z **cs** (C#, což je výchozí), **VB** (Visual Basic) nebo **js** (JScript). Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Obor názvů**

     Volitelný **řetězcový** parametr.

     Určuje runtime obor názvů pro generovaný typy.

- **zdroje**

     Požadovaný parametr `ITaskItem[]`.

     Definuje pole položek zdrojového souboru MSBuild, které mohou být spotřebovány a generovány úlohami.

- **SuppressStartupBanner**

     Volitelný **logický** parametr.

     Pokud `true` aplikace zabrání zobrazení zprávy o autorských právech a číslech verze při spuštění úlohy.

- **TrackerLogDirectory**

     Volitelný **řetězcový** parametr.

     Určuje adresář pro protokol sledování.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
