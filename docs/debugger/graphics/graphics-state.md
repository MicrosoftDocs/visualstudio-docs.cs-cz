---
title: Stav grafiky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b45e5d922a5f2ed5a2ba15086c708c734d25e95
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476377"
---
# <a name="graphics-state"></a>Stav grafiky
Okno stavu v sadě Visual Studio grafiky diagnostiky vám pomůže pochopit stav grafiky, která je aktivní v okamžiku aktuální událost, jako je například volání kreslení.  
  
## <a name="understanding-the-state-window"></a>Principy okno stavu  
 Okno Stav shromažďuje společně stavu, který ovlivňuje vykreslování a uvede jej hierarchicky, na jednom místě. V závislosti na verzi Direct3D – vaše aplikace používá, informace uvedené v okně stavu může mít rozdíly.  
  
### <a name="state-views"></a>Zobrazení stavů  
 Tabulka stavu můžete zobrazit několika různými způsoby:  
  
|Zobrazit|Popis|  
|----------|-----------------|  
|Zobrazení stavu vstupní rozhraní API|Toto zobrazení uvede se stavem v podobné rozložení pro Direct3D – objekty, které tvoří stav.|  
|Logický vstupní stav zobrazení|Toto zobrazení uvádí stav v logickém zobrazení, který není zrcadlení rozložení Direct3D – objekty, které tvoří stav.|  
|Připnuté zobrazení stavu|Zobrazení stavu Pinned místo hierarchie, uvede definovaného stavu položky jako plochý seznam s plně kvalifikované názvy. Toto zobrazení díky je možné zobrazit mnoho položek stavu z jiné sady stavu v malý počet řádků.|  
  
##### <a name="to-change-the-state-view"></a>Chcete-li změnit zobrazení stavu  
  
-   V okně stavu v horní levé pod záhlaví vyberte tlačítko, která odpovídá styl zobrazení stavu, který chcete použít.  
  
    -   **Nastaví zobrazení vstupní stav rozhraní API**  
  
    -   **Nastaví zobrazení logického stavu**  
  
    -   **Nastaví zobrazení stavu Pinned**  
  
> [!IMPORTANT]
>  Připnete musí stav v **zobrazit API vstupní stav** nebo **zobrazit logického stavu** ji zobrazit v zobrazení **zobrazit připnutý zobrazení stavu**.  
  
### <a name="state-table-format"></a>Formát stavu tabulky  
 Okno stavu uvede několik sloupců s informacemi.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|Název|Název položky stavu. Pokud tuto položku představuje sadu, stavu, lze rozšířit položky můžete ho zobrazit.<br /><br /> V **rozhraní API vstupní zobrazení stavu** a **logického stavu zobrazení** stavy, názvy odsazeny zobrazíte hierarchický vztah mezi stavy.<br /><br /> V **připnutý zobrazení stavu** stavu plně kvalifikované názvy se zobrazí jako plochý seznam.|  
|Hodnota|Hodnota položky stavu.|  
|Typ|Typ položky stavu.|  
  
### <a name="changed-state"></a>Změněné stavu  
 Stav grafiky obvykle přírůstkové změny mezi následné kreslení volání a různé druhy vykreslování problémy jsou situace, kdy se stav se změní nesprávně. A pomůže vám zjistit, které stav se změnil od předchozího kreslení volání, je stav, který se změnil označené hvězdičkou a zobrazí červeně – to platí nejen sám stát, ale její nadřazená položka stavu taky tak, aby snadno všimnete změněné stavu na nejvyšší úrovně a poté procházení k podrobnostem.  
  
### <a name="pinning-state"></a>Připnutí stavu  
 Protože mnoho aplikací vykreslení podobné objekty postupně, změny se známou sadou stavu, je někdy užitečné pro Připnutí změny stavů v místě, aby mohli sledovat jeho změny v průběhu přesunout z volání kreslení k vykreslení volání.  
  
 To může být užitečné, pokud jste izolované zdroj problému být z důvodu změn v určitém stavu.  
  
##### <a name="to-pin-state-in-place"></a>Chcete-li připnout stavu na místě  
  
1.  V okně stavu vyhledejte stavu, která vás zajímá. Můžete chtít rozbalte vyšší úrovně stavu najít podrobnosti, které vás zajímají.  
  
2.  Umístěte ukazatel myši stavu, která vás zajímá. Ikona PIN kódu se zobrazí vlevo položky stavu.  
  
3.  Zvolte ikonu Pin připnete položka stavu na místě.