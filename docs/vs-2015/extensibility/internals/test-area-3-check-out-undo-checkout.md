---
title: 'Testovací oblast 3: Rezervace a zrušení rezervace | Dokumentace Microsoftu'
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
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: adc6a84dbdc4fb182dd589c54527f02a1aa90d99
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722992"
---
# <a name="test-area-3-check-outundo-checkout"></a>Testovací oblast 3: Přečtěte si / zrušit rezervaci
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato oblast testovací modul plug-in správy zdrojového kódu pokrývá úprav a vrací položky z úložiště verzí prostřednictvím **rezervovat** a **vrátit zpět rezervaci** příkazy.  
  
 **Rezervovat**: značky položky v úložišti verzí jako rezervované, upraví místní kopii pro čtení a zápisu.  
  
 **Vrátit zpět rezervaci**: označí položku v úložišti verzí, jak se změnami, vrátí místní kopii do stavu před rezervaci (v závislosti na možnostech).  
  
## <a name="command-menu-access"></a>Přístup do příkazu nabídky  
 Následující [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrované vývojové prostředí nabídky cesty se používají v testovacích procesech.  
  
##### <a name="check-out"></a>Mrkni se:  
  
-   **Soubor**, **správy zdrojového kódu**, **rezervovat**.  
  
-   **Soubor**, **rezervovat**.  
  
-   Místní nabídka **rezervovat**.  
  
-   Zrušení rezervace: **souboru**, **správy zdrojového kódu**, **rezervace**.  
  
## <a name="common-expected-behavior"></a>Běžné očekávané chování  
  
-   Po rezervaci operace jsou cílové soubory nebo složky označena jako kontrolovaná navýšení kapacity v úložišti verzí.  
  
-   Úložiště verzí atributy rezervace pro správné uživatele.  
  
-   Čas a datum rezervaci správnost (podle nastavení uživatele).  
  
## <a name="test-cases"></a>Testovací případy  
 Tady jsou konkrétní testovací případy pro testovací oblast rezervace a zrušení rezervace.  
  
### <a name="case-3a-check-out"></a>Malá a velká 3a: Podívejte se na  
 Tato část se zaměřuje na operaci vrácení se změnami příkazu.  
  
|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Zkontrolujte si výhradní (COE) klientský projekt|1.  Vytvoření projektu klienta.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Projděte si celý projekt výhradně (**souboru**, **rezervovat**).|Podívejte se na vyvolá.|  
|Podívejte se na exkluzivní (COE) systému souborů nebo místní projekt webové služby IIS|1.  Nastavení webového serveru připojení ke sdílené složce v **nástroje**, **možnosti**, **projekty**, **nastavení webu**.<br />2.  Vytvoření webového projektu.<br />3.  Přidáte řešení do správy zdrojového kódu.<br />4.  Projděte si celý projekt výhradně (**souboru**, **správy zdrojových kódů**, **rezervovat**).|Podívejte se na vyvolá.|  
|Podívejte se na položky řešení v řešení (nové metody pro zpracování další soubory)|1.  Vytvořte prázdné řešení.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Podívejte se řešení.<br />4.  Přidejte několik položek řešení.<br />5.  Všechny nově přidané položky se změnami.<br />6.  Vyberte více položek řešení.<br />7.  Projděte si vybrané položky (nabídku, **rezervovat**).|Vybrané soubory jsou rezervovány.|  
|Zkontrolujte si místní verzi (Pokud tuto funkci podporuje modul plug-in v rámci testu)|1.  Uživatel 1: Vytvoření projektu klienta.<br />2.  Uživatel 1: Přidejte řešení do správy zdrojového kódu.<br />3.  Uživatel 2: Otevřete řešení ze správy zdrojového kódu do jiného umístění.<br />4.  Uživatel 2: Projděte si soubor.<br />5.  Uživatel 2: Upravte soubor.<br />6.  Uživatel 2: Kontrola v souboru.<br />7.  Uživatel 1: Podívejte se na místní verzi souboru (zkontrolujte **zkontrolujte si místní verze** rozšířených možností v **rezervovat** dialogové okno).|Místní verzi souboru je rezervován.<br /><br /> Úpravy uživatelem 2 nejsou použity pro uživatele 1 soubor.|  
  
### <a name="case-3b-disconnected-check-out"></a>Malá a velká 3b: odpojení rezervaci  
 V odpojeném režimu umožňuje uživatelům určitou úroveň podporu pokračování zdrojového ovládacího prvku při nejsou připojené přímo k úložišti verzí. To se provádí místně ukládání do mezipaměti všechny relevantní informace o zařazených řešení a projektů.  
  
 Výhradní rezervaci operací může dojít pouze během připojení k úložišti správy zdrojů. Sdílené rezervaci operací může dojít v okamžiku, zda připojení nebo odpojení. Proto pokud připojený k úložišti verzí, pouze **zkontrolujte si sdílené** (COS) je příkaz povolen. Při odpojení, **vrátit zpět rezervaci** je zakázaná, protože nebylo možné načíst předchozí verzi aplikace nahradit změny provedené uživatelem.  
  
 Když uživatel znovu připojí k verzi ukládat, rezervaci stavy všech zařazených řešení a projekty jsou synchronizovány. To udělá za rezervace, které uživatel provedl potřebné aktualizace do úložiště. Po synchronizaci se stalo, uživatel je moct pokračovat v práci jako za normálních okolností (připojené).  
  
#### <a name="expected-behavior"></a>Očekávané chování  
  
-   Nelze použít **zkontrolujte si výhradně** příkaz odpojené od úložiště verzí.  
  
-   Nelze použít **vrátit zpět rezervaci** příkaz odpojené od úložiště verzí.  
  
-   **Sdílené rezervovat** příkaz funguje.  
  
|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Při odpojení, podívejte se na soubor, pak se připojte pro synchronizaci|1.  Odpojit spravovaným projektem pomocí dialogového okna změnit správu zdrojových kódů (**souboru**, **správy zdrojových kódů**, **ivní změnit zdroj ovládání**l).<br />2.  Podívejte se do souboru.<br />3.  Klikněte na rezervaci (odpojeno) v dialogovém okně upozornění.<br />4.  Upravte soubor.<br />5.  Připojte se pomocí dialogového okna změnit správu zdrojových kódů.<br />6.  Získáte nejnovější verzi upravený soubor.|Běžné očekávané chování|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Případ 3c: dotaz upravit a dotaz uložte (QEQS)  
 Položky pod správou zdrojových kódů jsou sledována pro úpravy, změny, a uloží to pomohlo uživatelům snadno spravovat svoje soubory. Při úpravě řízené položku, která je "přihlásila" QEQS zachycuje pokus o úpravu a žádá uživatele, pokud chce rezervovat soubor pro úpravu. V závislosti na **nástroje**, **možnosti** nastavení, uživatel je musí zkontrolovat dolů, aby bylo možné upravit soubor nebo může být povoleno upravit kopii v paměti a prohlédnout později. Pokud uživatele **nástroje**, **možnosti** není nastavení k zobrazení rezervaci dialogové okno a jednoduše zaškrtněte ji a potom jako uživatel učiní jeho úprav, soubor automaticky rezervuje, kdykoli je to možné.  
  
#### <a name="expected-behavior"></a>Očekávané chování  
  
-   Po rezervaci operace jsou cílové soubory nebo složky označena jako kontrolovaná navýšení kapacity v úložišti verzí.  
  
-   Úložiště verzí atributy rezervaci pro správné uživatele.  
  
-   Čas a datum rezervaci správnost (podle nastavení uživatele).  
  
-   Místní kopie na cílový soubor nebo složku je zapisovatelný.  
  
|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Upravte textový soubor, který je vrácen se změnami|1.  Vytvořte nový projekt obsahující textový soubor.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Nastavte **nástroje**, **možnosti**, **správy zdrojových kódů**, **povolit vrácení souborů se upravovat za běhu na disku jen pro čtení** na nezaškrtnuté.<br />4.  Nastavte **nástroje**, **možnosti**, **správy zdrojových kódů**, **výzvy k registraci** v **při kontrole soubory jsou upravené** – pole se seznamem.<br />5.  Nastavte **nástroje**, **možnosti**, **správy zdrojových kódů**, **výzvy k registraci** v **při kontrolejsouuloženysoubory** – pole se seznamem.<br />6.  Otevřete textový soubor v editoru, pokus zadat nový text do souboru. Pokud tento krok úspěšný, pokračujte dalším krokem.<br />7.  Klikněte na tlačítko **zrušit** v **rezervovat pro úpravy** dialogové okno. Pokud tento krok úspěšný, pokračujte dalším krokem.<br />8.  Nastavte **nástroje**, **možnosti**, **správy zdrojových kódů**, **povolit vrácení souborů se upravovat za běhu na disku jen pro čtení** na zaškrtnuté.<br />9. Otevřete soubor projektu v editoru, pokus zadat nový text v souboru. Pokud tento krok úspěšný, pokračujte dalším krokem.<br />10. Klikněte na tlačítko **upravit** v **rezervovat pro úpravy** dialogové okno. Pokud tento krok úspěšný, pokračujte dalším krokem.<br />11. Upravte textový soubor a pokusí se ho uložte.|`Result of step 6:`<br /><br /> Podívejte se pro dialogové okno Upravit.<br /><br /> `Result of step 7:`<br /><br /> Soubor je beze změny.<br /><br /> `Result of step 9:`<br /><br /> Podívejte se pro dialogové okno Upravit.<br /><br /> `Result of step 10:`<br /><br /> Můžete upravit soubor projektu v paměti.<br /><br /> `Result of step 11:`<br /><br /> Uložit, prohlédněte si na Uložit dialogové okno zobrazí.|  
|Upravit soubor řešení, která je vrácena se změnami|Opakujte kroky, jak je popsáno v předchozí test, ale místo úpravy textového souboru, upravte řešení tak, že změna vlastností řešení.|Stejné jako předchozí test|  
|Upravit soubor projektu, která je vrácena se změnami|Opakujte kroky, jak je popsáno v předchozím testu, ale místo úpravy textového souboru, upravte projekt tak, že změna vlastností projektu.|Stejné jako předchozí test.|  
  
### <a name="case-3d-silent-check-out"></a>Malá a velká 3d: Tiché podívejte se na  
 Tato kontrola zahrnuje podoblasti scénáře kde **rezervovat** dialogové okno nezobrazí za uživatele **nástroje**, **možnosti**, **nastavení správy zdrojového kódu** .  
  
#### <a name="expected-behavior"></a>Očekávané chování  
  
-   Po rezervaci operace jsou cílové soubory nebo složky označena jako kontrolovaná navýšení kapacity v úložišti verzí.  
  
-   Úložiště verzí atributy rezervaci pro správné uživatele.  
  
-   Čas a datum rezervaci je správný (podle nastavení uživatele).  
  
-   Místní kopie na cílový soubor nebo složku je zapisovatelný.  
  
|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Bezobslužné ověření souboru|1.  Nastavte **nástroje**, **možnosti**, **správy zdrojových kódů** k **checkout soubory automaticky na Upravit**.<br />2.  Vytvoření nového projektu se souborem.<br />3.  Přidáte řešení do správy zdrojového kódu.<br />4.  Rezervujte soubor.|Soubor je rezervován tiše (bez uživatelského rozhraní).|  
|Tiché rezervace projektu|1.  Nastavte **nástroje**, **možnosti**, **správy zdrojových kódů** k **checkout soubory automaticky na Upravit**.<br />2.  Vytvořte nový projekt.<br />3.  Přidáte řešení do správy zdrojového kódu.<br />4.  Podívejte se projektu.|Soubor je rezervován tiše (bez uživatelského rozhraní).|  
  
### <a name="case-3e-undo-check-out"></a>Malá a velká 3e: vrátit zpět rezervaci  
 **Vrátit zpět rezervaci** slouží ke zrušení soubor rezervován stav a vyhněte se vracení změny provedené v souboru.  
  
#### <a name="expected-behavior"></a>Očekávané chování  
  
-   Výchozí hodnota je založena na uživatele **podívejte se na místní verze** nastavení. Pokud uživatel se rozhodl rezervovat místní verze, je výchozí nastavení pro zrušení rezervace se vždycky vrátit k verzi rezervován.  
  
-   Po přijetí zpět na ikony v **Průzkumníka řešení** jsou aktualizované pro vliv na soubory a položka se odebere z **čekající vrácení se změnami** okna.  
  
|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Vrátit zpět rezervaci jeden soubor, který je zaregistrovány exkluzivně|1.  Vytvoření projektu klienta.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Soubor rezervujete exkluzivně.<br />4.  Upravte soubor.<br />5.  Vrátit zpět rezervaci (**souboru**, **správy zdrojového kódu**, **rezervace**).|Běžné očekávané chování.|  
|Vrátit zpět rezervaci jeden soubor, který je rezervován Shared|1.  Vytvoření projektu klienta.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Projděte si soubor sdílený.<br />4.  Upravte soubor.<br />5.  Vrátit zpět rezervaci (**souboru**, **správy zdrojového kódu**, **rezervace**).|Běžné očekávané chování.|  
|Rezervace projektu po přidání souborů do projektu|1.  Vytvořte nový projekt a přidat do správy zdrojového kódu.<br />2.  Podívejte se projektu.<br />3.  Přidejte soubor do projektu.<br />4.  Rezervace projektu.|Přidaný soubor se odebere z projektu v Průzkumníku řešení.<br /><br /> Projekt je již rezervován.|  
|Rezervace projektu po odstranění soubory z projektu|1.  Vytvořte nový projekt a přidat do správy zdrojového kódu.<br />2.  Podívejte se projektu.<br />3.  Odstranění souboru z projektu.<br />4.  Rezervace projektu.|Odstraněný soubor se zobrazí v rámci projektu v Průzkumníku řešení.<br /><br /> Projekt je již rezervován.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

