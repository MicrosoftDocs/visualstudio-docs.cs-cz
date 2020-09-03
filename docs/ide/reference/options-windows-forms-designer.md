---
title: Možnosti, Návrhář formulářů, obecné
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568058"
---
# <a name="options-dialog-box-windows-forms-designer"></a>Dialogové okno Možnosti: Návrhář formulářů

Stránka možnosti Návrhář formulářů umožňuje nastavit předvolby pro mřížky a další funkce Návrhář formulářů v sadě Visual Studio. V nabídce **nástroje** otevřete dialogové okno **Možnosti** .

## <a name="code-generation-settings"></a>Nastavení generování kódu

**Generování optimalizovaného kódu**\
Povoluje generování optimalizovaného kódu. Některé ovládací prvky nemusí být kompatibilní s tímto režimem. Aby se tato změna projevila, musí být aplikace Visual Studio zavřená a znovu otevřená.

## <a name="high-dpi-support"></a>Podpora vysokého rozlišení DPI

**Oznámení škálování DPI**\
Zobrazit zprávu v Návrháři Windows Form, která může restartovat Visual Studio s 100% škálováním Další informace najdete v tématu [zakázání sledování dpi v aplikaci Visual Studio](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio).

## <a name="layout-settings"></a>Nastavení rozložení

**Výchozí velikost buňky mřížky**\
Nastaví mezery v pixelech mezi vodorovnou a svislou mřížkou v návrháři. Výchozí velikost je 8, 8. Maximální velikost je 200, 200.

**Režim rozložení**\
Určuje systém zarovnání, který se má použít pro rozložení. Můžete zvolit buď SnapToGrid nebo zarovnávacím čárám.

**Zobrazit mřížku**\
Určuje, zda budou v Návrháři zobrazeny mřížky pro změnu velikosti. Ve výchozím nastavení je mřížka zapnutá.

**Přichycení k mřížce**\
Určuje, zda budou návrháři přitahovat objekty a ovládací prvky do mřížky. Jinými slovy, změnu velikosti a přesunu prvků v návrháři jsou omezeny na GridSize přírůstek, pokud je tato funkce zapnuta. Díky tomu, že je SnapToGrid zapnuté, je snazší přesně rozmístit různé aspekty uživatelského rozhraní, ale omezuje svobodu, se kterou může ovládací prvek umístit. Ve výchozím nastavení je SnapToGrid zapnutý.

## <a name="object-bound-smart-tag-settings"></a>Nastavení inteligentních značek objektů vázaných na objekty

**Automaticky otevřít inteligentní značky**\
Určuje, zda ovládací prvky a komponenty zobrazují inteligentní značky. Ne všechny ovládací prvky a komponenty podporují inteligentní značky.

## <a name="refactoring"></a>Refaktoring

**Povolit refaktoring při přejmenování**\
Při nastavení na `true` je provedena operace refaktoringu přejmenování při přejmenování součásti z okna okno Vlastnosti nebo Osnova dokumentu.

## <a name="toolbox"></a>Sada nástrojů

**Automaticky naplnit panel nástrojů**\
Určuje, zda je okno panelu nástrojů vyplněno automaticky komponentami a ovládacími prvky sestavenými projektem.
