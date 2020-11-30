---
title: Výchozí umístění příkazů, skupin a panelů nástrojů | Microsoft Docs
description: Přečtěte si o příkazech IDE, příkazech produktu a příkazech editoru, které se ve výchozím nastavení zobrazí v uživatelském rozhraní sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cacf8db933c7d56d44351da11b7b310bc0bdb8aa
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329879"
---
# <a name="default-command-group-and-toolbar-placement"></a>Výchozí umístění příkazů, skupin a panelů nástrojů
V případě jednotnosti a stability produktu zobrazuje uživatelské rozhraní ve výchozím nastavení určité skupiny příkazů a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje definice pro příkazy a skupiny příkazů. Sady VSPackage můžou také používat standardní příkazy a skupiny příkazů.

 Výchozí skupiny příkazů spadají do tří kategorií: příkazy integrovaného vývojového prostředí (IDE), příkazy produktu a příkazy editoru.

## <a name="default-ide-commands"></a>Výchozí příkazy IDE
 Výchozí panel nástrojů IDE obsahuje příkazy sdílené všemi produkty obsaženými v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Mezi ně patří příkazy týkající se obecných operací projektu, jako je například příkaz **Uložit** a příkaz **Přidat položku** . Sady VSPackage by neměly přidávat do nebo odečíst z tohoto panelu nástrojů s jednou výjimkou: Pokud produkt nebo VSPackage přidá nové okno nástroje, pak by okno mělo být přidáno do seznamu dostupných oken nástrojů v nabídce **zobrazení** . Nové produkty nebo VSPackage můžou přidat vlastní panel nástrojů.

## <a name="default-product-commands"></a>Výchozí příkazy produktu
 Každý produkt může integrované vývojové prostředí poskytnout pomocí vlastního výchozího panelu nástrojů, který obsahuje důležité a často používané příkazy. Je ale vhodné použít stávající nabídky a panely nástrojů, kdykoli je to možné, a doplnit je dalšími panely nástrojů pro konkrétní úkoly podle potřeby.

 Pole Priorita pro panel nástrojů určuje umístění řádku. Nulová priorita umístí panel nástrojů na třetí řádek (řádek 3) pod panelem nabídek (řádek 1) a **standardní** panel nástrojů (řádek 2). Proto se na řádku zobrazí další panely nástrojů (Priorita + 3). Následné panely nástrojů jsou umístěny na stejném řádku, pokud existuje prostor; v opačném případě se automaticky přesunou na další řádek.

## <a name="default-editor-commands"></a>Výchozí příkazy editoru
 VSPackage, který poskytuje vlastní editor, by měl poskytnout výchozí panel nástrojů, který obsahuje nejdůležitější a často používané příkazy v tomto editoru. Panel nástrojů editoru by měl být zobrazen, pokud je editor aktivní a měl by být skrytý, když Editor není aktivní. Tato viditelnost je ovládána v `VisibilityConstraints` prvku souboru *. vsct* .

 Panely nástrojů editoru by se měly umístit pod IDE a na panely nástrojů produktu.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a skupiny definované rozhraním IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
