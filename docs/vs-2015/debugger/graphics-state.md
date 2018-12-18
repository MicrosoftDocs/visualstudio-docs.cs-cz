---
title: Stav grafiky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5100f32a7a706f0d61e3b0ac006c8168e1ee553
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750373"
---
# <a name="graphics-state"></a>Stav grafiky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno stavu ve Visual Studio graphics Diagnostics vám pomůže pochopit stav grafiky, která je aktivní v okamžiku aktuální události, jako je například volání draw.  
  
## <a name="understanding-the-state-window"></a>Principy okno stavu  
 Okno stavu shromažďuje společně stavu, který má vliv na vykreslování a prezentuje hierarchicky, na jednom místě. V závislosti na verzi rozhraní Direct3D vaše aplikace používá, informace uvedené v okně Stav může mít rozdíly.  
  
### <a name="state-views"></a>Zobrazení stavů  
 Tabulka stavu můžete zobrazit několika různými způsoby:  
  
|Zobrazit|Popis|  
|----------|-----------------|  
|Zobrazit vstupní stav rozhraní API|Toto zobrazení uvádí stav v rozložení na objekty Direct3D, které tvoří stavu.|  
|Logický vstupní stav zobrazení|Toto zobrazení uvádí stav v logickém zobrazení, která není zrcadlení rozložení objekty Direct3D, které tvoří stavu.|  
|Připnout stav zobrazení|Místo hierarchii zobrazení stavu Pinned nabídne stav Připnutí položek jako plochý seznam plně kvalifikovaných názvů. Toto zobrazení umožňuje je možné zobrazit mnoho položek stavu z různých sad stavu v malý počet řádků.|  
  
##### <a name="to-change-the-state-view"></a>Chcete-li změnit zobrazení stavu  
  
-   V okně stavu, v horním levém pod záhlaví klikněte na tlačítko, který odpovídá stylu zobrazení stavu, který chcete použít.  
  
    -   **Zobrazit vstupní stav rozhraní API**  
  
    -   **Zobrazit logického stavu zobrazení**  
  
    -   **Zobrazit stav Pinned**  
  
> [!IMPORTANT]
>  Musí připnout stav v **API zobrazit vstupní stav** nebo **zobrazit logického stavu** zobrazení, který se má zobrazit **zobrazit připnuté zobrazení stavu**.  
  
### <a name="state-table-format"></a>Formát stavu tabulky  
 Okno stavu představuje několik sloupců s informacemi.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|Název|Název položky stavu. Pokud se tato položka představuje sadu stavu, je možné rozšířit položky zobrazení.<br /><br /> V **API vstupní zobrazení stavu** a **logického stavu zobrazení** stavy, názvy odsazeny zobrazíte hierarchický vztah mezi stavy.<br /><br /> V **připnuté zobrazení stavu** stavu, plně kvalifikovaných názvů se zobrazí jako plochý seznam.|  
|Hodnota|Hodnota položky stavu.|  
|Typ|Typ položky stavu.|  
  
### <a name="changed-state"></a>Změna stavu  
 Stav grafiky obvykle přírůstkové změny mezi voláními výkresu následné a různé druhy problémů s vykreslováním jsou způsobeny, když se stav změní nesprávně. Můžete najít v jakém stavu se od předchozího volání kreslení změnila, stavu, která se změnila s hvězdičkou a zobrazí červeně – to platí nejen stav samotný, ale jeho nadřazenou položku stavu, takže můžete snadno Přímá změna stavu na nejvyšší úroveň a pak procházení k podrobnostem.  
  
### <a name="pinning-state"></a>Stav Připnutí  
 Protože velký počet aplikací vykreslení podobné objekty postupně, změna známé sady stavu, je někdy užitečné pro Připnutí Změna stavů v místě, tak, aby mohli sledovat, jak mění při přesunu z volání draw, chcete-li nakreslit volání.  
  
 To může být užitečné, pokud jste izolovali příčiny problému bude z důvodu změn v určitém stavu.  
  
##### <a name="to-pin-state-in-place"></a>Pokud chcete připnout stav na místě  
  
1.  V okně stavu vyhledejte stav, který vás zajímá. Budete muset rozbalit vyšší úrovně stavu k nalezení podrobností, které vás zajímají.  
  
2.  Umístěte kurzor do stavu, který vás zajímá. Nalevo od položky, stav se zobrazí ikona připnout.  
  
3.  Vyberte ikonu připínáčku připněte položky stavu na místě.



