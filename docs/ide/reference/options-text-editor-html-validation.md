---
title: Možnosti, textový editor, HTML (webové formuláře), ověřování
description: Naučte se, jak pomocí stránky ověřování v oddílu HTML nastavit předvolby pro způsob, jakým Editor HTML kontroluje syntaxi značek HTML v dokumentu.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 769a16c0dd1275c435f8cd0b496097a5b1575160
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932511"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Možnosti, textový editor, HTML (webové formuláře), ověřování

Stránka možnosti **ověřování** slouží k nastavení předvoleb pro způsob, jakým Editor HTML kontroluje SYNTAXI značek HTML v dokumentu. Chcete-li získat přístup k této stránce, v řádku nabídek zvolte  >  **možnost** nástroje a poté rozbalte položku **textový editor**  >  **HTML (webové formuláře)**  >  **ověřování**.

## <a name="validation"></a>Ověřování

- **Pro detekci schématu ověření použít typ DOCTYPE**

   Schéma určuje, které prvky, atributy a velká písmena jsou v tomto schématu platné. Určuje také značky a atributy, které jsou k dispozici v technologii IntelliSense.

   Tuto možnost vyberte, pokud chcete, aby aplikace Visual Studio používala obsah< stránky **! TYP DOCTYPE>** deklarace a element **HTML** pro určení schématu. Například pokud vyberete tuto možnost a stránka obsahuje deklaraci `<!DOCTYPE html>` , Visual Studio použije schéma HTML5. Nicméně pokud má značka **jazyka HTML** atribut **xmlns** , například `<html xmlns="http://www.w3.org/1999/xhtml">` , Visual Studio používá schéma XHTML5.

- **Cíl, když se nenašel žádný typ DOCTYPE**

   Vyberte schéma, proti kterému se má ověřit, pokud není **<! Deklarace>DOCTYPE** na stránce

  - **Zobrazit chyby**

     Zaškrtnutím políčka povolíte ověřování. Pokud políčko není zaškrtnuté, Editor nebude označovat chyby ověřování.

     Další zaškrtávací políčka umožňují doladit ověřování zadáním jednotlivých typů chyb, které má Editor označit.

     > [!NOTE]
     > Některá schémata nenabízejí možnosti pro označení jednotlivých typů chyb. Například pokud jako cílové schéma zvolíte **XHTML 1,1** , všechna zaškrtávací políčka jsou zakázána. V této instanci jsou označeny všechny typy chyb.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
