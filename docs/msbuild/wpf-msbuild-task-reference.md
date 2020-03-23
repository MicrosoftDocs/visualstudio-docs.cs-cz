---
title: WPF MSBuild odkaz na úkol | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70d994e32b717ff566a2e38acee732c7525d1bb0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630844"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild odkaz na úkol

Proces sestavení Nadace Windows Presentation Foundation (WPF) rozšiřuje modul sestavení společnosti Microsoft (MSBuild) o další sadu úloh sestavení, včetně úkolů pro kompilaci značek a prostředků procesu.

## <a name="in-this-section"></a>V tomto oddílu

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Klasifikuje sadu zdrojových prostředků jako ty, které budou vloženy do sestavení. Pokud prostředek není lokalizovatelný, je vložen do sestavení hlavní aplikace; v opačném případě je vložen do satelitního sestavení.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Generuje sestavení, pokud alespoň jedna stránka XAML v projektu odkazuje na typ, který je deklarován místně v tomto projektu. Generované sestavení je odebráno po dokončení procesu sestavení nebo pokud se proces sestavení nezdaří.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Vrátí adresář aktuálního runtime rozhraní .NET Framework.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Převede nelokalizovatelné soubory projektu XAML na zkompilovaný binární formát.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Provádí kompilaci značek druhého průchodu u souborů XAML, které odkazují na typy ve stejném projektu.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Sloučí atributy lokalizace a komentáře jednoho nebo více souborů binárního formátu XAML do jednoho souboru pro celé sestavení.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Vloží jeden nebo více prostředků (*.jpg*, *.ico*, *.bmp*, XAML v binárním formátu a další typy rozšíření) do souboru *.resources.*

- [UidManager](../msbuild/uidmanager-task.md)

 Zkontroluje, aktualizuje nebo odebere jedinečné identifikátory (UID), aby lokalizoval všechny prvky XAML, které jsou zahrnuty ve zdrojových souborech XAML.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Přidá prvek ** \<hostInBrowser />** do manifestu aplikace*\<(název projektu>.exe.manifest)* při sestavení projektu aplikace prohlížeče XAML (XBAP).

## <a name="see-also"></a>Viz také

- [Msbuild](../msbuild/msbuild.md)