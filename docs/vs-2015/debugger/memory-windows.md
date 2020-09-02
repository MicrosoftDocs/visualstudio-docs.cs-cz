---
title: Paměťová okna | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: e60f9b3c9acf1377139fee27486bb10251d8804a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158472"
---
# <a name="memory-windows"></a>Okna paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **paměť** poskytuje zobrazení do paměťového prostoru používaného vaší aplikací. Okno **kukátka** , dialogové okno **QuickWatch** , okno **Automatické** hodnoty a **místní** hodnoty zobrazují obsah proměnných uložených v určitých umístěních v paměti. Ale v okně **paměť** se zobrazuje velký obrázek. Toto zobrazení může být pohodlné pro zkoumání velkých částí dat (například vyrovnávacích pamětí nebo velkých řetězců), které se v ostatních oknech nezobrazují správně. Okno **paměti** však není omezeno na zobrazení dat. Zobrazuje vše v paměťovém prostoru, bez ohledu na to, zda se jedná o data, kód nebo náhodné bity paměti v nepřiřazené paměti.  
  
 Okno **paměť** je dostupné pouze v případě, že je povoleno ladění na úrovni adresy v dialogovém okně **Možnosti** , uzel**ladění** . Okno **paměti** není k dispozici pro skript nebo SQL, což jsou jazyky, které nerozpoznají koncept paměti.  
  
## <a name="opening-a-memory-window"></a>Otevření okna paměti  
  
#### <a name="to-open-a-memory-window"></a>Otevření okna paměti  
  
1. Spusťte ladění, pokud ještě nejste v režimu ladění.  
  
2. V nabídce **ladění** přejděte na příkaz **Windows**. Pak přejděte na **paměť** a pak klikněte na **paměť 1**, **paměť 2**, **paměť 3**nebo **paměť 4**. (Edice nižší úrovně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mají pouze jedno okno **paměti** . Pokud používáte některou z těchto edicí, stačí kliknout na **paměť**.)  
  
## <a name="paging-in-the-memory-window"></a>Stránkování v okně paměti  
 Okno **paměti** má svislý posuvník, který pracuje nestandardním způsobem. Adresní prostor moderního počítače je velmi velký a můžete se snadno ztratit tím, že převedete jezdce posuvníku a přetáhnete ho do náhodného umístění. Z tohoto důvodu je jezdec "zavedený" pružinou "a vždy zůstává ve středu posuvníku. V aplikacích s nativním kódem můžete stránku nahoru nebo dolů, ale nemůžete se pohybovat volně.  
  
 V dolní části okna se zobrazí vyšší adresy paměti. Pokud chcete zobrazit vyšší adresu, posuňte se dolů, ne.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Pro stránku nahoru nebo dolů v paměti  
  
1. Chcete-li přejít o stránku dolů (přesunout na vyšší adresu paměti), klikněte pod jezdcem svislého posuvníku na šipku.  
  
2. Chcete-li stránku nahoru (přesunout na nižší adresu paměti), klikněte nad jezdcem svislého posuvníku.  
  
## <a name="selecting-a-memory-location"></a>Výběr umístění v paměti  
 Pokud chcete okamžitě přejít na vybrané umístění v paměti, můžete to udělat pomocí operace přetažení nebo úpravou hodnoty v poli **adresa** . Pole **adresa** akceptuje nejen číselné hodnoty, ale také výrazy, které se vyhodnotí jako adresy. Ve výchozím nastavení okno **paměti** považuje výraz **adresy** za živý výraz, který je znovu vyhodnocen při provádění programu. Živé výrazy můžou být velmi užitečné. Můžete je například použít k zobrazení paměti, která je dotykem ukazatele.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Výběr umístění v paměti přetažením  
  
1. V jakémkoli okně vyberte adresu paměti nebo proměnnou ukazatele, která obsahuje adresu paměti.  
  
2. Přetáhněte adresu nebo ukazatel na okno **paměti** .  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Výběr umístění paměti úpravou  
  
1. V okně **paměť** vyberte pole **adresa** .  
  
2. Zadejte nebo vložte adresu, kterou chcete zobrazit, a potom stiskněte klávesu **ENTER**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Změna způsobu, jakým okno paměti zobrazuje informace  
 Můžete upravit způsob, jakým okno **paměti** zobrazuje obsah paměti. Ve výchozím nastavení se obsah paměti zobrazuje jako celá čísla typu Byte v šestnáctkovém formátu a počet sloupců je automaticky určen aktuální šířkou okna.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Změna formátu obsahu paměti  
  
1. Klikněte pravým tlačítkem myši na okno **paměti** .  
  
2. Vyberte formát, který chcete.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Změna počtu sloupců v okně paměti  
  
1. Na panelu nástrojů v horní části okna **paměti** Najděte seznam **sloupce** .  
  
2. V seznamu **sloupce** vyberte počet sloupců, které chcete zobrazit, nebo vyberte možnost **automaticky** pro automatické úpravy, která se přizpůsobí šířce okna.  
  
   Pokud nechcete, aby se obsah okna **paměti** měnil při provádění programu, můžete vyhodnotit Live Expression reevaluation.  
  
#### <a name="to-toggle-live-evaluation"></a>Přepnutí na živé vyhodnocení  
  
1. Klikněte pravým tlačítkem myši na okno **paměti** .  
  
2. V místní nabídce klikněte na znovu **vyhodnotit automaticky**.  
  
    Pokud je zapnuté živé vyhodnocení, možnost se vybere a kliknutím na toto se vyhodnotí živé vyhodnocení. Pokud je živé vyhodnocení vypnuto, možnost není vybraná a kliknutím na toto tlačítko se zapne pro živé vyhodnocení.  
  
   Panel nástrojů můžete skrýt nebo zobrazit v horní části okna **paměti** . Nebudete mít přístup k poli adresa nebo k jiným nástrojům, pokud je panel nástrojů skrytý.  
  
#### <a name="to-toggle-the-toolbar"></a>Přepnutí panelu nástrojů  
  
1. Klikněte pravým tlačítkem myši na okno **paměti** .  
  
2. V místní nabídce klikněte na tlačítko **Zobrazit panel nástrojů**.  
  
     Panel nástrojů se zobrazí nebo zmizí v závislosti na předchozím stavu.  
  
## <a name="following-a-pointer-through-memory"></a>Po ukazateli paměti  
 V aplikacích s nativním kódem můžete použít názvy registru jako živé výrazy. Například můžete použít ukazatel zásobníku a postupovat podle zásobníku.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Postup při sledování paměti pomocí ukazatele  
  
1. Do pole **adresa** v okně **paměti** zadejte výraz ukazatele. Proměnná ukazatele musí být v aktuálním oboru. V závislosti na jazyku bude pravděpodobně nutné na něj odkázat.  
  
2. Stiskněte klávesu **ENTER**.  
  
     Když teď použijete příkaz pro spuštění, například **Krok**, adresa paměti, která se zobrazí, se automaticky změní, protože se změní ukazatel.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
