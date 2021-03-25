---
title: Rozšiřování nabídek a příkazů | Microsoft Docs
description: Přečtěte si o příkazech, které přidávají akce a procesy do sady Visual Studio. Šablona projektu VSPackage ukazuje, jak implementovat velmi základní příkaz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a96978cdad45c669b607c18e12b2e492dcf95bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075208"
---
# <a name="extend-menus-and-commands"></a>Rozšiřování nabídek a příkazů
Příkazy představují způsob, jakým přidáváte akce a procesy do sady Visual Studio. Ve většině případů se příkazy zobrazují v nabídkách nebo na panelech nástrojů. Šablona projektu VSPackage ukazuje, jak implementovat velmi základní příkaz. Pro poněkud déle, ale i i pro základní implementaci, přečtěte si téma [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

 Další informace o příkazech, nabídkách a panelech nástrojů sady Visual Studio najdete v tématech [příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

 Příkazy, nabídky a panely nástrojů jsou definovány v souboru *. vsct* , který je součástí projektů VSPackage. Můžete najít informace o integrovaném vývojovém prostředí sady Visual Studio a souboru *. vsct* ve [způsobu, jakým sady VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Následující témata vysvětlují, jak přidat různé druhy příkazů, nabídek a panelů nástrojů.

## <a name="in-this-section"></a>V této části
- [Přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Vysvětluje, jak přidat nabídku do horního řádku nabídek sady Visual Studio.

- [Vázání klávesových zkratek k položkám nabídky](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Vysvětluje, jak přidat klávesovou zkratku (například CTRL + 3) k položce nabídky.

- [Přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md) Vysvětluje, jak přidat podnabídku do horní nabídky.

- [Přidat seznam naposledy použitých do podnabídky](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Vysvětluje, jak přidat seznam naposledy použitých.

- [Vytvoření opakovaně použitelných skupin tlačítek](../extensibility/creating-reusable-groups-of-buttons.md) Popisuje, jak seskupit položky příkazů, aby mohly být zahrnuty do více nabídek.

- [Přidat ikony do příkazů nabídky](../extensibility/adding-icons-to-menu-commands.md) Popisuje, jak přidat ikonu do příkazu na panelu nástrojů i v nabídce.

- [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md) Popisuje použití `TextChanges` příznaku pro povolení dynamické změny položky nabídky.

- [Změna vzhledu příkazu](../extensibility/changing-the-appearance-of-a-command.md) Popisuje, jak dynamicky povolit nebo zakázat příkaz.

- [Aktualizace uživatelského rozhraní](../extensibility/updating-the-user-interface.md) Popisuje, jak vynutit aktualizaci uživatelského rozhraní, aby odrážela nedávné změny.

- [Příkazy nabídky lokalizace](../extensibility/localizing-menu-commands.md) Vysvětluje, jak lokalizovat příkazy nabídky.
