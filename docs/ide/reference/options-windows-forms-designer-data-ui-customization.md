---
title: Možnosti, Návrhář formulářů systému Windows, Přizpůsobení uživatelského rozhraní dat
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e48777a50ddf66a8e5493698fb401ff7201de03e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114687"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Dialogové okno Možnosti: Návrhář formulářů windows > přizpůsobení uživatelského rozhraní dat

Toto dialogové okno definuje, které ovládací prvky se zobrazí v seznamu dostupných ovládacích prvků pro položky v okně Zdroje dat. Chcete-li jej otevřít, vyberte**možnosti** **nástrojů** > a potom vyberte možnost Přizpůsobení > **uživatelského rozhraní návrháře formulářů** **Windows**.

Ovládací prvek můžete vybrat z položky v okně Zdroje dat před jeho přetažením do formuláře v aplikaci pro Windows Forms. Dostupné ovládací prvky jsou určeny datovým typem položky. Každý datový typ má seznam platných přidružených ovládacích prvků definovaných v tomto dialogovém okně, včetně výchozího ovládacího prvku. Když přetáhnete položku z okna Zdroje dat do formuláře bez výběru ovládacího prvku, bude do formuláře přidán výchozí ovládací prvek pro datový typ vybrané položky.

Přizpůsobte seznam přidružených ovládacích prvků zaškrtnutím a zrušením zaškrtnutí políček dostupných ovládacích prvků pro každý datový typ. Chcete-li přidat ovládací prvek do seznamu, přidejte ovládací prvek, který implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute> atribut nebo <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> data-binding do panelu nástrojů. Ovládací prvek se pak zobrazí v seznamu ovládacích prvků pro datový typ. Další informace naleznete v [tématu How to: Add Custom Controls to the Data Sources window](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Datový typ

Zobrazí seznam typů, ke kterým přidružíte ovládací prvky. Tabulky jsou reprezentovány jako `[List]` datový typ. Sloupce jsou reprezentovány jako skutečný datový typ sloupce v podkladovém úložišti dat.

## <a name="associated-controls"></a>Přidružené ovládací prvky

Zobrazí seznam ovládacích prvků, které jsou přidruženy k vybranému datovému typu. Zaškrtněte nebo zrušte zaškrtnutí políčka vedle ovládacího prvku, chcete-li jej přidružit nebo zrušit jeho přidružení. Vybrané ovládací prvky se zobrazí v okně Zdroje dat pro sloupec databáze, který je vázán na přidružený datový typ.

## <a name="set-default"></a>Nastavit výchozí

Přiřadí vybraný typ ovládacího prvku jako výchozí pro vybraný datový typ. Výchozí ovládací prvek se zobrazí jako první výběr v místní nabídce pro sloupec databáze v okně Zdroje dat. Když přetáhnete položku z okna Zdroje dat do formuláře bez výběru ovládacího prvku, bude do formuláře přidán výchozí ovládací prvek pro datový typ vybrané položky.

Jako výchozí pro datový typ lze přiřadit pouze jeden typ ovládacího prvku.

## <a name="clear-default"></a>Vymazat výchozí

Odebere označení ovládacího prvku jako výchozí pro vybraný datový typ. Pokud pro vybraný datový typ není `[None]` žádné výchozí nastavení, zobrazí se jako první výběr v místní nabídce pro sloupec databáze tohoto typu.
