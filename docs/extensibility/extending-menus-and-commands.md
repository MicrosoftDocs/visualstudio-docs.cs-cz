---
title: Rozšíření nabídek a příkazů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711803"
---
# <a name="extend-menus-and-commands"></a>Rozšíření nabídek a příkazů
Příkazy jsou způsob, jakým do sady Visual Studio přidáváte akce a procesy. Ve většině případů jsou příkazy zobrazeny v nabídkách nebo panelech nástrojů. Šablona projektu VSPackage ukazuje, jak implementovat velmi základní příkaz. O něco delší, ale stále základní implementaci, viz [Vytvoření rozšíření s příkazem nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

 Další informace o příkazech, nabídkách a panelech nástrojů sady Visual Studio naleznete v [tématu Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md).

 Příkazy, nabídky a panely nástrojů jsou definovány v souboru *.vsct,* který je součástí projektů VSPackage. Informace o rozhraní IDE sady Visual Studio a souboru *.vsct* naleznete v části [Jak vspackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Následující témata vysvětlují, jak přidat různé druhy příkazů, nabídek a panelů nástrojů.

## <a name="in-this-section"></a>V tomto oddílu
- [Přidání nabídky do panelu nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Vysvětluje, jak přidat nabídku do horního panelu nabídek sady Visual Studio.

- [Svázání klávesových zkratek s položkami nabídky](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) Vysvětluje, jak přidat klávesovou zkratku (například CTRL + 3) k položce nabídky.

- [Přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md) Vysvětluje, jak přidat podnabídku do horní nabídky.

- [Přidání naposledy použitého seznamu do podnabídky](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) Vysvětluje, jak přidat seznam naposledy použitých.

- [Vytvoření opakovaně použitelných skupin tlačítek](../extensibility/creating-reusable-groups-of-buttons.md) Popisuje způsob seskupení položek příkazů tak, aby mohly být zahrnuty do více nabídek.

- [Přidání ikon do příkazů nabídky](../extensibility/adding-icons-to-menu-commands.md) Popisuje, jak přidat ikonu do příkazu na panelu nástrojů i v nabídce.

- [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md) Popisuje použití příznaku `TextChanges` k dynamické změně položky nabídky.

- [Změna vzhledu příkazu](../extensibility/changing-the-appearance-of-a-command.md) Popisuje, jak dynamicky povolit nebo zakázat příkaz.

- [Aktualizace uživatelského rozhraní](../extensibility/updating-the-user-interface.md) Popisuje, jak vynutit aktualizaci uživatelského rozhraní tak, aby odrážela nedávné změny.

- [Lokalizovat příkazy nabídky](../extensibility/localizing-menu-commands.md) Vysvětluje, jak lokalizovat příkazy nabídky.
