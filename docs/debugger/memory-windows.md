---
title: Zobrazení paměti pro proměnné v ladicím programu | Dokumentace Microsoftu
ms.custom: H1Hack27Feb2017
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdf8e5fc5ee0ac34b4c295f6cc593e0a93b548ae
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257261"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Použití okna paměť v ladicím programu sady Visual Studio (C#, C++, Visual Basic, F#)

Během ladění, **paměti** okno zobrazuje paměťový prostor, vaše aplikace používá. 

Ladicí program systému windows jako **Watch**, **automatické hodnoty**, **místní hodnoty**a **QuickWatch** dialogového okna se zobrazí, proměnné, které se ukládají na konkrétní umístění v paměti. **Paměti** v okně se zobrazí celkový obrázek. Zobrazení paměti je vhodné pro zkoumání velkých časti dat (vyrovnávací paměti nebo velké řetězce, například), které nechcete zobrazit i v jiných oknech. 

**Paměti** okno se neomezuje na zobrazení dat. Všechno, co zobrazí v paměti, včetně dat, kód a náhodné bits uvolňování paměti v nepřiřazené paměti.  

**Paměti** okno není k dispozici pro skript nebo ladění SQL. Tyto jazyky není povědomý koncept paměti.  
  
## <a name="open-a-memory-window"></a>Otevřete okno paměti  
  
Ostatní okna ladicího programu, jako jsou **paměti** windows jsou k dispozici pouze během relace ladění. 

>[!IMPORTANT]
>Povolit **paměti** windows, **povolit ladění na úrovni adres** musí být vybraný v **nástroje** > **možnosti** (nebo **Ladění** > **možnosti**) > **ladění** > **Obecné**. 

**Otevře se okno paměti**
  
1. Ujistěte se, že **povolit ladění na úrovni adres** výběru v **nástroje** > **možnosti** (nebo **ladění**  >  **Možnosti**) > **ladění** > **Obecné**. 
   
1. Spuštění ladění tak, že vyberete na zelenou šipku klávesy **F5**, nebo výběrem **ladění** > **spustit ladění**.  
   
2. V části **ladění** > **Windows** > **paměti**vyberte **paměti 1**, **paměti 2**, **Paměti 3**, nebo **paměti 4**. (Některých edicích systémů [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nabízejí pouze jeden **paměti** okna.)  

## <a name="move-around-in-the-memory-window"></a>Pohyb v okně paměti  

Je velký adresní prostor počítače a kde můžete snadno ztratit posouváním v **paměti** okna. 

Vyšších adresách paměti se zobrazí v dolní části okna. Zobrazit adresu vyšší, přesuňte se dolů. Chcete-li zobrazit adresu nižší posuňte nahoru.  

Můžete okamžitě přejít na uvedené adrese v **paměti** okna pomocí přetahování myší, nebo zadáním adresy v **adresu** pole. **Adresu** pole přijímá alfanumerické adresy a výrazy, které vedou na adresy, jako například `e.User.NonroamableId`. 

Chcete vynutit okamžitou opakované vyhodnocení výrazu v **adresu** vyberte zaoblení šipku **automaticky přehodnotit** ikonu. 

Ve výchozím nastavení **paměti** okno zpracovává **adresu** výrazů jako živé výrazy, které jsou znovu zhodnotí jako spuštění aplikace. Živé výrazů může hodit, například chcete-li zobrazit paměť, která je přistupovala proměnné ukazatele.  

**Pokud chcete pomocí přetažení přetažení přesunout do umístění v paměti:**  
   
1. V jakékoli okno ladicího programu vyberte adresu paměti nebo proměnné ukazatele, který obsahuje adresu paměti.  
   
2. Přetažení adresu nebo ukazatel **paměti** okna. Tuto adresu se pak objeví v **adresu** pole a **paměti** přizpůsobí zobrazení, které řeší v horní části okna. 
  
**Chcete-li přesunout do umístění v paměti tak, že ho zadáte do pole adresy:**
  
- Zadejte nebo vložte adresu nebo výrazu v **adresu** pole a stiskněte klávesu **Enter**, nebo vyberte z rozevíracího seznamu v **adresu** pole. **Paměti** přizpůsobí zobrazení, které řeší v horní části okna.
  
## <a name="customize-the-memory-window"></a>Přizpůsobení okna paměť 

Ve výchozím nastavení obsah paměti se zobrazí jako celá čísla 1 bajt v šestnáctkovém formátu a šířku okna určuje počet sloupců, které jsou zobrazeny. Můžete přizpůsobit tak, jak **paměti** okno zobrazuje obsah paměti.  
  
**Chcete-li změnit formát obsah paměti:**  
  
-  Klikněte pravým tlačítkem **paměti** okna a zvolte formáty, které chcete v místní nabídce.  
  
**Chcete-li změnit počet sloupců v okně paměti:**
  
- Vyberte šipku rozevíracího seznamu vedle položky **sloupce** pole a vyberte číslo sloupce, které chcete zobrazit, nebo vyberte **automaticky** pro automatickou úpravu založené na šířku okna.  
  
Pokud nechcete, aby obsah **paměti** oknu změnit vaše aplikace běží, můžete ji vypnout vyhodnocení výrazu za provozu. 

**Chcete-li přepnout živé vyhodnocení:**  
  
- Klikněte pravým tlačítkem **paměti** okna a vyberte **automaticky přehodnotit** v místní nabídce. 

  >[!NOTE]
  >Live výraz hodnocení je přepínací tlačítko a je ve výchozím, proto výběr **automaticky přehodnotit** ji vypne. Výběr **automaticky přehodnotit** znovu ho znovu zapne. 
  
Můžete skrýt nebo zobrazit panel nástrojů v horní části **paměti** okna. Nebudete mít přístup k **adresu** pole nebo jiné nástroje, když je skrytý panelu nástrojů.  
  
**Chcete-li přepnout zobrazení na panelu nástrojů:**  
  
- Klikněte pravým tlačítkem **paměti** okna a vyberte **zobrazit panel nástrojů** v místní nabídce. Panelu nástrojů zobrazí nebo zmizí, v závislosti na jeho předchozího stavu.  
  
## <a name="follow-a-pointer-through-memory"></a>Aby následoval ukazatel přes paměti  

V aplikacích s nativní kód můžete použít názvy registrů jako živé výrazy. Například můžete použít ukazatel zásobníku dodržovat zásobníku.  
  
**Chcete-li, aby následoval ukazatel přes paměti:**
  
1. V **paměti** okno **adresu** zadejte výraz ukazatele, který je v aktuálním oboru. V závislosti na jazyku budete muset přistoupit přes ukazatel.  
  
2. Stisknutím klávesy **zadejte**.  
   
   Při použití příkazu ladění, jako **krok**, adresa paměti, které jsou zobrazeny v **adresu** pole a v horní části **paměti** okno se automaticky změní jako ukazatel změny.  
  
## <a name="see-also"></a>Viz také:  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)