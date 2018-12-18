---
title: Ikony zobrazení třídy a prohlížeče objektů
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ff94e67291bff8dc00d3fa63976f283da485f6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745786"
---
# <a name="class-view-and-object-browser-icons"></a>Ikony zobrazení tříd a prohlížeče objektů

**Třídy zobrazení** a **Prohlížeč objektů** zobrazit ikony, které představují entity kódu, například obory názvů, třídy, funkce a proměnné. Následující tabulka ukazuje a popisuje ikony.

|Ikona|Popis|Ikona|Popis|
|----------|-----------------|----------|-----------------|
|![Namespace – Symbol](../ide/media/vxnamespace_icon.gif)|Obor názvů|![Deklarace – Symbol](../ide/media/vxmethod_icon.gif)|Metody nebo funkce|
|![Ikona – třída](../ide/media/vxclass_icon.gif)|Třída|![Symbol operátoru](../ide/media/vxoperator_icon.gif)|Operátor|
|![Rozhraní Symbol typu Lupa](../ide/media/vxinterface_icon.gif)|Rozhraní|![Vlastnost Symbol](../ide/media/vxproperty_icon.gif)|Vlastnost|
|![Struktura – Symbol](../ide/media/vxstruct_icon.gif)|Struktura|![Ikona pole.](../ide/media/vxfield_icon.gif)|Pole nebo proměnná|
|![Union – Symbol](../ide/media/vxunion_icon.gif)|Unie|![Symbol událostí](../ide/media/vxevent_icon.gif)|Událost|
|![Symbol – výčet](../ide/media/vxenum_icon.gif)|Výčet|![Konstantní ikonu](../ide/media/vxconstant_icon.gif)|Konstanta|
|![Typ definice symbolu](../ide/media/vxtypedef_icon.gif)|Definice TypeDef|![Položka výčtu – Symbol](../ide/media/vxenumitem_icon.gif)|Položka výčtu|
|![Symbol modul aplikace Visual Studio](../ide/media/vxmodule_icon.gif)|Modul|![Symbol položka mapy](../ide/media/vxmapitem_icon.gif)|Mapování položky|
|![Symbol – metoda rozšíření](../ide/media/extensionmethod.gif)|Metody rozšíření|![Deklarace – Symbol](../ide/media/vxmethod_icon.gif)|Externí deklarace|
|![Delegát – Symbol](../ide/media/vxdelegate_icon.gif)|Delegát|![Ikona chyby pro zobrazení tříd a prohlížeč objektů](../ide/media/erroricon.gif)|Chyba|
|![Výjimka – Symbol](../ide/media/vxexception_icon.gif)|Výjimka|![Šablona – Symbol](../ide/media/vxtemplate_icon.gif)|Šablony|
|![Map – Symbol](../ide/media/vxmap_icon.gif)|mapy|![Chyba vykřičníku bodu Symbol](../ide/media/vxerror_icon.gif)|Neznámé|
|![Typ přesměrování Symbol](../ide/media/ob_type_forward.gif)|Předávání typů|||

## <a name="signal-icons"></a>Signální ikony

Následující signální ikony platí pro všechny předchozí ikony a určit jejich usnadnění.

|Ikona|Popis|
|----------|-----------------|
|\<Žádná ikona signál >|Veřejné. Přístupné z kdekoli v této komponentě a z libovolné součásti, které na ni odkazuje.|
|![Signál chráněné – Symbol](../ide/media/vxsignal_icon_key.gif)|Chráněný. Přístupné z obsahující třídy nebo typu nebo zařízení odvozené z obsahující třídy nebo typu.|
|![Signál privátní – Symbol](../ide/media/vxsignal_icon_lock.gif)|Privátní. Přístupné pouze v obsahující třídy nebo typu.|
|![Signál zapečetěná – Symbol](../ide/media/vxsignal_icon_envelope.gif)|Zapečetěné.|
|![Signal Friend&#47;interní Symbol](../ide/media/vxsignal_icon_diamond.gif)|Friend nebo interní. Dostupné jenom z projektu.|
|![Ikona šipky signál](../ide/media/vxsignal_icon_arrow.gif)|Zástupce. Zástupce k objektu.|

> [!NOTE]
> Pokud zdrojové řízení databáze je součástí projektu, další signální ikony zobrazují označující stav zdrojového kódu, například změnami nebo rezervována.

## <a name="see-also"></a>Viz také:

- [Zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md)