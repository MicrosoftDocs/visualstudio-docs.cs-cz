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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b65edc2b6c48bc76075e909d0f9bd1341a1b6dd8
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040560"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Možnosti, textový editor, HTML (webové formuláře), ověřování

Stránka možnosti **ověřování** slouží k nastavení předvoleb pro způsob, jakým Editor HTML kontroluje SYNTAXI značek HTML v dokumentu. Chcete-li získat přístup k této stránce, v řádku **Tools** nabídek zvolte  >  **možnost** nástroje a poté rozbalte položku **textový editor**  >  **HTML (webové formuláře)**  >  **ověřování**.

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
