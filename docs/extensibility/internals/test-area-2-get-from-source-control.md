---
title: 'Oblasti test 2: Získání od správy zdrojového kódu | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27f2a535b2e08d3632dfd46031823919477fca3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133242"
---
# <a name="test-area-2-get-from-source-control"></a>Oblasti test 2: Získání od správy zdrojového kódu
Tato oblast testovací zahrnuje testovacích případů pro načítání položky z úložiště verzí pomocí příkazu Get. Tyto testovacích případů lze použít pro obě místní a webové projekty.  
  
## <a name="command-menu-access"></a>Příkaz přístup do nabídky  
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovací případy.  
  
##### <a name="get-latest-version"></a>Získáte nejnovější verzi:  
  
-   **Soubor**, **ovládací prvek zdroje**, **získat nejnovější verzi**.  
  
-   **Soubor**, **získat nejnovější verzi**.  
  
-   Místní nabídky, **získat nejnovější verzi**.  
  
-   GET: **soubor**, **ovládací prvek zdroje**, **získat**.  
  
## <a name="expected-behavior"></a>Očekávané chování  
  
##### <a name="get-latest-version"></a>Získáte nejnovější verzi:  
 Provede načtení silent (bez uživatelského rozhraní) nejnovější verze položky z úložiště verzí.  
  
##### <a name="get"></a>Získáte:  
 Zobrazí **získat** dialogové okno a umožňuje uživateli provádět změny do sady souborů, které budou načteny a také změnit možnosti, které ovlivňují, jak jsou načteny soubory.  
  
## <a name="test-cases"></a>Testovací případy  
  
|Akce|Kroky testů|Očekávané výsledky ověření|  
|------------|----------------|--------------------------------|  
|Získat nejnovější verzi souboru, který neexistuje místně|1.  Vytvořte projekt.<br />2.  Přidání položky do projektu.<br />3.  Uveďte projektu ve správě zdrojového kódu.<br />4.  Místní kopie položky odstraňte.<br />5.  Získat nejnovější verzi položky (místní nabídky, **získat nejnovější verzi**).|Soubor položky se načítají místně.|  
|Získá soubor, který neexistuje místně|1.  Vytvořte projekt.<br />2.  Přidání položky do projektu.<br />3.  Uveďte projektu ve správě zdrojového kódu.<br />4.  Místní kopie položky odstraňte.<br />5.  Získejte položku (**soubor**, **správy zdrojového kódu**, **získat** \<položka >).|Soubor položky se načítají místně.|  
|Získá soubor, který je rezervována výhradně a upravit místně|1.  Vytvořte projekt.<br />2.  Přidání položky do projektu.<br />3.  Uveďte projektu ve správě zdrojového kódu.<br />4.  Položka projektu výhradně rezervujte.<br />5.  Upravte místní kopii.<br />6.  Získat nejnovější verzi položky (**soubor**, **získat nejnovější verzi** \<položka >). Pokud tento krok úspěšný, pokračujte dalším krokem.<br />7.  Klikněte na tlačítko **nahradit** tlačítko v dialogu s upozorněním.|**ReResult z kroku 6** `:`<br /><br /> Dialogové okno upozornění označuje, že tento soubor je rezervovaný.<br /><br /> **ReResult z kroku 7:**<br /><br /> Změny místního souboru je nahrazena původní verzi z úložiště verzí.<br /><br /> Soubor je pro čtení a zápis.|  
|Získání a nahraďte soubor, který je rezervována, sdílet a měnit místně|1.  Vytvořte nový projekt.<br />2.  Přidání položky do projektu.<br />3.  Uveďte projektu ve správě zdrojového kódu.<br />4.  Podívejte se na Položka projektu jako sdílený.<br />5.  Upravte místní kopii.<br />6.  Získat nejnovější verzi položky (**soubor**, **získat nejnovější verzi** \<položka >). Pokud tento krok úspěšný, pokračujte dalším krokem.<br />7.  Klikněte na tlačítko **nahradit** v dialogovém okně upozornění.|**Výsledkem krok 6:**<br /><br /> Dialogové okno upozornění označuje, že tento soubor je rezervovaný.<br /><br /> **Výsledkem krok 7:**<br /><br /> Změny místního souboru je nahrazena původní verzi z úložiště verzí.<br /><br /> Soubor je pro čtení a zápis.|  
|Získá soubor, který neexistuje místně, stejné jako nejnovější verzi v úložišti verze|1.  Vytvořte nový projekt.<br />2.  Přidání položky do projektu.<br />3.  Uveďte projektu ve správě zdrojového kódu.<br />4.  Získejte položku (**soubor**, **správy zdrojového kódu**, **získat** \<položka >).|Místní soubor je beze změny.|  
|Získání řešení s projektem jeden|1.  Vytvoření řešení s projektem jeden.<br />2.  Místní řešení ve správě zdrojového kódu.<br />3.  Odstraňte všechny soubory projektu místně.<br />4.  Získání řešení (**soubor**, **správy zdrojového kódu**, **získat**).|Všechny odstraněné soubory jsou obnoveny místně.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)