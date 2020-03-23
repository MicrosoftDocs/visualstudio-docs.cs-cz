---
title: Ikony zobrazení třídy a prohlížeče objektů
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6589d40d8f897eb8df7f108f53973af268d1edc9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588392"
---
# <a name="class-view-and-object-browser-icons"></a>Ikony zobrazení tříd a prohlížeče objektů

**Zobrazení tříd** a **prohlížeč objektů** zobrazují ikony, které představují entity kódu, například obory názvů, třídy, funkce a proměnné. Následující tabulka znázorňuje a popisuje ikony.

|Ikona|Popis|Ikona|Popis|
|----------|-----------------|----------|-----------------|
|![Symbol oboru názvů](../ide/media/vxnamespace_icon.gif)|Obor názvů|![Symbol deklarace](../ide/media/vxmethod_icon.gif)|Metoda nebo funkce|
|![Ikona třídy](../ide/media/vxclass_icon.gif)|Třída|![Symbol operátora](../ide/media/vxoperator_icon.gif)|Operátor|
|![Symbol rozhraní lízátka](../ide/media/vxinterface_icon.gif)|Rozhraní|![Symbol vlastnosti](../ide/media/vxproperty_icon.gif)|Vlastnost|
|![Symbol struktury](../ide/media/vxstruct_icon.gif)|Struktura|![Ikona pole](../ide/media/vxfield_icon.gif)|Pole nebo proměnná|
|![Symbol sjednocení](../ide/media/vxunion_icon.gif)|Sjednocení|![Symbol události](../ide/media/vxevent_icon.gif)|Událost|
|![Symbol výčtu](../ide/media/vxenum_icon.gif)|Výčet|![Ikona konstanta](../ide/media/vxconstant_icon.gif)|Trvalé|
|![Symbol definice textu](../ide/media/vxtypedef_icon.gif)|Typedef|![Výčet symbolu položky](../ide/media/vxenumitem_icon.gif)|Výčet položky|
|![Symbol modulu visual studia](../ide/media/vxmodule_icon.gif)|Modul|![Symbol položky mapy](../ide/media/vxmapitem_icon.gif)|Mapovat položku|
|![Symbol rozšiřující metody](../ide/media/extensionmethod.gif)|Metoda rozšíření|![Symbol deklarace](../ide/media/vxmethod_icon.gif)|Externí prohlášení|
|![Symbol delegáta](../ide/media/vxdelegate_icon.gif)|Delegát|![Ikona chyby pro zobrazení tříd a prohlížeč objektů](../ide/media/erroricon.gif)|Chyba|
|![Symbol výjimky](../ide/media/vxexception_icon.gif)|Výjimka|![Symbol šablony](../ide/media/vxtemplate_icon.gif)|Šablona|
|![Symbol mapy](../ide/media/vxmap_icon.gif)|Mapa|![Symbol bodu vykřičníku chyby](../ide/media/vxerror_icon.gif)|Není známo|
|![Symbol přeposílání textu](../ide/media/ob_type_forward.gif)|Předávání typů|||

## <a name="signal-icons"></a>Ikony signálu

Následující ikony signálu platí pro všechny předchozí ikony a označují jejich přístupnost.

|Ikona|Popis|
|----------|-----------------|
|\<> žádná ikona signálu|Veřejné. Přístupné odkudkoli v této součásti a z libovolné součásti, která na něj odkazuje.|
|![Symbol chráněný signálem](../ide/media/vxsignal_icon_key.gif)|Chráněné. Přístupné z obsahující třídy nebo typu, nebo ty, které jsou odvozeny z obsahující třídy nebo typu.|
|![Soukromý symbol signálu](../ide/media/vxsignal_icon_lock.gif)|Soukromé. Přístupné pouze v obsahující třídy nebo typu.|
|![Symbol zapečetěný signálem](../ide/media/vxsignal_icon_envelope.gif)|Uzavřené.|
|![Signál přítel&#47;vnitřní symbol](../ide/media/vxsignal_icon_diamond.gif)|Přítel/Interní. Přístupné pouze z projektu.|
|![Šipka ikony signálu](../ide/media/vxsignal_icon_arrow.gif)|Zástupce. Zástupce objektu.|

> [!NOTE]
> Pokud je projekt součástí databáze správy zdrojového kódu, mohou se zobrazit další ikony signálu, které označují stav správy zdrojového kódu, například vrácení se změnami nebo odhlášení.

## <a name="see-also"></a>Viz také

- [Zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md)
