---
title: Paměť Windows | Dokumentace Microsoftu
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
- vs.debug.memory
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
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 704c0ff20dbd11b4640b2d81670a4cdeaf3f1ea0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724243"
---
# <a name="memory-windows"></a>Okna paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Paměti** okno poskytuje přehled o místo v paměti, který používá vaše aplikace. **Watch** okně **QuickWatch** dialogovém okně **automatické hodnoty** okně a **místní hodnoty** v okně zobrazí obsah proměnné, které jsou uložené na konkrétní umístění v paměti. Ale **paměti** v okně se zobrazí obrázek ve velkém měřítku. Tento náhled může být vhodné pro zkoumání velkých časti dat (vyrovnávací paměti nebo velké řetězce, například), který není zobrazit i v jiných oknech. Ale **paměti** okno není omezena pouze na zobrazení dat. Zobrazí se všechno, co v místo v paměti, zda obsah se data, kód nebo náhodného bits uvolňování paměti v nepřiřazené paměti.  
  
 **Paměti** není k dispozici pouze v případě, že je povoleno ladění úrovni adres v interval **možnosti** dialogovém okně**ladění** uzlu. **Paměti** okno není k dispozici pro skript nebo SQL, které jsou jazyky, které nedokáže rozpoznat koncept paměti.  
  
## <a name="opening-a-memory-window"></a>Otevřete okno paměti  
  
#### <a name="to-open-a-memory-window"></a>Otevře se okno paměti  
  
1.  Spusťte ladění, pokud jste už není v režimu ladění.  
  
2.  V **ladění** nabídky, přejděte k **Windows**. Pak, přejděte na **paměti** a potom klikněte na tlačítko **paměti 1**, **paměti 2**, **paměti 3**, nebo **paměti 4**. (Nižší úrovně edice [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsahovat pouze jeden **paměti** okna. Pokud používáte některou z těchto edicí, stačí kliknout na **paměti**.)  
  
## <a name="paging-in-the-memory-window"></a>Stránkování v paměti okna  
 **Paměti** má okno svislý posuvník, který se ovládá nestandardním způsobem. Adresní prostor moderní počítače je velmi velké a může snadno získat ztratili jste uchopíte jeho thumb posuvník a jeho přetažením do náhodných umístění. Z tohoto důvodu jezdce je "pružinou" a vždy zůstane v centru posuvník. V nativním kódu aplikace můžete stránku nahoru nebo dolů ale nejde o volně přejděte.  
  
 Vyšších adresách paměti se zobrazí v dolní části okna. Zobrazit adresu vyšší, přesuňte se dolů, nikoli nahoru.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Na stránce nahoru nebo dolů v paměti  
  
1.  Na stránce dolů (Přejít na vyšší adresy paměti), klikněte v části jezdce v svislý posuvník.  
  
2.  Na stránce nahoru (Přejít na nižší adresa paměti), klikněte výše thumb svislý posuvník.  
  
## <a name="selecting-a-memory-location"></a>Vyberte umístění v paměti  
 Pokud chcete okamžitě přesunout do vybraného umístění v paměti, můžete tak učinit pomocí operace přetažení myší nebo úpravou hodnoty v **adresu** pole. **Adresu** pole přijímá pouze číselné hodnoty, ale také výrazy, které vedou k adresám. Ve výchozím nastavení **paměti** okno zachází **adresu** výraz jako výraz za provozu, který je již znovu jako váš program se spustí. Živé výrazů může být velmi užitečné. Například můžete je zobrazit paměť, která je přistupovala ukazatel.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Vyberte umístění v paměti přetažením  
  
1.  V libovolném okně vyberte paměti adresa proměnné typu nebo ukazatel, který obsahuje adresu paměti.  
  
2.  Přetáhněte adresu nebo ukazatel **paměti** okna.  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Vyberte umístění v paměti tak, že upravíte  
  
1.  V **paměti** okna, vyberte **adresu** pole.  
  
2.  Zadejte nebo vložte adresu chcete vidět, a potom stiskněte klávesu **ENTER**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Mění způsob informace zobrazí okno paměti  
 Můžete přizpůsobit tak, jak **paměti** okno zobrazuje obsah paměti. Ve výchozím nastavení obsah paměti se zobrazí jako jeden bajtové celá čísla v šestnáctkovém formátu a počet sloupců je automaticky určeno aktuální šířku okna.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Chcete-li změnit formát obsah paměti  
  
1.  Klikněte pravým tlačítkem myši **paměti** okna.  
  
2.  Vyberte formát, který chcete.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Chcete-li změnit počet sloupců v okně paměti  
  
1. Na panelu nástrojů v horní části **paměti** okna, vyhledejte **sloupce** seznamu.  
  
2. V **sloupce** vyberte číslo sloupce, které chcete zobrazit nebo vybrat **automaticky** pro automatickou úpravu na šířku okna.  
  
   Pokud nechcete, aby obsah **paměti** oknu změnit jako váš program spustí, můžete ji vypnout vyhodnocení výrazu za provozu.  
  
#### <a name="to-toggle-live-evaluation"></a>Chcete-li přepnout živé hodnocení  
  
1. Klikněte pravým tlačítkem myši **paměti** okna.  
  
2. V místní nabídce klikněte na tlačítko **automaticky přehodnotit**.  
  
    Pokud se vyžaduje vyhodnocení za provozu na, bude vybrána možnost a kliknutím ji vypne živé hodnocení. Pokud se vyžaduje vyhodnocení za provozu vypnuto, není vybrána možnost a kliknutím zapne živé hodnocení.  
  
   Můžete skrýt nebo zobrazit panel nástrojů v horní části **paměti** okna. Nebudete mít přístup k vyřešení pole nebo jinými nástroji tak dlouho, dokud je skrytý panelu nástrojů.  
  
#### <a name="to-toggle-the-toolbar"></a>Chcete-li přepnout panel nástrojů  
  
1.  Klikněte pravým tlačítkem myši **paměti** okna.  
  
2.  V místní nabídce klikněte na tlačítko **zobrazit panel nástrojů**.  
  
     Panelu nástrojů zobrazí nebo zmizí, v závislosti na jeho předchozího stavu.  
  
## <a name="following-a-pointer-through-memory"></a>Následující ukazatel přes paměti  
 V nativním kódu aplikace můžete použít názvy registrů jako živé výrazy. Například můžete použít ukazatel zásobníku dodržovat zásobníku.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Chcete-li, aby následoval ukazatel přes paměti  
  
1.  V **paměti** okno **adresu** zadejte výraz ukazatele. Proměnné ukazatele musí být v aktuálním oboru. V závislosti na jazyku budete muset přistoupit přes ukazatel.  
  
2.  Stisknutím klávesy **ENTER**.  
  
     Teď, když použijete příkazu ke spuštění jako například **krok**, adresa paměti, který se zobrazí jako ukazatel nezmění automaticky změní.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)





