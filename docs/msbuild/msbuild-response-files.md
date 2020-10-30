---
title: Soubory odpovědí nástroje MSBuild | Microsoft Docs
description: Seznamte se s odpověďmi nástroje MSBuild nebo soubory. rsp, textovými soubory, které obsahují MSBuild.exe přepínačů příkazového řádku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b18ad00c3be8c3684551f28bc170dbd4a8428533
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049143"
---
# <a name="msbuild-response-files"></a>Soubory odezvy nástroje MSBuild

Soubory odpovědí ( *. rsp* ) jsou textové soubory, které obsahují *MSBuild.exe* přepínačů příkazového řádku. Každý přepínač může být na samostatném řádku nebo všechny přepínače mohou být na jednom řádku. Řádky komentáře jsou uvozeny **#** symbolem. **@** Přepínač slouží k předání dalšího souboru odpovědi do *MSBuild.exe* .

## <a name="msbuildrsp"></a>MSBuild. rsp

Soubor automatické odpovědi je speciální soubor *. rsp* , který *MSBuild.exe* automaticky používat při sestavování projektu. Tento soubor, *MSBuild. rsp* , musí být ve stejném adresáři jako *MSBuild.exe* , jinak nebude nalezen. Úpravou tohoto souboru můžete zadat výchozí přepínače příkazového řádku na *MSBuild.exe* . Například pokud použijete stejný protokolovací nástroj při každém sestavení projektu, můžete přidat přepínač **-protokolovacího** nástroje do *MSBuild. rsp* a *MSBuild.exe* použije protokolovací nástroj vždy, když je projekt sestaven.

## <a name="directorybuildrsp"></a>Adresář. Build. rsp

Ve verzi 15,6 a novější nástroj MSBuild hledá nadřazené adresáře projektu pro soubor s názvem *Directory. Build. rsp* .  To může být užitečné v úložišti zdrojového kódu k poskytnutí výchozích argumentů během sestavení příkazového řádku.  Lze ji také použít k určení argumentů příkazového řádku hostovaných sestavení.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Referenční dokumentace k příkazovému řádku](../msbuild/msbuild-command-line-reference.md)
