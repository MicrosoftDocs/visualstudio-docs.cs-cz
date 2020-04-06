---
title: Výchozí umístění příkazu, skupiny a panelu nástrojů | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708894"
---
# <a name="default-command-group-and-toolbar-placement"></a>Výchozí umístění příkazu, skupiny a panelu nástrojů
Pro jednotnost a stabilitu produktu ui zobrazuje určité [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] skupiny příkazů ve výchozím nastavení a poskytuje definice pro příkazy a skupiny příkazů. VSPackages můžete také použít standardní příkazy a skupiny příkazů.

 Výchozí skupiny příkazů spadají do tří kategorií: příkazy IDE, příkazy produktu a příkazy editoru.

## <a name="default-ide-commands"></a>Výchozí příkazy ide
 Výchozí panel nástrojů ide obsahuje příkazy sdílené [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]všemi produkty obsaženými v . Patří mezi ně příkazy týkající se obecných operací projektu, jako je například příkaz **Uložit** a **Příkaz Přidat položku.** VSPackages by neměla přidávat nebo odečítat z tohoto panelu nástrojů, s jednou výjimkou: Pokud produkt nebo VSPackage přidá nové okno nástroje, okno by měla být přidána do seznamu dostupných oken nástrojů v nabídce **Zobrazit.** Nové produkty nebo VSPackages můžete přidat svůj vlastní panel nástrojů.

## <a name="default-product-commands"></a>Výchozí příkazy produktu
 Každý produkt může ide poskytnout vlastní výchozí panel nástrojů, který obsahuje důležité a často používané příkazy. Je však nejlepší použít existující nabídky a panely nástrojů, kdykoli je to možné, a podle potřeby je doplnit o další panely nástrojů specifické pro úkoly.

 Pole priority panelu nástrojů určuje umístění řádku. Nulová priorita umístí panel nástrojů na třetí řádek (řádek 3), pod řádek nabídek (řádek 1) a **standardní** panel nástrojů (řádek 2). Proto se na řádku zobrazují další panely nástrojů (priorita + 3). Následující panely nástrojů jsou umístěny na stejném řádku, pokud je prostor; v opačném případě jsou automaticky přesunuty do dalšího řádku.

## <a name="default-editor-commands"></a>Výchozí příkazy editoru
 VSPackage, který poskytuje vlastní editor by měl poskytnout výchozí panel nástrojů, který obsahuje nejdůležitější a často používané příkazy v tomto editoru. Panel nástrojů editoru by se měl zobrazit, když je editor aktivní, a měl by být skrytý, když editor není aktivní. Tato viditelnost je řízena v elementu `VisibilityConstraints` souboru *.vsct.*

 Editor panely nástrojů by měly být umístěny pod IDE a panely nástrojů produktu.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a skupiny definované ide](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
