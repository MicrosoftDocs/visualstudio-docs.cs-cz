---
title: 'Testovací oblast 3: rezervace vrácení se změnami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab4389c936b71ba8ccbb21b22d0a5e533282026d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155992"
---
# <a name="test-area-3-check-outundo-checkout"></a>Testovací oblast 3: rezervace/zrušení rezervace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato testovací oblast modulu plug-in zdrojového ovládacího prvku pokrývá **Úpravy a vrácení** položek z úložiště verzí prostřednictvím příkazů rezervace a **zrušení rezervace** .  
  
 **Rezervovat**: označí položku v úložišti verzí jako zarezervovánou, upraví místní kopii na čtení a zápis.  
  
 **Zrušit rezervaci**: označí položku v úložišti verzí jako vrácenou, vrátí místní kopii do stavu před rezervaci (v závislosti na možnostech).  
  
## <a name="command-menu-access"></a>Přístup k nabídce příkazů  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]V testovacích případech se používají následující cesty nabídky integrovaného vývojového prostředí.  
  
##### <a name="check-out"></a>Mrkni se:  
  
- **Soubor**, **Správa zdrojového kódu**, **rezervace**.  
  
- **Soubor**, **Podívejte**se.  
  
- Místní nabídka se **rezervuje**.  
  
- Zrušit rezervaci: **soubor**, Správa **zdrojového kódu**, **Zrušit rezervaci**.  
  
## <a name="common-expected-behavior"></a>Obvyklé očekávané chování  
  
- Po dokončení operace rezervace jsou cílové soubory a složky označeny jako rezervované v obchodě s verzemi.  
  
- V úložišti verzí se zarezervuje na správného uživatele.  
  
- Čas a datum rezervace jsou správné (podle nastavení uživatele).  
  
## <a name="test-cases"></a>Testovací případy  
 Níže jsou uvedené konkrétní testovací případy pro testovací oblast rezervace nebo zrušení rezervace.  
  
### <a name="case-3a-check-out"></a>Případ 3a: rezervace  
 Tato část se zaměřuje na fungování příkazu k rezervaci.  
  
|Akce|Testovací kroky|Očekávané výsledky k ověření|  
|------------|----------------|--------------------------------|  
|Rezervovat exkluzivní (COE) projekt klienta|1. Vytvořte projekt klienta.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Prohlédněte si výhradně celý projekt (**soubor**, **rezervuje**).|K rezervaci dojde.|  
|Rezervovat exkluzivně (COE) systém souborů nebo místní webový projekt služby IIS|1. Nastavte připojení webového serveru ke sdílené složce v **nabídce nástroje**, **Možnosti**, **projekty**a **Nastavení webu**.<br />2. Vytvořte webový projekt.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Prohlédněte si výhradně celý projekt (**soubor**, Správa **zdrojového kódu**, **rezervace**).|K rezervaci dojde.|  
|Rezervovat položky řešení v řešení (nová metoda pro zpracování jiných souborů)|1. Vytvořte prázdné řešení.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Podívejte se na řešení.<br />4. Přidejte několik položek řešení.<br />5. proveďte kontrolu všech nově přidaných položek.<br />6. Vyberte více položek řešení.<br />7. Podívejte se na vybrané položky (místní nabídka, **rezervuje**).|Vybrané soubory jsou rezervovány.|  
|Rezervovat místní verzi (Pokud modul plug-in v rámci testu tuto funkci podporuje)|1. uživatel 1: Vytvořte projekt klienta.<br />2. uživatel 1: přidejte řešení do správy zdrojového kódu.<br />3. uživatel 2: Otevřete řešení ze správy zdrojového kódu do jiného umístění.<br />4. uživatel 2: Podívejte se na soubor.<br />5. uživatel 2: Upravte soubor.<br />6. uživatel 2: vrácení souboru se změnami.<br />7. uživatel 1: Podívejte se na místní verzi tohoto souboru (v dialogovém okně **rezervovat** zaškrtněte možnost Upřesnit **místní verzi** ).|Místní verze souboru je rezervovaná.<br /><br /> Změny podle uživatele 2 nejsou aplikovány na soubor uživatele 1.|  
  
