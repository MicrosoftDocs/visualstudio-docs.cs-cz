---
title: Stav grafiky | Microsoft Docs
description: Řešení problémů s vykreslováním zobrazením stavu grafiky pro každé volání remízy. Části stavu, které byly změněny z předchozího volání, jsou zvýrazněny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c6f909d7e250be193bb446d25cd4182d4f062ebe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888599"
---
# <a name="graphics-state"></a>Stav grafiky
Okno stav v nástroji Diagnostika grafiky sady Visual Studio pomáhá pochopit stav grafiky, která je aktivní v době aktuální události, jako je například volání metody Draw.

## <a name="understanding-the-state-window"></a>Principy okna stav
 Okno stav shromažďuje dohromady stav, který ovlivňuje vykreslování a prezentuje jej hierarchicky na jednom místě. V závislosti na verzi rozhraní Direct3D, kterou vaše aplikace používá, můžou mít informace zobrazené v okně stav nějaké rozdíly.

### <a name="state-views"></a>Zobrazení stavu
 Tabulku stavů můžete zobrazit několika různými způsoby:

|Zobrazení|Description|
|----------|-----------------|
|Zobrazení stavu vstupu rozhraní API|Toto zobrazení prezentuje stav v podobném rozložení pro objekty Direct3D, které tvoří stav.|
|Zobrazení stavu logického vstupu|Toto zobrazení prezentuje stav v logickém zobrazení, které nezrcadlí rozložení objektů Direct3D, které tvoří stav.|
|Připnuté zobrazení stavu|Místo hierarchie se zobrazuje připnuté stavové položky v nestrukturovaném seznamu s plně kvalifikovanými názvy. Toto zobrazení umožňuje zobrazit mnoho položek stavu z různých sad stavu v malém počtu řádků.|

##### <a name="to-change-the-state-view"></a>Změna zobrazení stavu

- V okně stav v levém horním rohu přímo pod záhlavím vyberte tlačítko, které odpovídá stylu zobrazení stavu, který chcete použít.

  - **Zobrazit vstupní stav rozhraní API**

  - **Zobrazit zobrazení logického stavu**

  - **Zobrazit připnuté zobrazení stavu**

> [!IMPORTANT]
> Musíte připnout stav do **vstupního stavu rozhraní API pro zobrazení** nebo **Zobrazit zobrazení logických stavů** , které se zobrazí v **zobrazení zobrazit připnutý stav**.

### <a name="state-table-format"></a>Formát stavové tabulky
 Stavové okno prezentuje několik sloupců informací.

|Sloupec|Popis|
|------------|-----------------|
|Název|Název položky stavu. Pokud tato položka představuje sadu stavů, lze položku Rozbalit a zobrazit ji.<br /><br /> V **zobrazení stav vstupu rozhraní API** a stavy **zobrazení logický stav** se názvy odsadí, aby se zobrazil hierarchický vztah mezi stavy.<br /><br /> V **připojeném stavu zobrazení stav** jsou plně kvalifikované názvy zobrazeny v nestrukturovaném seznamu.|
|Hodnota|Hodnota položky stavu.|
|Typ|Typ položky stavu.|

### <a name="changed-state"></a>Změněný stav
 Stav grafiky se obvykle mění postupně mezi následnými voláními vykreslování a mnoho druhů potíží s vykreslováním je způsobeno chybnou změnou stavu. Abychom vám pomohli najít, který stav se od předchozího volání draw změnil, je stav, který se změnil, označený hvězdičkou a zobrazený červeně – to platí nejen pro samotný stav, ale také pro svůj nadřazený stavovou položku, takže můžete snadno přejít na nejvyšší úroveň a pak přejít k podrobnostem.

### <a name="pinning-state"></a>Stav připnutí
 Vzhledem k tomu, že mnoho aplikací vykresluje podobné objekty postupně a mění známou stav, je někdy užitečné připnout změny stavů, abyste mohli sledovat, jak se změní při přesunu z volání remízy na volání metody Draw.

 To může být užitečné také v případě, že jste se zdrojem problému v důsledku změny v určitém stavu nastavili.

##### <a name="to-pin-state-in-place"></a>Připnutí stavu na místo

1. V okně stav Najděte stav, který vás zajímá. Možná budete muset rozbalit stav vyšší úrovně a vyhledat si podrobnosti, které vás zajímají.

2. Umístěte ukazatel na stav, který vás zajímá. Ikona připnutí se zobrazí nalevo od položky stav.

3. Vyberte ikonu připnutí pro připnutí položky stavu na místě.
