---
title: Různé, XML, textový editor, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656239"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Různé, XML, Textový editor, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno umožňuje změnit nastavení automatického dokončování a schématu pro editor XML. K dialogovému oknu **Možnosti** získáte přístup z nabídky **nástroje** .

> [!NOTE]
> Tato nastavení jsou k dispozici, když vyberete složku **textový editor** , složku **XML** a potom možnost **různé** v dialogovém okně **Možnosti** .

## <a name="auto-insert"></a>Automaticky vložit
 **Zavřít značky** Pokud je zaškrtnuto nastavení automatického dokončování, Editor automaticky přidá koncovou značku, když zadáte pravou ostrou závorku (>) k uzavření počáteční značky, pokud již značka není uzavřená. Toto je výchozí chování.

 Dokončení prázdného prvku nezávisí na nastavení automatického dokončování. Prázdný prvek můžete vždy automaticky dokončovat zadáním zpětného lomítka (/).

 **Uvozovky atributů** Při vytváření atributů XML Editor vloží `=" "`é znaky a umístí kurzor (^) do dvojitých uvozovek.

 Ve výchozím nastavení je zaškrtnuto.

 **Deklarace oboru názvů** Editor automaticky vloží deklarace oboru názvů všude, kde jsou potřeba.

 Ve výchozím nastavení je zaškrtnuto.

 **Jiné značky (komentáře, CDATA)** Komentáře, CDATA, DOCTYPE, instrukce pro zpracování a další značky jsou automaticky dokončeny.

 Ve výchozím nastavení je zaškrtnuto.

## <a name="network"></a>Sítě
 **Automaticky stahovat specifikace DTD a schémata** Schémata a definice typu dokumentu (DTD) se automaticky stáhnou z umístění HTTP. Tato funkce používá System.Net s povolenou detekcí automatického proxy server.

 Ve výchozím nastavení je zaškrtnuto.

## <a name="outlining"></a>Sbalování
 **Po otevření souborů přejít do režimu sbalení** Zapne funkci sbalení při otevření souboru.

 Ve výchozím nastavení je zaškrtnuto.

## <a name="caching"></a>Ukládání do mezipaměti
 **Schémata** Určuje umístění mezipaměti schématu. Tlačítko Procházet ( **...** ) otevře dialogové okno **Procházet adresářem** v aktuálním umístění mezipaměti schémat. Můžete vybrat jiný adresář, nebo můžete vybrat složku v dialogovém okně, kliknout pravým tlačítkem myši a kliknutím na **otevřít** zobrazit informace o tom, co se nachází v adresáři.

## <a name="see-also"></a>Viz také
 [Vlastnosti dokumentu XML, vlastnosti](../xml-tools/xml-document-properties-properties-window.md) [editoru XML](../xml-tools/xml-editor-components.md) okna
