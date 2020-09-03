---
title: Ikony Zobrazení tříd a Prohlížeč objektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e67763234ff7b3778cccabaed45fbbc0bc04d30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620485"
---
# <a name="class-view-and-object-browser-icons"></a>Ikony zobrazení třídy a prohlížeče objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení tříd * * a **Prohlížeč objektů** zobrazí ikony, které reprezentují entity kódu, například obory názvů, třídy, funkce a proměnné. Následující tabulka ukazuje a popisuje ikony.

|Ikona|Popis|Ikona|Popis|
|----------|-----------------|----------|-----------------|
|![Symbol oboru názvů](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Obor názvů|![Symbol deklarace](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Metoda nebo funkce|
|![Ikona třídy](../ide/media/vxclass-icon.gif "vxClass_Icon")|Třída|![Symbol operátoru](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|Operátor|
|![Symbol rozhraní lupy](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Rozhraní|![Symbol vlastnosti](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Vlastnost|
|![Symbol struktury](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Struktura|![Ikona pole](../ide/media/vxfield-icon.gif "vxField_Icon")|Pole nebo proměnná|
|![Symbol sjednocení](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Sjednocení|![Symbol události](../ide/media/vxevent-icon.gif "vxEvent_Icon")|Událost|
|![Symbol výčtu](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Výčet|![Ikona konstanty](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Konstanta|
|![Symbol definice typu](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|Definic|![Výčet symbolu položky](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Položka výčtu|
|![Symbol modulu sady Visual Studio](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Modul|![Symbol položky mapy](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Položka mapování|
|![Symbol metody rozšíření](../ide/media/extensionmethod.gif "ExtensionMethod")|Metoda rozšíření|![Symbol deklarace](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Externí deklarace|
|![Symbol delegáta](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|Delegát|![Ikona chyby pro Zobrazení tříd a Prohlížeč objektů](../ide/media/erroricon.gif "ErrorIcon")|Chyba|
|![Symbol výjimky](../ide/media/vxexception-icon.gif "vxException_Icon")|Výjimka|![Symbol šablony](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Šablona|
|![Symbol mapy](../ide/media/vxmap-icon.gif "vxMap_Icon")|Mapa|![Chybový symbol pro vykřičník](../ide/media/vxerror-icon.gif "vxError_Icon")|Neznámý|
|![Symbol předávání typu](../ide/media/ob-type-forward.gif "ob_type_forward")|Přesměrování typu|||

## <a name="signal-icons"></a>Ikony signálu
 Následující ikony signálu se vztahují na všechny předchozí ikony a označují přístupnost.

> [!NOTE]
> Pokud je váš projekt součástí databáze správy zdrojového kódu, mohou být zobrazeny další ikony signálu, které označují stav správy zdrojového kódu, například vráceno nebo rezervováno.

|Ikona|Popis|
|----------|-----------------|
|\<No Signal Icon>|Republik. Přístupné z libovolného místa v této součásti a ze všech komponent, které na ni odkazují.|
|![Symbol Protected signálu](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Proti. Přístupné z obsahující třídy nebo typu nebo z těch, které jsou odvozeny z obsahující třídy nebo typu.|
|![Privátní symbol signálu](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Hlášen. Přístupný pouze v nadřazené třídě nebo typu.|
|![Symbol zapečetěného signálu](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Sada.|
|![Přítel&#47;interní symbol signálu](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Přítel/interní. Přístupný pouze z projektu.|
|![Šipka ikony signálu](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Shortcut. Zástupce objektu.|

## <a name="see-also"></a>Viz také
 [Zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md)
