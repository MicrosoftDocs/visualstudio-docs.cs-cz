---
title: WPF MSBuild – referenční informace k úloze | Microsoft Docs
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
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb21495954801d55c1db0bb9156a813ab73db683
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687110"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild – referenční dokumentace úlohy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces sestavení Windows Presentation Foundation (WPF) rozšiřuje nástroj Microsoft Build Engine (MSBuild) o další sadu úloh sestavení, včetně úloh pro zkompilování značek a zpracování prostředků.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Klasifikuje sadu zdrojových prostředků jako ty, které budou vloženy do sestavení. Pokud prostředek nelze lokalizovat, je vložen do hlavního sestavení aplikace; v opačném případě je vložen do satelitního sestavení.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Vygeneruje sestavení, pokud alespoň jedna [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] Stránka v projektu odkazuje na typ, který je deklarován místně v daném projektu. Vygenerované sestavení je odebráno po dokončení procesu sestavení, nebo pokud proces sestavení není úspěšný.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Vrátí adresář aktuálního [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] modulu runtime.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Převede soubory projektu, které nejsou lokalizovatelné [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] na kompilovaný binární formát.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Provádí kompilaci kódu s druhými průchody na [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] souborech, které odkazují na typy ve stejném projektu.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Sloučí atributy lokalizace a komentáře jednoho nebo více [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů binárního formátu do jediného souboru pro celé sestavení.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Vloží jeden nebo více prostředků (. jpg,. ico,. bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] v binárním formátu a dalších typech rozšíření) do souboru. Resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Kontroluje, aktualizuje nebo odebírá jedinečné identifikátory (UID), aby bylo možné lokalizovat všechny [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] prvky, které jsou součástí zdrojových [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] souborů.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Přidá **\<hostInBrowser />** prvek do manifestu aplikace (*ProjectName*. exe. manifest) při [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] sestavení projektu.  
  
## <a name="see-also"></a>Viz také  
 [Nástroji](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)
