---
title: Rozšiřování nabídek a příkazů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 83d9dc45863f1ed1b5e11c17b9e922b62b0186dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204523"
---
# <a name="extending-menus-and-commands"></a>Rozšiřování nabídek a příkazů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příkazy představují způsob, jakým přidáváte akce a procesy do sady Visual Studio. Ve většině případů se příkazy zobrazují v nabídkách nebo na panelech nástrojů. Šablona projektu VSPackage ukazuje, jak implementovat velmi základní příkaz. Pro poněkud déle, ale i i pro základní implementaci, přečtěte si téma [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Další informace o příkazech, nabídkách a panelech nástrojů sady Visual Studio najdete v tématech [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Příkazy, nabídky a panely nástrojů jsou definovány v souboru. vsct, který je součástí projektů VSPackage. Můžete najít informace o integrovaném vývojovém prostředí sady Visual Studio a souboru. vsct ve [způsobu, jakým sady VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Následující témata vysvětlují, jak přidat různé druhy příkazů, nabídek a panelů nástrojů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přidání nabídky do řádku nabídek v sadě Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Vysvětluje, jak přidat nabídku do horního řádku nabídek sady Visual Studio.  
  
 [Vytváření vazeb mezi klávesovými zkratkami a položkami nabídky](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Vysvětluje, jak přidat klávesovou zkratku (například CTRL + 3) k položce nabídky.  
  
 [Přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md)  
 Vysvětluje, jak přidat podnabídku do horní nabídky.  
  
 [Přidání seznamu Naposledy použité do podnabídky](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Vysvětluje, jak přidat seznam naposledy použitých.  
  
 [Vytváření znovu použitelných skupin tlačítek](../extensibility/creating-reusable-groups-of-buttons.md)  
 Popisuje, jak seskupit položky příkazů, aby mohly být zahrnuty do více nabídek.  
  
 [Přidávání ikon k příkazům nabídky](../extensibility/adding-icons-to-menu-commands.md)  
 Popisuje, jak přidat ikonu do příkazu na panelu nástrojů i v nabídce.  
  
 [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md)  
 Popisuje použití `TextChanges` příznaku pro povolení dynamické změny položky nabídky.  
  
 [Změna vzhledu příkazu](../extensibility/changing-the-appearance-of-a-command.md)  
 Popisuje, jak dynamicky povolit nebo zakázat příkaz.  
  
 [Aktualizace uživatelského rozhraní](../extensibility/updating-the-user-interface.md)  
 Popisuje, jak vynutit aktualizaci uživatelského rozhraní, aby odrážela nedávné změny.  
  
 [Lokalizace příkazů nabídky](../extensibility/localizing-menu-commands.md)  
 Vysvětluje, jak lokalizovat příkazy nabídky.  
  
## <a name="related-sections"></a>Související oddíly
