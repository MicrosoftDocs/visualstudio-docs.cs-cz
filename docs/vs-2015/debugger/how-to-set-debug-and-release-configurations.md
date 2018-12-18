---
title: 'Postupy: Konfigurace nastavení ladění a verzí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ba827fda69b1dc455df4efe9c9f6eb83687780f3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758499"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Postupy: Nastavení konfigurace ladění a verzí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty aplikace Visual Studio mají samostatné verze a ladění konfigurace pro váš program. Jak naznačují názvy, sestavení verze ladění pro ladění a verze vydání pro konečnou distribuci vydání.  
  
 Konfigurace ladění programu je kompilován sestaví neoptimalizovaná a obsahující symbolické ladicí informace. Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vytvořenými pokyny je složitější.  
  
 Konfigurace programu pro vydání neobsahuje žádné symbolické ladicí informace a je plně optimalizována. Ladit informace mohou být generovány v souborech PDB v závislosti na využívaných možnostech kompilátoru. Vytváření souborů PDB může být velmi užitečné, pokud budete muset později ladit vydané verze.  
  
 Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).  
  
 Můžete změnit konfiguraci sestavení z **sestavení** nabídky, z panelu nástrojů nebo na stránkách vlastností projektu. Stránky vlastností projektu jsou specifické pro jazyk. Následující postup ukazuje, jak změnit konfiguraci sestavení z nabídky a panelu nástrojů. Další informace o tom, jak změnit konfiguraci sestavení v projektech v různých jazycích najdete v níže uvedené části na odkaz Příbuzná témata.  
  
### <a name="to-change-the-build-configuration"></a>Chcete-li změnit konfiguraci sestavení  
  
1.  V nabídce sestavení: klikněte na tlačítko **sestavení / nástroje Configuration Manager**a pak vyberte **ladění** nebo **vydání**.  
  
2.  Na panelu nástrojů zvolte buď **ladění** nebo **vydání** z **konfigurace řešení** pole se seznamem.  
  
     ![konfigurace sestavení nástrojů](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Tento panel nástrojů není k dispozici ve verzích Express. Můžete použít **sestavit řešení F6** a **zahájit ladění F5** položky nabídky pro výběr konfigurace.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Nastavení projektu pro jazyk C# konfiguraci ladění](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Konfigurace ladění projektu v jazyce Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md)   
 [Konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)



