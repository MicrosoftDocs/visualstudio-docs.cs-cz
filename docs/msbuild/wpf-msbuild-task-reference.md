---
title: WPF MSBuild – referenční informace k úloze | Microsoft Docs
description: Podívejte se na odkaz na úlohu pro proces sestavení Windows Presentation Foundation (WPF), který rozšiřuje MSBuild o další úkoly.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94050565e6c5619781434c7a18307bfbf80b51f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933671"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild – referenční dokumentace úlohy

Proces sestavení Windows Presentation Foundation (WPF) rozšiřuje nástroj Microsoft Build Engine (MSBuild) o další sadu úloh sestavení, včetně úloh pro zkompilování značek a zpracování prostředků.

## <a name="in-this-section"></a>V této části

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Klasifikuje sadu zdrojových prostředků jako ty, které budou vloženy do sestavení. Pokud prostředek nelze lokalizovat, je vložen do hlavního sestavení aplikace; v opačném případě je vložen do satelitního sestavení.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Vygeneruje sestavení, pokud alespoň jedna stránka XAML v projektu odkazuje na typ, který je deklarován místně v daném projektu. Vygenerované sestavení je odebráno po dokončení procesu sestavení, nebo pokud proces sestavení není úspěšný.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Vrátí adresář aktuálního modulu runtime .NET Framework.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Převede soubory projektu XAML, které nejsou lokalizovatelné, do zkompilovaného binárního formátu.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Provede kompilační kompilaci kódu na souborech XAML, které odkazují na typy ve stejném projektu.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Sloučí atributy lokalizace a komentáře jednoho nebo více souborů binárního formátu XAML do jednoho souboru pro celé sestavení.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Vloží jeden nebo více prostředků (*. jpg*, *. ico*, *. bmp*, XAML v binárním formátu a jiné typy rozšíření) do souboru *. Resources* .

- [UidManager](../msbuild/uidmanager-task.md)

 Kontroluje, aktualizuje nebo odebírá jedinečné identifikátory (UID), aby bylo možné lokalizovat všechny prvky XAML, které jsou zahrnuty ve zdrojových souborech XAML.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Přidá **\<hostInBrowser />** element do manifestu aplikace (*\<projectname> . exe. manifest*) při sestavení projektu aplikace prohlížeče XAML (XBAP).

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)