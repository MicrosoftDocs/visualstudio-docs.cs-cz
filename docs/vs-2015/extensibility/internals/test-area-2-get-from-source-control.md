---
title: 'Testovací oblast 2: Získání ze správy zdrojových kódů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96b00cfc9965b6006fa51b3cd313566658d604bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786155"
---
# <a name="test-area-2-get-from-source-control"></a>Testovací oblast 2: Načtení ze správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tento test oblast obsahuje informace o testovacích případů pro načítání položek ze úložiště verzí pomocí příkazu Get. Tyto testovací případy můžete použít pro oba místní a pro webové projekty.  
  
## <a name="command-menu-access"></a>Přístup do příkazu nabídky  
 Následující [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí nabídky cesty se používají v testovacích procesech.  
  
##### <a name="get-latest-version"></a>Načíst nejnovější verzi:  
  
-   **Soubor**, **správy zdrojového kódu**, **načíst nejnovější verzi**.  
  
-   **Soubor**, **načíst nejnovější verzi**.  
  
-   Místní nabídka **získat nejnovější verzi**.  
  
-   GET: **souboru**, **správy zdrojového kódu**, **získat**.  
  
## <a name="expected-behavior"></a>Očekávané chování  
  
##### <a name="get-latest-version"></a>Načíst nejnovější verzi:  
 Provede tichý režim (žádné uživatelské rozhraní) načtení nejnovější verze položky z úložiště verzí.  
  
##### <a name="get"></a>Získáte:  
 Zobrazí **získat** dialogové okno a umožňuje uživatelům provádět změny do sady souborů, který načte se také upravit možnosti, které ovlivňují, jak jsou soubory načteny.  
  
## <a name="test-cases"></a>Testovací případy  
  
|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Načíst nejnovější verzi souboru, který neexistuje lokálně|1.  Vytvoření projektu.<br />2.  Přidání položky do projektu.<br />3.  Umístěte projekt pod správou zdrojových kódů.<br />4.  Odstraňte místní kopii položky.<br />5.  Načíst nejnovější verzi položky (nabídku, **získat nejnovější verzi**).|Soubor položky se načte místně.|  
|Načtení souboru, která místně neexistuje|1.  Vytvoření projektu.<br />2.  Přidání položky do projektu.<br />3.  Umístěte projekt pod správou zdrojových kódů.<br />4.  Odstraňte místní kopii položky.<br />5.  Získat položku (**souboru**, **správy zdrojových kódů**, **získat** \<položka >).|Soubor položky se načte místně.|  
|Získat soubor, který byl exkluzivně rezervován a upravena místně|1.  Vytvoření projektu.<br />2.  Přidání položky do projektu.<br />3.  Umístěte projekt pod správou zdrojových kódů.<br />4.  Položka projektu rezervujte exkluzivně.<br />5.  Upravte místní kopii.<br />6.  Načíst nejnovější verzi položky (**souboru**, **získat nejnovější verzi** \<položka >). Pokud tento krok úspěšný, pokračujte dalším krokem.<br />7.  Klikněte na tlačítko **nahradit** tlačítko v dialogu s upozorněním.|**ReResult z kroku 6** `:`<br /><br /> Dialogové okno upozornění označuje, že je soubor rezervován.<br /><br /> **ReResult z kroku 7:**<br /><br /> Změny místního souboru se nahradí původní verzi z úložiště verzí.<br /><br /> Soubor je pro čtení a zápisu.|  
|Získání a nahraďte soubor, který je rezervován, sdílet a upravena místně|1.  Vytvořte nový projekt.<br />2.  Přidání položky do projektu.<br />3.  Umístěte projekt pod správou zdrojových kódů.<br />4.  Projděte si položku projektu jako sdílené.<br />5.  Upravte místní kopii.<br />6.  Načíst nejnovější verzi položky (**souboru**, **získat nejnovější verzi** \<položka >). Pokud tento krok úspěšný, pokračujte dalším krokem.<br />7.  Klikněte na tlačítko **nahradit** v dialogu s upozorněním.|**Výsledkem krok 6:**<br /><br /> Dialogové okno upozornění označuje, že je soubor rezervován.<br /><br /> **Výsledkem krok 7:**<br /><br /> Změny místního souboru se nahradí původní verzi z úložiště verzí.<br /><br /> Soubor je pro čtení a zápisu.|  
|Získat soubor, který neexistuje lokálně, stejné jako v úložišti verzí nejnovější verze|1.  Vytvořte nový projekt.<br />2.  Přidání položky do projektu.<br />3.  Umístěte projekt pod správou zdrojových kódů.<br />4.  Získat položku (**souboru**, **správy zdrojových kódů**, **získat** \<položka >).|Místní soubor je beze změny.|  
|Získejte řešení pomocí jednoho projektu|1.  Vytvořte řešení pomocí jednoho projektu.<br />2.  Toto řešení pod správou zdrojových kódů.<br />3.  Odstraňte všechny soubory projektu místně.<br />4.  Získání řešení (**souboru**, **správy zdrojových kódů**, **získat**).|Místně obnovení všech odstraněných souborů.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

