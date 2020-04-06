---
title: 'Testovací oblast 3: Rezervovat pokladnu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5365da1e342df5aea9c1b1cd2ae5a446baea57f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704609"
---
# <a name="test-area-3-check-outundo-checkout"></a>Testovací oblast 3: Rezervovat/vrátit pokladnu
Tato testovací oblast modulu plug-in pro řízení zdrojového kódu zahrnuje úpravy a vrácení položek z úložiště verzí pomocí příkazů **Rezervovat** a **Vrátit pokladnu.**

**Rezervovat**: Označí položku v úložišti verzí jako rezervovánou, upraví místní kopii tak, aby četla/zapisovala.

**Vrácení pokladny**zpět : Označí položku v úložišti verzí jako vrácenou se změnami, vrátí místní kopii do stavu před odjezdem (v závislosti na možnostech).

## <a name="command-menu-access"></a>Přístup k nabídce příkazů

Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovacích případech.

##### <a name="check-out"></a>Mrkni se:

- **Soubor**, **řízení zdrojového kódu**, **rezervovat**.

- **Soubor**, **rezervovat**.

- Místní nabídka, **Rezervovat**.

- Vrácení pokladny: **Soubor**, **Řízení zdrojového kódu**, Vrácení **pokladny**.

## <a name="common-expected-behavior"></a>Běžné očekávané chování

- Po operaci rezervování jsou cílové soubory nebo složky označeny jako rezervováné v úložišti verzí.

- Úložiště verzí přiřazuje pokladnu správnému uživateli.

- Čas a datum pokladny jsou správné (podle nastavení uživatele).

## <a name="test-cases"></a>Testovací případy

Následují specifické testovací případy pro testovací oblast Pokladna/Vrácení pokladny.

### <a name="case-3a-check-out"></a>Případ 3a: Odjezd

Tato část se zaměřuje na operaci příkazu check-out.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Rezervovat exkluzivní (COE) klientský projekt|1. Vytvořte klientský projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Podívejte se na celý projekt výhradně **(Soubor**, **Rezervovat).**|Check out dochází.|
|Rezervovat výhradní (COE) souborový systém nebo místní webový projekt služby IIS|1. Nastavte připojení webového serveru ke sdílení souborů v **nástrojích**, **možnostech**, **projektech**, **nastavení webu**.<br />2. Vytvořte webový projekt.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Podívejte se na celý projekt výhradně **(Soubor,** **Zdrojové zdroje**, **Rezervovat).**|Check out dochází.|
|Rezervovat položky řešení v řešení (nová metoda pro zpracování jiných souborů)|1. Vytvořte prázdný roztok.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Podívejte se na roztok.<br />4. Přidejte několik položek řešení.<br />5. Zkontrolujte všechny nově přidané položky.<br />6. Vyberte více položek řešení.<br />7. Podívejte se na vybrané položky (Místní nabídka, **Rezervovat).**|Vybrané soubory jsou rezervovány.|
|Rezervovat místní verzi (pokud tuto funkci podporuje plug-in v testu)|1. Uživatel 1: Vytvořte klientský projekt.<br />2. Uživatel 1: Přidejte řešení do správy zdrojového kódu.<br />3. Uživatel 2: Otevřete řešení ze správy zdrojového kódu do jiného umístění.<br />4. Uživatel 2: Podívejte se na soubor.<br />5. Uživatel 2: Upravte soubor.<br />6. Uživatel 2: Změna v souboru.<br />7. Uživatel 1: Podívejte se na místní verzi souboru (Podívejte se na možnost **Rezervovat místní verzi** upřesnit v dialogovém okně **Rezervovat).**|Místní verze souboru je rezervována.<br /><br /> Změny uživatelem 2 nejsou použity pro soubor uživatele 1.|

### <a name="case-3b-disconnected-check-out"></a>Případ 3b: Odpojeno Odhlášení

Provoz v odpojeném režimu umožňuje uživatelům určitou úroveň nepřetržité podpory správy zdrojového kódu, pokud nejsou připojeni přímo k úložišti verzí. To se provádí místním ukládáním do mezipaměti všechny relevantní informace o narukované řešení a projekty.

