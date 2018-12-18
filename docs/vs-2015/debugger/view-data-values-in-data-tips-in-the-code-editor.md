---
title: Zobrazení hodnot dat v datových tipech v editoru kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37fc58a68f8cf482ac6a2bbab3ecb47c28d60904
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799441"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Zobrazení hodnot dat v datových tipech v editoru kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataTips poskytují pohodlný způsob, jak zobrazit informace o proměnných ve svém programu během ladění. DataTips fungovat pouze v režimu pozastavení a pouze s proměnnými, které jsou v aktuálním oboru spuštění.  
  
 V [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], může být DataTips připojené do určitého umístění ve zdrojovém souboru nebo mohou být plovoucí nad všechny [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] systému windows.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>K zobrazení datového tipu (pouze v režimu přerušení)  
  
1. V okně zdroje umístěte ukazatel myši nad všechny proměnné v aktuálním oboru.  
  
    Zobrazí se DataTip.  
  
   > [!NOTE]
   >  Datových tipech jsou vždy vyhodnoceny v kontextu, kde je spuštění pozastaveno, a ne je ukazatel myši. Pokud je ukazatel myši nad proměnnou v jiné funkce se stejným názvem jako proměnná, která je v aktuálním kontextu, zobrazí se jako hodnotu proměnné v aktuálním kontextu hodnotu proměnné v jiné funkci.  
  
2. DataTip zmizí při odebrání ukazatel myši. Pro Připnutí DataTip tak, aby zůstane otevřený, klikněte na tlačítko **připojit ke zdroji** ikonu, nebo  
  
   - Klikněte pravým tlačítkem na proměnnou a pak klikněte na **připojit ke zdroji**.  
  
     Připnuté DataTip ukončí po ukončení relace ladění.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Odepnout DataTip a usnadnit float  
  
-   V připojených DataTip, klikněte **Odepnout ze zdroje** ikonu.  
  
     Ikona Připnutí změní nepřipnuté pozici. DataTip nyní čísel s plovoucí čárkou nad všechna otevřená okna. S plovoucí desetinnou čárkou DataTip ukončí po ukončení relace ladění.  
  
### <a name="to-repin-a-floating-datatip"></a>Chcete-li repin DataTip s plovoucí desetinnou čárkou  
  
-   V datovém tipu klikněte na ikonu připínáčku.  
  
     Ikona Připnutí změní na připojený pozice. Pokud DataTip je mimo okno zdroje, je zakázán ikonu připínáčku a DataTip nedá připnout.  
  
### <a name="to-close-a-datatip"></a>Zavřete DataTip  
  
-   Umístěte ukazatel myši nad DataTip a potom klikněte na tlačítko **Zavřít** ikonu.  
  
### <a name="to-close-all-datatips"></a>Zavřete všechny DataTips  
  
-   Na **ladění** nabídky, klikněte na tlačítko **vymazat všechny DataTips**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Zavřete všechny DataTips pro konkrétní soubor  
  
-   Na **ladění** nabídky, klikněte na tlačítko **vymazat všechny DataTips připojené k** *souboru*.  
  
## <a name="expanding-and-editing-information"></a>Rozbalení a informace pro úpravy  
 Používání tipů DataTips rozbalte pole, struktury nebo objektu pro zobrazení členů. Můžete také upravit hodnotu proměnné z DataTip.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Chcete-li rozbalit proměnnou zobrazíte jeho prvky  
  
-   V datovém tipu, umístěte ukazatel myši nad **+** znak, který předchází název proměnné.  
  
     Proměnná se rozbalí a zobrazí jeho prvky ve formě stromu.  
  
     Při rozbalení proměnné můžete použít klávesy se šipkami na klávesnici přesunout nahoru a dolů. Alternativně můžete pomocí myši.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Chcete-li upravit hodnoty proměnné pomocí DataTip  
  
1.  V datovém tipu klikněte na hodnotu. Tato možnost je zakázána pro hodnoty jen pro čtení.  
  
2.  Zadejte novou hodnotu a stiskněte klávesu ENTER.  
  
## <a name="making-a-datatip-transparent"></a>Změna průhledný DataTip  
 Pokud chcete zobrazit kód, který je za DataTip, lze provádět DataTip dočasně transparentní. To se nevztahuje na datových tipech, které jsou připojené nebo s plovoucí desetinnou čárkou.  
  
#### <a name="to-make-a-datatip-transparent"></a>Chcete-li DataTip transparentní  
  
-   V datovém tipu stiskněte klávesu CTRL.  
  
     Za předpokladu, podržte stisknutou klávesu CTRL, zůstanou DataTip transparentní.  
  
## <a name="visualizing-complex-data-types"></a>Vizualizace komplexních datových typů  
 Pokud se zobrazí s ikonou lupy vedle názvu proměnné v DataTip, jeden nebo více [vytvořit vlastní Vizualizéry](../debugger/create-custom-visualizers-of-data.md) jsou k dispozici pro tento datový typ proměnné. Vizualizéru můžete použít k zobrazení informací lépe vystihuje, obvykle grafické způsobem.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Chcete-li zobrazit obsah proměnné pomocí vizualizéru  
  
-   Klikněte na ikonu lupy, chcete-li vybrat výchozí vizualizér pro datový typ.  
  
     -nebo-  
  
     Klikněte na rozbalovací šipku vedle vizualizéru vyberte ze seznamu odpovídající vizualizéry datového typu.  
  
     Vizualizéru se zobrazí informace.  
  
## <a name="adding-information-to-a-watch-window"></a>Přidání informací do okna kukátka  
 Pokud chcete pokračovat a sledujte proměnné, můžete přidat proměnnou **Watch** okna z DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>K přidání proměnné okno kukátka  
  
-   Klikněte pravým tlačítkem na DataTip a potom klikněte na tlačítko **Přidat kukátko**.  
  
     Proměnná se přidá do **Watch** okna. Pokud používáte edici, která podporuje více **Watch** windows, proměnné se přidá do **kukátko 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Import a export DataTips  
 Exportovat DataTips do souboru XML, který je možné sdílet s kolegy nebo upravovat pomocí textového editoru.  
  
#### <a name="to-export-datatips"></a>Chcete-li exportovat DataTips  
  
1.  V nabídce ladit, klikněte na tlačítko **exportovat DataTips**.  
  
     **Exportovat DataTips** zobrazí se dialogové okno.  
  
2.  Pomocí standardních souborových postupů, přejděte do umístění, kam chcete uložit soubor XML, zadejte název souboru v **název_souboru** pole a potom klikněte na tlačítko **OK**.  
  
#### <a name="to-import-datatips"></a>Chcete-li importovat datové tipy  
  
1.  V nabídce ladit, klikněte na tlačítko **importovat DataTips**.  
  
     **Importovat DataTips** zobrazí se dialogové okno.  
  
2.  Pomocí dialogového okna Najít soubor XML, který chcete otevřít a klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Postupy: použití dialogového okna QuickWatch](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Vytváření vlastních Vizualizérů](../debugger/create-custom-visualizers-of-data.md)   
 [Postupy: Změna numerického formátu ladicí program Windows](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)



