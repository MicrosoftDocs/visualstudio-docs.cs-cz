---
title: Volby, Textový editor, XML, Různé
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dd468945b1ab9ac83b219b9c8c396f017065e2be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568123"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Volby, Textový editor, XML, Různé

Pomocí stránky Různé **možnosti** můžete změnit nastavení automatického dokončování a schématu editoru XML. Chcete-li získat přístup k různé možnosti XML, zvolte**Možnosti** >  **nástroje** > **Textový editor** > **XML**a pak zvolte **Různé**.

## <a name="auto-insert"></a>Automatické vkládání

**Zavřít značky**

Textový editor přidává při vytváření elementů XML blízké značky. Pokud je vybrána počáteční značka prvku, editor vloží odpovídající značku zavřít, včetně odpovídající předpony oboru názvů. Toto políčko je ve výchozím nastavení zaškrtnuto.

**Atributové uvozovky**

Při vytváření atributů XML editor vloží `="` `"` znaky a umístí stříšku (**^**) do uvozovek. Toto políčko je ve výchozím nastavení zaškrtnuto.

**Deklarace oboru názvů**

Editor automaticky vloží deklarace oboru názvů všude tam, kde jsou potřeba. Toto políčko je ve výchozím nastavení zaškrtnuto.

**Ostatní značky (Komentáře, CDATA)**

Komentáře, CDATA, DOCTYPE, pokyny pro zpracování a další značky jsou automaticky dokončeny. Toto políčko je ve výchozím nastavení zaškrtnuto.

## <a name="network"></a>Network (Síť)

**Automatické stahování dtd a schémat**

Definice schémat a typů dokumentů (DTD) se automaticky stahují z umístění PROTOKOLU HTTP. Tato funkce používá System.Net s povolenou detekcí serveru autoproxy. Toto políčko je ve výchozím nastavení zaškrtnuto.

## <a name="outlining"></a>Sbalování

**Zadání režimu osnovy při otevření souborů**

Zapne funkci osnovy při otevření souboru. Toto políčko je ve výchozím nastavení zaškrtnuto.

## <a name="caching"></a>Ukládání do mezipaměti

**Schémata**

Určuje umístění mezipaměti schématu. Tlačítko **Procházet** otevře aktuální umístění mezipaměti schématu v novém okně. Výchozí umístění je *%VsInstallDir%\xml\Schémata*.

## <a name="see-also"></a>Viz také

- [Volby XML – formátování](options-text-editor-xml-formatting.md)
- [Nástroje XML v sadě Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
