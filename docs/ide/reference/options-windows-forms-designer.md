---
title: Možnosti, Návrhář formulářů systému Windows, Obecné
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2a72b27dc2277501d0e0957c8b89b551f4d6852d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568058"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Dialogové okno Možnosti: Návrhář formulářů systému Windows

Stránka možností návrháře formulářů systému Windows umožňuje nastavit předvolby pro mřížky a další funkce Návrháře formulářů Systému Windows v sadě Visual Studio. Otevřete dialogové okno **Volby** z nabídky **Nástroje.**

## <a name="code-generation-settings"></a>Nastavení generování kódu

**Optimalizované generování kódu**\
Umožňuje optimalizované generování kódu. Některé ovládací prvky nemusí být kompatibilní s tímto režimem. Aby se tato změna projevila, musí být sada Visual Studio uzavřena a znovu otevřena.

## <a name="high-dpi-support"></a>Podpora vysokého DPI

**Oznámení o změně měřítka DPI**\
Zobrazí zprávu v Návrháři formulářů systému Windows, která může restartovat visual studio se 100% škálováním. Další informace naleznete [v tématu Disable DPI-awareness in Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Nastavení rozložení

**Výchozí velikost buňky mřížky**\
Nastaví mezery v obrazových bodech mezi vodorovnou a svislou mřížkou v návrháři. Výchozí velikost je 8, 8. Maximální velikost je 200 200.

**Režim rozložení**\
Určuje systém zarovnání, který má být používán pro rozvržení. Můžete zvolit buď SnapToGrid nebo Snaplines.

**Zobrazit mřížku**\
Určuje, zda návrháři zobrazí mřížku velikosti. Ve výchozím nastavení je mřížka zapnutá.

**Přichytit k mřížce**\
Určuje, zda návrháři přichytí objekty a ovládací prvky k mřížce. Jinými slovy, změna velikosti a přesun prvků v návrháři jsou omezeny na přírůstek GridSize při zapnutí této funkce. Zapnutí snaptogridu usnadňuje přesné zařazování různých aspektů uživatelského rozhraní, ale omezuje svobodu, s jakou lze umístit ovládací prvky. Ve výchozím nastavení je snaptogrid zapnutý.

## <a name="object-bound-smart-tag-settings"></a>Nastavení inteligentních značek vázaných na objekt

**Automatické otevírání inteligentních značek**\
Určuje, zda ovládací prvky a součásti zobrazují inteligentní značky. Inteligentní značky nepodporují všechny ovládací prvky a součásti.

## <a name="refactoring"></a>Refaktoring

**Povolit refaktoring při přejmenování**\
Pokud je `true`nastavena na , provede se přejmenování operace refaktoringu při přejmenování komponenty z okna Vlastnosti nebo okna Osnova dokumentu.

## <a name="toolbox"></a>Sada nástrojů

**Automaticky naplnit panel nástrojů**\
Určuje, zda je okno panelu nástrojů automaticky naplněno součástmi a ovládacími prvky vytvořenými projektem.
