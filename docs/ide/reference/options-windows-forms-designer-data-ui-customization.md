---
title: Možnosti, Návrhář formulářů, přizpůsobení uživatelského rozhraní dat
description: Naučte se, jak pomocí stránky pro přizpůsobení uživatelského rozhraní dat definovat, které ovládací prvky se zobrazí v seznamu dostupných ovládacích prvků pro položky v okně zdroje dat.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 46834dea30f41ebf0eb8629fe4dde0525288e82d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932303"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Dialogové okno Možnosti: Návrhář formulářů > přizpůsobení uživatelského rozhraní dat

Toto dialogové okno definuje, které ovládací prvky se zobrazí v seznamu dostupných ovládacích prvků pro položky v okně zdroje dat. Pokud ho chcete otevřít, vyberte  >  **Možnosti** nástrojů a pak vyberte **Návrhář formulářů**  >  **přizpůsobení uživatelského rozhraní**.

Můžete vybrat ovládací prvek z položky v okně zdroje dat před tím, než ho přetáhnete do formuláře v aplikaci model Windows Forms. Dostupné ovládací prvky jsou určeny datovým typem položky. Každý datový typ obsahuje seznam platných přidružených ovládacích prvků, které jsou definovány v tomto dialogovém okně, včetně výchozího ovládacího prvku. Když přetáhnete položku z okna zdroje dat do formuláře bez výběru ovládacího prvku, do formuláře se přidá výchozí ovládací prvek pro datový typ vybrané položky.

Přizpůsobte seznam přidružených ovládacích prvků zaškrtnutím a zrušením zaškrtnutí políček dostupných ovládacích prvků pro každý datový typ. Chcete-li přidat ovládací prvek do seznamu, přidejte ovládací prvek, který implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute> buď <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> atribut nebo atribut vazby dat do sady nástrojů. Ovládací prvek se pak zobrazí v seznamu ovládacích prvků pro datový typ. Další informace najdete v tématu [Postup: Přidání vlastních ovládacích prvků do okna zdroje dat](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Datový typ

Zobrazí seznam typů, ke kterým přiřadíte ovládací prvky. Tabulky jsou reprezentovány jako `[List]` datový typ. Sloupce jsou reprezentovány jako skutečný datový typ sloupce v podkladovém úložišti dat.

## <a name="associated-controls"></a>Přidružené ovládací prvky

Zobrazí seznam ovládacích prvků, které jsou přidruženy k vybranému datovému typu. Zaškrtněte nebo zrušte zaškrtnutí políčka vedle ovládacího prvku k přidružení nebo zrušení jeho přidružení. Vybrané ovládací prvky se zobrazí v okně zdroje dat pro sloupec databáze vázaný na přidružený datový typ.

## <a name="set-default"></a>Nastavit výchozí

Přiřadí vybraný typ ovládacího prvku jako výchozí pro vybraný datový typ. Výchozí ovládací prvek se zobrazí jako první výběr v místní nabídce pro sloupec databáze v okně zdroje dat. Když přetáhnete položku z okna zdroje dat do formuláře bez výběru ovládacího prvku, do formuláře se přidá výchozí ovládací prvek pro datový typ vybrané položky.

Jako výchozí hodnotu pro datový typ lze přiřadit pouze jeden typ ovládacího prvku.

## <a name="clear-default"></a>Vymazat výchozí

Odebere označení ovládacího prvku jako výchozího pro vybraný datový typ. Pokud pro vybraný datový typ neexistuje výchozí hodnota, `[None]` zobrazí se jako první výběr v místní nabídce pro sloupec databáze tohoto typu.