Výhradní operace rezervování může dojít pouze při připojení k úložišti správy zdrojového kódu. Ke sdíleným operacím rezervování může dojít kdykoli, ať už jsou připojené nebo odpojené. Proto je po odpojení od úložiště verzí povolen pouze příkaz **Rezervovat sdílené** (COS). Při odpojení je **vrácení pokladny** zakázáno, protože starou verzi nelze načíst, aby nahradila změny provedené uživatelem.

Když se uživatel znovu připojí k úložišti verzí, budou synchronizovány stavy pokladny všech zapsaných řešení a projektů. To provede nezbytné aktualizace úložiště pro pokladny, které uživatel provedl. Po synchronizaci došlo k synchronizaci, uživatel je schopen pokračovat v práci jako normální (připojeno).

#### <a name="expected-behavior"></a>Očekávané chování

- Příkaz Rezervovat výhradně nelze **použít,** když je odpojen od úložiště verzí.

- Příkaz **Vrátit pokladnu** nelze použít, když je odpojen od úložiště verzí.

- **Příkaz Sdílené rezervování** funguje.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Při odpojení si vyhledání souboru a připojení k synchronizaci|1. Odpojte řízený projekt pomocí dialogového okna Změnit sřízení zdrojového kódu (**Soubor**, **Řízení zdrojového kódu**, **Změna správy zdrojového kódu).**<br />2. Zkontrolujte soubor.<br />3. V dialogovém okně upozornění klikněte na rezervovat (odpojeno).<br />4. Upravte soubor.<br />5. Připojte se pomocí dialogového okna Změnit směřovat zdrojového kódu.<br />6. Získejte nejnovější verzi upraveného souboru.|Běžné očekávané chování|

### <a name="case-3c-query-editquery-save-qeqs"></a>Případ 3c: Úprava dotazu/uložení dotazu (QEQS)
 Položky pod správou zdrojového kódu jsou sledovány pro úpravy, změny a ukládání, které uživatelům pomáhají snadno spravovat jejich soubory. Při úpravě řízené položky, která je "vrácení se změnami", qeqs zachytí pokus o úpravu a zeptá se uživatele, pokud chce rezervovat soubor pro jeho úpravu. V závislosti na **nástrojích** **, Nastavení možností** je uživatel buď nucen rezervovat soubor, aby mohl upravovat, nebo může mít možnost upravit kopii v paměti a rezervovat později. Pokud je **uživatelské nástroje**, **Možnosti** nastavení není nastavena na zobrazení rezervovat dialogové okno a jen rezervovat, pak jako uživatel dělá jeho úpravy, soubor automaticky rezervuje, kdykoli je to možné.

#### <a name="expected-behavior"></a>Očekávané chování

- Po operaci rezervování jsou cílové soubory nebo složky označeny jako rezervováné v úložišti verzí.

- Úložiště verzí přiřazuje rezervování správnému uživateli.

- Čas a datum odjezdu jsou správné (podle nastavení uživatele).

- Místní kopie cílového souboru nebo složky je zapisovatelná.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Úprava textového souboru se změnami|1. Vytvořte nový projekt obsahující textový soubor.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Nastavení **nástrojů**, **možností**, **správy zdrojového kódu**, **Povolit úpravy souborů, zatímco jen pro čtení na disku** nezaškrtnuté.<br />4. Nastavit **nástroje,** **možnosti,** **řízení zdrojového kódu**, **Výzva k check-out** při **vrácení se změnami soubory jsou upraveny** pole se seznamem.<br />5. Nastavit **nástroje,** **možnosti,** **řízení zdrojového kódu**, **Výzva k check-out** při **vrácení se změnami soubory jsou uloženy** se seznamem pole.<br />6. Otevřete textový soubor v editoru, pokuste se do něj zadat nový text. Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />7. V dialogovém **okně Rezervovat pro úpravy** klepněte na tlačítko **Storno.** Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />8. Nastavení **nástrojů,** **možností**, **správy zdrojového kódu**, **Povolit, aby byly soubory upravovány pouze pro čtení na disku.**<br />9. Otevřete soubor projektu v editoru, pokuste se zadat nový text do souboru. Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />10. V dialogovém okně **Rezervovat pro úpravy** klikněte na **Upravit.** Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />11. Upravte textový soubor a pokuste se jej uložit.|`Result of step 6:`<br /><br /> Zobrazí se dialogové okno Upravit.<br /><br /> `Result of step 7:`<br /><br /> Soubor se nezmění.<br /><br /> `Result of step 9:`<br /><br /> Zobrazí se dialogové okno Upravit.<br /><br /> `Result of step 10:`<br /><br /> Soubor projektu můžete upravit v paměti.<br /><br /> `Result of step 11:`<br /><br /> Při uložení se zobrazí dialogové okno Rezervovat při uložení.|
|Úprava souboru řešení, který je se změnami|Opakujte kroky popsané v předchozím testu, ale místo úpravtextového souboru upravte řešení změnou vlastností řešení.|Stejné jako předchozí test|
|Úprava souboru projektu se změnami|Opakujte kroky popsané v předchozím testu, ale místo úpravtextového souboru upravte projekt změnou vlastností projektu.|Stejné jako předchozí test.|

