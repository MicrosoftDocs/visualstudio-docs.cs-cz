---
title: Soubory odpovědí nástroje MSBuild | Microsoft Docs
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
ms.openlocfilehash: 44d6e3c77fee53b15ec8d18cb74fd7355ee101a8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633236"
---
# <a name="msbuild-response-files"></a>Soubory odezvy nástroje MSBuild

Soubory odpovědí ( *. rsp*) jsou textové soubory, které obsahují přepínače příkazového řádku *MSBuild. exe* . Každý přepínač může být na samostatném řádku nebo všechny přepínače mohou být na jednom řádku. Řádky komentáře jsou uvozeny symbolem **#** . Přepínač **@** slouží k předání dalšího souboru odpovědi nástroji *MSBuild. exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp

Soubor automatické odpovědi je speciální soubor *. rsp* , který nástroj *MSBuild. exe* automaticky používá při sestavování projektu. Tento soubor, *MSBuild. rsp*, musí být ve stejném adresáři jako *MSBuild. exe*, jinak nebude nalezen. Úpravou tohoto souboru můžete zadat výchozí přepínače příkazového řádku pro *MSBuild. exe*. Například pokud použijete stejný protokolovací nástroj při každém sestavení projektu, můžete přidat přepínač **-protokolovacího** nástroje na *MSBuild. rsp*a nástroj *MSBuild. exe* použije protokolovací nástroj při každém sestavení projektu.

## <a name="directorybuildrsp"></a>Adresář. Build. rsp

Ve verzi 15,6 a novější nástroj MSBuild hledá nadřazené adresáře projektu pro soubor s názvem *Directory. Build. rsp*.  To může být užitečné v úložišti zdrojového kódu k poskytnutí výchozích argumentů během sestavení příkazového řádku.  Lze ji také použít k určení argumentů příkazového řádku hostovaných sestavení.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md)
