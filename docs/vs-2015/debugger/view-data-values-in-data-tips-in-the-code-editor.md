---
title: Zobrazení hodnot dat v datových tipech v editoru kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: fd2c7bf67b5c2e7f25b4193462883b53cda8db87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700112"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Zobrazení hodnot dat v datových tipech v editoru kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Datové tipy poskytují pohodlný způsob zobrazení informací o proměnných v programu během ladění. Datové tipy pracují pouze v režimu pozastavení a pouze s proměnnými, které jsou v aktuálním oboru provádění.  
  
 V nástroji [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] mohou být datové tipy připnuté na konkrétní umístění ve zdrojovém souboru nebo mohou být plovoucí na všech [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknech.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Zobrazení DataTip (pouze v režimu pozastavení)  
  
1. V okně zdroje umístěte ukazatel myši na libovolnou proměnnou v aktuálním oboru.  
  
    Zobrazí se DataTip.  
  
   > [!NOTE]
   > Tipy k datům jsou vždy vyhodnocovány v kontextu, kde je provádění pozastaveno, a nikoli na místě, kde je umístěn ukazatel myši. Pokud najedete myší na proměnnou v jiné funkci se stejným názvem jako proměnná, která je v aktuálním kontextu, zobrazí se hodnota proměnné ve druhé funkci jako hodnota proměnné v aktuálním kontextu.  
  
2. DataTip zmizí po odebrání ukazatele myši. Pokud chcete DataTip připnout tak, aby zůstaly otevřené, klikněte na ikonu **Připnout na zdroj** nebo  
  
   - Klikněte pravým tlačítkem na proměnnou a pak klikněte na **Připnout na zdroj**.  
  
     Připnutý DataTip se zavře, když relace ladění skončí.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Odepnout DataTip a označit jako plovoucí  
  
- V připnutých DataTip klikněte na ikonu **odepnout ze zdroje** .  
  
     Ikona připnutí se změní na nepřipojenou pozici. DataTip je teď Floaty nad všemi otevřenými okny. Plovoucí DataTip se po ukončení relace ladění ukončí.  
  
### <a name="to-repin-a-floating-datatip"></a>Znovu plovoucí DataTip  
  
- V DataTip klikněte na ikonu připnutí.  
  
     Ikona připnutí se změní na připnuté umístění. Pokud je DataTip mimo okno zdrojového kódu, ikona připnutí je zakázána a DataTip nelze připnout.  
  
### <a name="to-close-a-datatip"></a>Zavření DataTip  
  
- Umístěte ukazatel myši na DataTip a potom klikněte na ikonu **Zavřít** .  
  
### <a name="to-close-all-datatips"></a>Zavření všech tipů  
  
- V nabídce **ladění** klikněte na možnost **Vymazat všechny datové tipy**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Zavření všech datových tipů pro určitý soubor  
  
- V nabídce **ladění** klikněte na **Vymazat všechny tipy připnuté na** *soubor*.  
  
## <a name="expanding-and-editing-information"></a>Rozbalování a úpravy informací  
 Můžete použít datové tipy k rozšíření pole, struktury nebo objektu k zobrazení členů. Můžete také upravit hodnotu proměnné z DataTip.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Chcete-li rozbalit proměnnou a zobrazit její prvky  
  
- V DataTip umístěte ukazatel myši nad **+** znaménko, které se nachází před názvem proměnné.  
  
     Proměnná se rozbalí a zobrazí její prvky ve formě stromu.  
  
     Když je proměnná rozbalená, můžete se přesunout nahoru a dolů pomocí kláves se šipkami na klávesnici. Alternativně můžete použít myš.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Úprava hodnoty proměnné pomocí DataTip  
  
1. V DataTip klikněte na hodnotu. Tato hodnota je zakázána pro hodnoty jen pro čtení.  
  
2. Zadejte novou hodnotu a stiskněte klávesu ENTER.  
  
## <a name="making-a-datatip-transparent"></a>DataTip transparentní  
 Pokud chcete zobrazit kód, který je za DataTip, můžete DataTip dočasně transparentní. To se nevztahuje na datové tipy, které jsou připnuté nebo plovoucí.  
  
#### <a name="to-make-a-datatip-transparent"></a>Nastavení DataTip na průhledný  
  
- V DataTip stiskněte klávesu CTRL.  
  
     DataTip zůstane transparentní, dokud podržíte klávesu CTRL.  
  
## <a name="visualizing-complex-data-types"></a>Vizualizace složitých datových typů  
 Pokud se vedle názvu proměnné v DataTip zobrazuje ikona lupy, je pro proměnné tohoto datového typu k dispozici jeden nebo více typů pro [vytváření vlastních vizualizací](../debugger/create-custom-visualizers-of-data.md) . Můžete použít Vizualizér k zobrazení informací smysluplnější, obvykle grafickým způsobem.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Zobrazení obsahu proměnné pomocí Vizualizér  
  
- Kliknutím na ikonu lupy vyberte výchozí Vizualizér pro datový typ.  
  
     -nebo-  
  
     Klikněte na šipku rozevíracího seznamu vedle Vizualizér a vyberte ze seznamu vhodných vizualizací pro datový typ.  
  
     V Vizualizér se zobrazí informace.  
  
## <a name="adding-information-to-a-watch-window"></a>Přidání informací do okna kukátka  
 Pokud chcete i nadále sledovat proměnnou, můžete přidat proměnnou do okna **kukátka** z DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Přidání proměnné do okno Kukátko  
  
- Klikněte pravým tlačítkem na DataTip a pak klikněte na **Přidat kukátko**.  
  
     Proměnná je přidána do okna **kukátko** . Pokud používáte edici, která podporuje více oken **kukátka** , je proměnná přidána do **kukátka 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Import a export datových tipů  
 Můžete exportovat datové tipy do souboru XML, který lze sdílet s kolegy nebo upravit pomocí textového editoru.  
  
#### <a name="to-export-datatips"></a>Export datových tipů  
  
1. V nabídce Ladění klikněte na **exportovat datové tipy**.  
  
     Zobrazí se dialogové okno **pro export tipů pro** datatext.  
  
2. Pomocí standardních technik souborů přejděte do umístění, kam chcete soubor XML uložit, zadejte název souboru do pole **název souboru** a potom klikněte na **OK**.  
  
#### <a name="to-import-datatips"></a>Import datových tipů  
  
1. V nabídce Ladění klikněte na **Import datových tipů**.  
  
     Zobrazí se dialogové okno **importovat tipy pro** datatexty.  
  
2. Pomocí dialogového okna vyhledejte soubor XML, který chcete otevřít, a klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Postupy: použití dialogového okna QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Vytvořit vlastní vizualizace](../debugger/create-custom-visualizers-of-data.md)   
 [Postupy: Změna číselného formátu oken ladicího programu](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
