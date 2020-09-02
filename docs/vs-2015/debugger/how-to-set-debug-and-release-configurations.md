---
title: 'Postupy: nastavení konfigurace ladění a vydání | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703637"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Postupy: Nastavení konfigurace ladění a verzí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty sady Visual Studio mají samostatné konfigurace vydaných verzí a ladění pro váš program. Jak názvy implikuje, sestavíte ladicí verzi pro ladění a verzi Release pro konečnou distribuci vydaných verzí.  
  
 Konfigurace ladění programu je kompilována s úplnými symbolickými informacemi o ladění a bez optimalizace. Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější.  
  
 Konfigurace vydané verze vašeho programu neobsahuje žádné symbolické ladicí informace a je plně optimalizována. Informace o ladění mohou být generovány v souborech PDB v závislosti na použitých možnostech kompilátoru. Vytváření souborů PDB může být velmi užitečné, pokud budete později muset ladit prodejní verzi.  
  
 Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).  
  
 Můžete změnit konfiguraci sestavení z nabídky **sestavit** , z panelu nástrojů nebo na stránkách vlastností projektu. Stránky vlastností projektu jsou specifické pro jazyk. Následující postup ukazuje, jak změnit konfiguraci sestavení z nabídky a panelu nástrojů. Další informace o tom, jak změnit konfiguraci sestavení v projektech v různých jazycích, najdete v níže uvedené části Příbuzná témata.  
  
### <a name="to-change-the-build-configuration"></a>Změna konfigurace sestavení  
  
1. V nabídce sestavení: klikněte na **sestavit/Configuration Manager**a pak vyberte **ladit** nebo **vydat**.  
  
2. Na panelu nástrojů vyberte buď možnost **ladění** , nebo **vydaná verze** v seznamu **Konfigurace řešení** .  
  
     ![konfigurace sestavení panelu nástrojů](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Tento panel nástrojů není k dispozici v edicích Express. K výběru konfigurace můžete použít položky nabídky **Sestavit řešení F6** a **Spustit ladění F5** .  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Nastavení projektu pro konfiguraci ladění v jazyce C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Nastavení projektu pro konfiguraci Visual Basicho ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Postupy: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)   
 [Ladit a vydávat konfigurace projektů](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)