### <a name="case-3b-disconnected-check-out"></a>Případ 3B: odpojená rezervace  
 Provoz v odpojeném režimu umožňuje uživatelům určitou úroveň pokračující podpory správy zdrojového kódu, když není připojená přímo k úložišti verzí. K tomu je potřeba ukládat do mezipaměti všechny relevantní informace o zařazení řešení a projektů.  
  
 Exkluzivní operace rezervace mohou nastat pouze při připojení k úložišti správy zdrojů. Sdílené operace rezervace můžou být kdykoli k dispozici, ať už připojené, nebo odpojené. Proto je po odpojení od úložiště verzí povolen pouze příkaz pro **rezervaci sdíleného** (cos). Během odpojení je **zrušení rezervace** zakázané, protože se nepovedlo načíst starou verzi, aby se nahradily změny provedené uživatelem.  
  
 Když se uživatel znovu připojí k úložišti verzí, budou synchronizovány stavy rezervace všech zařazených řešení a projektů. V tomto případě jsou nezbytné aktualizace Storu pro rezervace, které uživatel provedl. Po dokončení synchronizace bude uživatel moci pokračovat v práci jako normální (připojeno).  
  
#### <a name="expected-behavior"></a>Očekávané chování  
  
- Příkaz k **rezervaci exkluzivně** nejde použít při odpojení od úložiště verzí.  
  
- Příkaz pro **zrušení rezervace** nelze použít při odpojení od úložiště verzí.  
  
- **Sdílený** příkaz pro rezervaci funguje.  
  
|Akce|Testovací kroky|Očekávané výsledky k ověření|  
|------------|----------------|--------------------------------|  
|Když je odpojený, podívejte se na soubor a pak se připojte k synchronizaci.|1. Odpojte řízený projekt pomocí dialogového okna změnit správu zdrojového kódu (**soubor**, Správa **zdrojového kódu**, **změňte zdroj Contro**l).<br />2. soubor rezervovat.<br />3. v dialogovém okně upozornění klikněte na rezervovat (odpojeno).<br />4. Upravte soubor.<br />5. Připojte se pomocí dialogového okna změnit správu zdrojového kódu.<br />6. Stáhněte si nejnovější verzi upravovaného souboru.|Obvyklé očekávané chování|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Případ 3C: dotaz Edit/Query Save (QEQS)  
 Položky pod správou zdrojových kódů jsou sledovány pro úpravy, změny a uložení, které uživatelům umožňují snadnou správu svých souborů. Když se upraví kontrolovaná položka, která je vrácená se změnami, QEQS zachytí pokusy o úpravu a požádá uživatele, pokud chce soubor rezervovat. V závislosti na **nástrojích**nastavení **možností** je uživatel buď nuceně soubor rezervovat, aby mohl upravit nebo Povolit úpravu kopie v paměti a vrátit se změnami později. Pokud se v dialogovém okně pro **uživatele, nastavení** **Možnosti** nezobrazuje dialogové okno rezervovat a stačí ho zkontrolovat, pak se soubor automaticky rezervuje, kdykoli je to možné.  
  
#### <a name="expected-behavior"></a>Očekávané chování  
  
- Po dokončení operace rezervace jsou cílové soubory a složky označeny jako rezervované v obchodě s verzemi.  
  
- Atributy úložiště verze se rezervují pro správného uživatele.  
  
- Čas a datum rezervace jsou správné (podle nastavení uživatele).  
  
- Místní kopie cílového souboru nebo složky je zapisovatelná.  
  
|Akce|Testovací kroky|Očekávané výsledky k ověření|  
|------------|----------------|--------------------------------|  
|Upravit textový soubor, který je vrácen se změnami|1. Vytvořte nový projekt obsahující textový soubor.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Nastavte **nástroje**, **Možnosti**, Správa **zdrojového kódu**a **povolte úpravy souborů, když se na disku jen pro čtení** nekontrolují.<br />4. Nastavte **nástroje**, **Možnosti**, Správa **zdrojového kódu**a **vyzvat k rezervaci** v poli se seznamem **při kontrole souborů zaškrtnutoy** .<br />5. Nastavte **nástroje**, **Možnosti**, **Správa zdrojového kódu**, dotázat se na **rezervaci** v poli se seznamem **při uložení souborů se změnami** .<br />6. Otevřete textový soubor v editoru a pokuste se zadat nový text do souboru. V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />7. v dialogovém okně **rezervovat pro úpravy** klikněte na **Zrušit** . V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />8. nastavení **nástrojů**, **možností**, **správy zdrojů**, **povolených úprav souborů na disku jen pro čtení na** kontrolovaném disku.<br />9. Otevřete soubor projektu v editoru a pokuste se zadat nový text v souboru. V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />10. v dialogovém okně **rezervovat pro úpravy** klikněte na **Upravit** . V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />11. upravte textový soubor a pokuste se ho uložit.|`Result of step 6:`<br /><br /> Zobrazí se dialogové okno rezervovat pro úpravy.<br /><br /> `Result of step 7:`<br /><br /> Soubor je beze změny.<br /><br /> `Result of step 9:`<br /><br /> Zobrazí se dialogové okno rezervovat pro úpravy.<br /><br /> `Result of step 10:`<br /><br /> Soubor projektu můžete upravit v paměti.<br /><br /> `Result of step 11:`<br /><br /> Při uložení se zobrazí dialogové okno rezervovat při uložení.|  
|Upravit soubor řešení, který je vrácen se změnami|Opakujte kroky popsané v předchozím testu, ale místo úprav textového souboru upravte řešení změnou vlastností řešení.|Stejné jako předchozí test|  
|Upravit soubor projektu, který je vrácen se změnami|Opakujte kroky popsané v předchozím testu, ale místo úprav textového souboru upravte projekt změnou vlastností projektu.|Stejné jako předchozí test.|  
  
