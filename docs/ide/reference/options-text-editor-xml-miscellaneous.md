---
title: Možnosti, textový editor, XML, různé
description: Naučte se používat různé stránky v části XAML ke změně nastavení automatického dokončování a schématu pro editor XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a02a2a133031661ecbf9c3719f3b1993f3b20b5b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040117"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Možnosti, textový editor, XML, různé

Na stránce **různé** možnosti můžete změnit nastavení automatického dokončování a schématu pro editor XML. Chcete-li získat přístup k různým možnostem jazyka XML, zvolte možnost **nástroje**  >  **Options**  >  **textový editor**  >  **XML** a pak zvolte možnost **různé**.

## <a name="auto-insert"></a>Automaticky vložit

**Zavřít značky**

Textový editor přidá značky zavření při vytváření elementů XML. Pokud je vybrána počáteční značka elementu, Editor vloží zarovnávací uzavírací značku, včetně odpovídajícího prefixu oboru názvů. Toto zaškrtávací políčko je vybráno ve výchozím nastavení.

**Uvozovky atributů**

Při vytváření atributů XML Editor vloží `="` `"` znaky a a umístí kurzor () do uvozovek **^** . Toto zaškrtávací políčko je vybráno ve výchozím nastavení.

**Deklarace oboru názvů**

Editor automaticky vloží deklarace oboru názvů všude, kde jsou potřeba. Toto zaškrtávací políčko je vybráno ve výchozím nastavení.

**Jiné značky (komentáře, CDATA)**

Komentáře, CDATA, DOCTYPE, instrukce pro zpracování a jiné značky jsou AutoComplete. Toto zaškrtávací políčko je vybráno ve výchozím nastavení.

## <a name="network"></a>Síť

**Automaticky stahovat specifikace DTD a schémata**

Schémata a definice typu dokumentu (DTD) se automaticky stáhnou z umístění HTTP. Tato funkce používá System.Net s povoleným zjišťováním pro automatickou proxy server. Toto zaškrtávací políčko je vybráno ve výchozím nastavení.

## <a name="outlining"></a>Sbalování

**Po otevření souborů přejít do režimu sbalení**

Zapne funkci sbalení při otevření souboru. Toto zaškrtávací políčko je vybráno ve výchozím nastavení.

## <a name="caching"></a>Ukládání do mezipaměti

**Schémata**

Určuje umístění mezipaměti schématu. Tlačítko **Procházet** otevře aktuální umístění mezipaměti schématu v novém okně. Výchozí umístění je *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Viz také

- [Možnosti XML – formátování](options-text-editor-xml-formatting.md)
- [Nástroje XML v sadě Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
