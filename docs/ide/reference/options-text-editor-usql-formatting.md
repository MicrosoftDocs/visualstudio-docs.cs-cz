---
title: Možnosti formátování editoru U-SQL
description: Naučte se, jak pomocí stránky možnosti formátování a jejích podstránek nastavit možnosti formátování kódu v editoru kódu při programování v U-SQL.
ms.custom: SEO-VS-2020
ms.date: 01/17/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Formatting.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf65c6c80bbcf24d48f5da584349cc4d6b26049
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040287"
---
# <a name="options-text-editor-u-sql-formatting"></a>Možnosti, textový editor, U-SQL, formátování

Pomocí stránky možnosti **formátování** můžete nastavit možnosti formátování kódu v editoru kódu. Chcete-li získat přístup k této **Tools** stránce Možnosti, klikněte na tlačítko  >  **Možnosti** nástrojů. V dialogovém okně **Možnosti** vyberte možnost **textový editor**  >  **formátování U-SQL**  >  **Formatting**.

## <a name="general-page"></a>Stránka Obecné

### <a name="general-settings"></a>Obecná nastavení

Tato nastavení mají vliv na to, *kdy* Editor kódu aplikuje možnosti formátování na kód.

- **Automaticky formátovat dokončený příkaz při zadání středníku**

   Když je tato možnost vybrána, formátuje příkazy při výběru středníku klíče v závislosti na možnostech formátování vybraných pro Editor.

- **Automaticky formátovat při vložení**

   Když se tato možnost vybere, zformátuje text, který se vloží do editoru, aby odpovídal možnostem formátování vybraným pro Editor.

## <a name="preview-windows"></a>Náhled oken

**Odsazení**, **nové řádky** a **mezery** na jednotlivých stránkách zobrazují v dolní části okno náhledu. V okně náhledu se zobrazí efekt jednotlivých možností. Chcete-li použít okno náhledu, vyberte možnost formátování. V okně náhledu se zobrazí příklad vybrané možnosti. Když změníte nastavení tak, že vyberete zaškrtávací políčko, okno náhledu se aktualizuje a zobrazí efekt nového nastavení.

### <a name="indentation-remarks"></a>Poznámky k odsazení

Možnosti odsazení na stránkách **karet** pro jednotlivé jazyky určují, kde Editor kódu umístí kurzor po stisknutí klávesy **ENTER** na konci řádku. Možnosti odsazení v části **formátování** platí, pokud je kód automaticky naformátován, například:

- Když vložíte kód do souboru při výběru **automaticky formátovat při vložení**
- Když je blok, který je naformátován, zadán ručně

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