### <a name="case-3d-silent-check-out"></a>Případ 3D: tichá rezervace  
 Tato podoblast pokrývá scénáře, ve kterých se dialogové okno **rezervace** nezobrazí pro jednotlivé **nástroje**uživatele, **Možnosti**, **Nastavení správy zdrojového kódu**.  
  
#### <a name="expected-behavior"></a>Očekávané chování  
  
- Po dokončení operace rezervace jsou cílové soubory a složky označeny jako rezervované v obchodě s verzemi.  
  
- Atributy úložiště verze se rezervují pro správného uživatele.  
  
- Čas a datum rezervace jsou správné (podle nastavení uživatele).  
  
- Místní kopie cílového souboru nebo složky je zapisovatelná.  
  
|Akce|Testovací kroky|Očekávané výsledky k ověření|  
|------------|----------------|--------------------------------|  
|Bezobslužná rezervace souboru|1. Nastavte **nástroje**, **Možnosti**, **správu zdrojového kódu** na soubory, které se budou **automaticky rezervovat při úpravách**.<br />2. Vytvořte nový projekt se souborem.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Prohlédněte si soubor.|Soubor je rezervován v tichém režimu (bez uživatelského rozhraní).|  
|Tichá rezervace pro projekt|1. Nastavte **nástroje**, **Možnosti**, **správu zdrojového kódu** na soubory, které se budou **automaticky rezervovat při úpravách**.<br />2. Vytvořte nový projekt.<br />3. Přidejte řešení do správy zdrojového kódu.<br />4. Prohlédněte si projekt.|Soubor je rezervován v tichém režimu (bez uživatelského rozhraní).|  
  
### <a name="case-3e-undo-check-out"></a>Případ 3e: zrušit rezervaci  
 **Zrušení rezervace se používá** ke zrušení stavu rezervace souboru a k tomu, abyste se vyhnuli vrácení změn provedených v souboru.  
  
#### <a name="expected-behavior"></a>Očekávané chování  
  
- Výchozí hodnota je založená na nastavení **místní verze rezervace** uživatele. Pokud se uživatel rozhodl zaregistrovat místní verzi, pak výchozí nastavení pro vrácení zpět se vždy vrátí k rezervované verzi.  
  
- Po přijetí akce zpět budou ikony v **Průzkumník řešení** aktualizovány pro ovlivněné soubory a položka bude odebrána z okna čeká se na **vrácení se změnami** .  
  
|Akce|Testovací kroky|Očekávané výsledky k ověření|  
|------------|----------------|--------------------------------|  
|Zrušení rezervace samostatného souboru, který je rezervován exkluzivně|1. Vytvořte projekt klienta.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Prohlédněte si soubor exkluzivně.<br />4. Upravte soubor.<br />5. zrušení rezervace (**soubor**, Správa **zdrojového kódu**, **zrušení rezervace**).|Obvyklé očekávané chování.|  
|Zrušení rezervace jednoho souboru, který je rezervován jako sdílený|1. Vytvořte projekt klienta.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Podívejte se na sdílený soubor.<br />4. Upravte soubor.<br />5. zrušení rezervace (**soubor**, Správa **zdrojového kódu**, **zrušení rezervace**).|Obvyklé očekávané chování.|  
|Zrušit rezervaci projektu po přidání souborů do projektu|1. Vytvořte nový projekt a přidejte ho do správy zdrojového kódu.<br />2. Prohlédněte si projekt.<br />3. Přidejte soubor do projektu.<br />4. zrušte rezervaci projektu.|Přidaný soubor se odebere z projektu v Průzkumník řešení.<br /><br /> Projekt již není rezervován.|  
|Zrušit rezervaci projektu po odstranění souborů z projektu|1. Vytvořte nový projekt a přidejte ho do správy zdrojového kódu.<br />2. Prohlédněte si projekt.<br />3. Odstraňte soubor z projektu.<br />4. zrušte rezervaci projektu.|Odstraněný soubor se zobrazí pod projektem v Průzkumník řešení.<br /><br /> Projekt již není rezervován.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
