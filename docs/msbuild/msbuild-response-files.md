---
title: Soubory odpovědí MSBuild | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302894"
---
# <a name="msbuild-response-files"></a>Soubory odpovědí MSBuild

Soubory odpovědi *(RSP*) jsou textové soubory, které obsahují přepínače příkazového řádku *MSBuild.exe.* Každý přepínač může být na samostatné lince nebo všechny přepínače mohou být na jedné lince. Řádky poznámek jsou **#** přednimi se symbolem. Přepínač **@** slouží k předání jiného souboru odpovědi do souboru *MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp

Soubor automatické odpovědi je speciální *soubor RSP,* který *msbuild.exe* automaticky používá při vytváření projektu. Tento soubor *MSBuild.rsp*musí být ve stejném adresáři jako *MSBuild.exe*, jinak nebude nalezen. Tento soubor můžete upravit a určit tak výchozí přepínače příkazového řádku na *msbuild.exe*. Například pokud použijete stejný protokolovací nástroj pokaždé, když vytvoříte projekt, můžete přidat **-logger** přepínač *MSBuild.rsp*a *MSBuild.exe* bude používat protokolovací nástroj pokaždé, když je vytvořen projekt.

## <a name="directorybuildrsp"></a>Directory.Build.rsp

Ve verzi 15.6 a vyšší bude služba MSBuild vyhledávat nadřazené adresáře projektu pro soubor s názvem *Directory.Build.rsp*.  To může být užitečné v úložišti zdrojového kódu poskytnout výchozí argumenty během sestavení příkazového řádku.  Lze také určit argumenty příkazového řádku hostovaných sestavení.

## <a name="see-also"></a>Viz také

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md)
