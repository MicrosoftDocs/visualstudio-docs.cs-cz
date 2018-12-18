---
title: Referenční dokumentace WPF MSBuild – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 5266b5b6274eb9a39f6603598b90cd551f25caef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49185468"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild – referenční dokumentace úlohy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Proces sestavení Windows Presentation Foundation (WPF) rozšiřuje další sadu úloh sestavení, včetně úloh ke kompilaci kódu a zdroje procesu Microsoft build engine (MSBuild).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Klasifikuje sadu prostředků zdroje jako ty, které budou vloženy do sestavení. Pokud prostředek není lokalizovatelné, je vložen do sestavení hlavní aplikace; v opačném případě se vloží do satelitního sestavení.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Generuje sestavení, pokud se alespoň jeden [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] stránky v projektu odkazuje na typ, který je deklarován místně v daném projektu. Generované sestavení se odebere po dokončení procesu sestavení, nebo pokud proces sestavení se nezdaří.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Vrátí adresáře aktuálního [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] modulu runtime.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Převede bez možnosti lokalizace [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] soubory do kompilovaného binárního formátu projektu.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Provede kompilaci značek druhého průchodu na [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] soubory, které odkazují na typy ve stejném projektu.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Sloučí atributy a komentáře lokalizace jednoho nebo víc [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] binárních souborů do jediného souboru pro celé sestavení.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Vloží jednu nebo více prostředků (JPG, ICO, BMP, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] v binárním formátu a ostatními typy rozšíření) do souboru .resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Kontroluje, aktualizuje nebo odebere jedinečné identifikátory (UID), aby bylo možné lokalizovat všechny [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] prvky, které jsou zahrnuté ve zdroji [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] soubory.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Přidá  **\<hostInBrowser / >** element do manifestu aplikace (*projectname*. exe.manifest) při [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] sestavení projektu.  
  
## <a name="see-also"></a>Viz také  
 [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)



