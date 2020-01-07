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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588392"
---
# <a name="class-view-and-object-browser-icons"></a>Ikony zobrazení tříd a prohlížeče objektů

**Zobrazení tříd** a **Prohlížeč objektů** zobrazují ikony, které reprezentují entity kódu, například obory názvů, třídy, funkce a proměnné. Následující tabulka ukazuje a popisuje ikony.

|Ikona|Popis|Ikona|Popis|
|----------|-----------------|----------|-----------------|
|![Symbol oboru názvů](../ide/media/vxnamespace_icon.gif)|Názvový prostor|![Symbol deklarace](../ide/media/vxmethod_icon.gif)|Metoda nebo funkce|
|![Ikona třídy](../ide/media/vxclass_icon.gif)|Třída|![Symbol operátoru](../ide/media/vxoperator_icon.gif)|Operátor|
|![Symbol rozhraní lupy](../ide/media/vxinterface_icon.gif)|Rozhraní|![Symbol vlastnosti](../ide/media/vxproperty_icon.gif)|Vlastnost|
|![Symbol struktury](../ide/media/vxstruct_icon.gif)|Struktura|![Ikona pole](../ide/media/vxfield_icon.gif)|Pole nebo proměnná|
|![Symbol sjednocení](../ide/media/vxunion_icon.gif)|Unie|![Symbol události](../ide/media/vxevent_icon.gif)|Událost|
|![Symbol výčtu](../ide/media/vxenum_icon.gif)|Výčet|![Ikona konstanty](../ide/media/vxconstant_icon.gif)|Konstanta|
|![Symbol definice typu](../ide/media/vxtypedef_icon.gif)|Definic|![Výčet symbolu položky](../ide/media/vxenumitem_icon.gif)|Položka výčtu|
|![Symbol modulu sady Visual Studio](../ide/media/vxmodule_icon.gif)|– modul|![Symbol položky mapy](../ide/media/vxmapitem_icon.gif)|Položka mapování|
|![Symbol metody rozšíření](../ide/media/extensionmethod.gif)|Metoda rozšíření|![Symbol deklarace](../ide/media/vxmethod_icon.gif)|Externí deklarace|
|![Symbol delegáta](../ide/media/vxdelegate_icon.gif)|Delegát|![Ikona chyby pro Zobrazení tříd a Prohlížeč objektů](../ide/media/erroricon.gif)|Chyba|
|![Symbol výjimky](../ide/media/vxexception_icon.gif)|Výjimka|![Symbol šablony](../ide/media/vxtemplate_icon.gif)|Šablona|
|![Symbol mapy](../ide/media/vxmap_icon.gif)|Mapa|![Chybový symbol pro vykřičník](../ide/media/vxerror_icon.gif)|Neznámé|
|![Symbol předávání typu](../ide/media/ob_type_forward.gif)|Přesměrování typu|||

## <a name="signal-icons"></a>Ikony signálu

Následující ikony signálu se vztahují na všechny předchozí ikony a označují přístupnost.

|Ikona|Popis|
|----------|-----------------|
|\<není ikona signálu >|Republik. Přístupné z libovolného místa v této součásti a ze všech komponent, které na ni odkazují.|
|![Symbol Protected signálu](../ide/media/vxsignal_icon_key.gif)|Proti. Přístupné z obsahující třídy nebo typu nebo z těch, které jsou odvozeny z obsahující třídy nebo typu.|
|![Privátní symbol signálu](../ide/media/vxsignal_icon_lock.gif)|Hlášen. Přístupný pouze v nadřazené třídě nebo typu.|
|![Symbol zapečetěného signálu](../ide/media/vxsignal_icon_envelope.gif)|Sada.|
|![Vnitřní symbol&#47;přítele signálu](../ide/media/vxsignal_icon_diamond.gif)|Přítel/interní. Přístupný pouze z projektu.|
|![Šipka ikony signálu](../ide/media/vxsignal_icon_arrow.gif)|Shortcut. Zástupce objektu.|

> [!NOTE]
> Pokud je váš projekt součástí databáze správy zdrojového kódu, mohou být zobrazeny další ikony signálu, které označují stav správy zdrojového kódu, například vráceno nebo rezervováno.

## <a name="see-also"></a>Viz také:

- [Zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md)