### <a name="case-3d-silent-check-out"></a>Případ 3d: Tichý check out
 Tato podoblast zahrnuje rozestavení scénářů, kdy se dialogové okno **Rezervovat** nezobrazuje podle **nastavení Nástrojů**, **Možnosti**, **Správa zdrojového kódu**uživatele .

#### <a name="expected-behavior"></a>Očekávané chování

- Po operaci rezervování jsou cílové soubory nebo složky označeny jako rezervováné v úložišti verzí.

- Úložiště verzí přiřazuje rezervování správnému uživateli.

- Čas a datum odjezdu je správné (podle nastavení uživatele).

- Místní kopie cílového souboru nebo složky je zapisovatelná.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Tichý výkaže pro soubor|1. Nastavte **nástroje,** **možnosti,** **řízení zdrojového kódu** na **pokladně soubory automaticky při úpravách**.<br />2. Vytvořte nový projekt se souborem.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Podívejte se na soubor.|Soubor je rezervován tiše (bez ui).|
|Tichá pokladna pro projekt|1. Nastavte **nástroje,** **možnosti,** **řízení zdrojového kódu** na **pokladně soubory automaticky při úpravách**.<br />2. Vytvořte nový projekt.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Podívejte se na projekt.|Soubor je rezervován tiše (bez ui).|

### <a name="case-3e-undo-check-out"></a>Případ 3e: Vrácení odhlášení
 **Vrácení zpět zpět se** používá ke zrušení stavu rezervováného souboru a k zabránění vrácení změn provedených v souboru se změnami.

#### <a name="expected-behavior"></a>Očekávané chování

- Výchozí nastavení je založeno na nastavení místní **verze uživatele.** Pokud se uživatel rozhodl rezervovat místní verzi, pak je výchozí pro vrácení pokladny vždy vrátit k verzi rezervována.

- Po přijetí vrácení se zobrazí ikony v **Průzkumníku řešení** pro ohrožené soubory a položka je odebrána z okna **Čekající vrácení se změnami.**

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Vrácení pokladny jednoho souboru, který je rezervován výhradně|1. Vytvořte klientský projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Podívejte se na soubor výhradně.<br />4. Upravte soubor.<br />5. Vrácení pokladny **(soubor,** **řízení zdrojového kódu**, vrácení **pokladny).**|Společné očekávané chování.|
|Vrácení zrušení vrácení pokladny jednoho souboru, který je rezervován sdílený|1. Vytvořte klientský projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Podívejte se na sdílený soubor.<br />4. Upravte soubor.<br />5. Vrácení pokladny **(soubor,** **řízení zdrojového kódu**, vrácení **pokladny).**|Společné očekávané chování.|
|Vrácení pokladny projektu po přidání souborů do projektu|1. Vytvořte nový projekt a přidejte jej do správy zdrojového kódu.<br />2. Podívejte se na projekt.<br />3. Přidejte soubor do projektu.<br />4. Vrácení pokladny projektu.|Přidaný soubor je odebrán z projektu v Průzkumníku řešení.<br /><br /> Projekt již není rezervován.|
|Vrácení pokladny projektu po odstranění souborů z projektu|1. Vytvořte nový projekt a přidejte jej do správy zdrojového kódu.<br />2. Podívejte se na projekt.<br />3. Odstraňte soubor z projektu.<br />4. Vrácení pokladny projektu.|Odstraněný soubor se zobrazí pod projektem v Průzkumníku řešení.<br /><br /> Projekt již není rezervován.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
