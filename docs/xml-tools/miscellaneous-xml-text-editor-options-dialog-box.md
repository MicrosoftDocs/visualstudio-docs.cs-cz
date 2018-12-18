---
title: Různé, XML, Textový editor, dialogové okno Možnosti
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd6ee70f99f3b82505d210ab95f8359b5c7f90c8
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571767"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Různé, XML, textový Editor, dialogové okno Možnosti

Toto dialogové okno umožňuje změnit nastavení automatického dokončování a schématu pro Editor XML. Dostanete **možnosti** dialogové okno z **nástroje** nabídky.

> [!NOTE]
> Tato nastavení jsou k dispozici, když vyberete **textového editoru** složku, **XML** složku a potom **různé** možnost z **možnosti** dialogové okno.


## <a name="auto-insert"></a>Automatické vkládání
 **Zavřít značky**

 Pokud automatické dokončování nastavení zaškrtnuté, editor automaticky přidá koncová značka, když zadáte pravé ostré závorky (>) zavřete úvodní značky, pokud už není uzavřený značky. Toto je výchozí chování.

 Dokončení prázdný element není závislá na nastavení automatické dokončování. Můžete vždy automatického dokončování prázdný element zadáním zpětné lomítko (/).

 **Atribut uvozovky**

 Při vytváření atributy XML, editor vloží `=" "` znaků a umisťuje šipka nahoru (^) uvnitř dvojitých uvozovek.

 Ve výchozím nastavení je zaškrtnuto.

 **Namespace – deklarace**

 Editor automaticky vloží deklarace oboru názvů, bez ohledu na jsou potřeba.

 Ve výchozím nastavení je zaškrtnuto.

 **Další kód (komentáře, CDATA)**

 Komentáře, CDATA, DOCTYPE, pokyny pro zpracování a jiné značky jsou automaticky dokončit.

 Ve výchozím nastavení je zaškrtnuto.

## <a name="network"></a>Sítě
 **Automaticky stahovat specifikace DTD a schémat.**

 Schémata a definice typu dokumentu (specifikace DTD) se automaticky stáhnou z umístění protokolu HTTP. Tato funkce používá System.Net s detekce automaticky proxy serveru povoleno.

 Ve výchozím nastavení je zaškrtnuto.

## <a name="outlining"></a>Sbalování
 **Zadejte popisující režimu při otevírání souborů**

 Spustí funkci popisující při otevření souboru.

 Ve výchozím nastavení je zaškrtnuto.

## <a name="caching"></a>Ukládání do mezipaměti
 **Schémata**

 Určuje umístění mezipaměti schématu. Na tlačítko Procházet (**...** ) otevře **Procházet adresář** dialogové okno na aktuální umístění mezipaměti schématu. Můžete vybrat jiný adresář, nebo můžete vybrat složku v dialogovém okně klikněte pravým tlačítkem a zvolte **otevřete** vidět co je v adresáři.

## <a name="see-also"></a>Viz také:

- [Vlastnosti dokumentu XML, vlastnosti – okno](../xml-tools/xml-document-properties-properties-window.md)
- [Součásti editoru XML](../xml-tools/xml-editor-components.md)