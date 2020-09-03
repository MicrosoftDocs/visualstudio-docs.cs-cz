---
title: Soubory odpovědí nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189375"
---
# <a name="msbuild-response-files"></a>Soubory odezvy nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soubory odpovědí (. rsp) jsou textové soubory, které obsahují MSBuild.exe přepínačů příkazového řádku. Každý přepínač může být na samostatném řádku nebo všechny přepínače mohou být na jednom řádku. Řádky komentáře jsou uvozeny **#** symbolem. **@** Přepínač slouží k předání dalšího souboru odpovědi do MSBuild.exe.  
  
 Soubor automatické odpovědi je speciální soubor. rsp, který MSBuild.exe automaticky používat při sestavování projektu. Tento soubor, MSBuild. rsp, musí být ve stejném adresáři jako MSBuild.exe, jinak nebude nalezen. Úpravou tohoto souboru můžete zadat výchozí přepínače příkazového řádku pro MSBuild.exe. Například pokud použijete stejný protokolovací nástroj při každém sestavení projektu, můžete přidat přepínač **/Logger** do MSBuild. rsp a MSBuild.exe bude používat protokolovací nástroj vždy, když je projekt sestaven.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md)
