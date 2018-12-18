---
title: Referenční dokumentace WPF MSBuild – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53f723644744001e39967186d0eeec74bf7d3bd7
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153797"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild – referenční dokumentace úlohy
Proces sestavení Windows Presentation Foundation (WPF) rozšiřuje další sadu úloh sestavení, včetně úloh ke kompilaci kódu a zdroje procesu Microsoft build engine (MSBuild).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Klasifikuje sadu prostředků zdroje jako ty, které budou vloženy do sestavení. Pokud prostředek není lokalizovatelné, je vložen do sestavení hlavní aplikace; v opačném případě se vloží do satelitního sestavení.  
  
 [Generatetemporarytargetassembly –](../msbuild/generatetemporarytargetassembly-task.md)  
 Generuje sestavení, pokud se alespoň jeden [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] stránky v projektu odkazuje na typ, který je deklarován místně v daném projektu. Generované sestavení se odebere po dokončení procesu sestavení, nebo pokud proces sestavení se nezdaří.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Vrátí adresáře aktuálního [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] modulu runtime.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Převede bez možnosti lokalizace [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] soubory do kompilovaného binárního formátu projektu.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Provede kompilaci značek druhého průchodu na [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] soubory, které odkazují na typy ve stejném projektu.  
  
 [Mergelocalizationdirectives –](../msbuild/mergelocalizationdirectives-task.md)  
 Sloučí atributy a komentáře lokalizace jednoho nebo víc [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] binárních souborů do jediného souboru pro celé sestavení.  
  
 [Resourcesgenerator –](../msbuild/resourcesgenerator-task.md)  
 Vloží jednu nebo více prostředků (*.jpg*, *.ico*, *.bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] v binárním formátu a ostatními typy rozšíření) do *.resources*souboru.  
  
 [Uidmanager –](../msbuild/uidmanager-task.md)  
 Kontroluje, aktualizuje nebo odebere jedinečné identifikátory (UID), aby bylo možné lokalizovat všechny [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] prvky, které jsou zahrnuté ve zdroji [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] soubory.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Přidá  **\<hostInBrowser / >** element do manifestu aplikace (*\<projectname >. exe.manifest*) při [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] sestavení projektu.  
  
## <a name="see-also"></a>Viz také:  
 [MSBuild](../msbuild/msbuild.md)