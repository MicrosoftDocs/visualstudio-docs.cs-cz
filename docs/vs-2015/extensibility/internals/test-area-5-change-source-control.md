---
title: 'Testovací oblast 5: Změna správy zdrojového kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d79281e2fef6a7ae77a2ba6c8375f47dc6520b3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155966"
---
# <a name="test-area-5-change-source-control"></a>Testovací oblast 5: Změna správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato testovací oblast modulu plug-in zdrojového ovládacího prvku pokrývá změnu správy zdrojového kódu prostřednictvím příkazu **změnit správu zdrojového kódu** .  
  
 Příkaz **změnit správu zdrojového kódu** poskytuje pro uživatele čtyři základní funkce:  
  
- **Zapisovat**  
  
   Umožňuje uživateli vytvořit nebo obnovit odkaz správy zdrojového kódu mezi řešení/projekt a úložištěm verzí.  
  
- **Vyjmout**  
  
   Odebere projekt nebo řešení ze správy zdrojového kódu na základě připojení.  
  
- **Připojit/odpojit:**  
  
  Přepne připojený nebo offline stav kontrolovaného řešení, který je popsaný v oblasti 3. Další informace naleznete v části [testovací oblast 3: rezervování/zrušení rezervace](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Přístup k nabídce příkazů  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]V testovacích případech se používá následující cesta nabídky integrovaného vývojového prostředí.  
  
 Změnit správu zdrojového kódu:**soubor**, Správa **zdrojového kódu**, **změnit správu zdrojového kódu**.  
  
## <a name="test-cases"></a>Testovací případy  
 Níže jsou uvedené konkrétní testovací případy pro testovací oblast příkazu **změnit správu zdrojového kódu** .  
  
### <a name="case-5a-bind"></a>Případ 5a: vazba  
 BIND umožňuje uživateli přidat informace o řízení zdrojového kódu do vybraných projektů a řešení. Uživatel je obvykle vyzván k identifikaci projektu ve správě zdrojového kódu, do kterého mají být přidány. Uživatel nemůže v rámci této operace vytvořit nový projekt ve správě zdrojového kódu (na rozdíl od přidání do správy zdrojového kódu).  
  
|Akce|Testovací kroky|Očekávané výsledky k ověření|  
|------------|----------------|--------------------------------|  
|Vytvořit vazby k prázdnému umístění|1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Otevřete dialogové okno **změnit správu zdrojového** kódu (**soubor**, Správa **zdrojového kódu**, **změnit správu zdrojového kódu**).<br />4. klikněte na zrušit **vazbu**.<br />5. Pokud se zobrazí dialogové okno s upozorněním, potvrďte ho.<br />6. Vyberte možnost všechny položky.<br />7. klikněte na **BIND**.<br />8. Přejděte do prázdného umístění v úložišti správy zdrojů.<br />9. Kliknutím na tlačítko **OK** zavřete dialogové okno **změnit správu zdrojového kódu** .<br />10. v potvrzovacím dialogovém okně klikněte na **pokračovat s těmito vazbami** .<br />11. Pokud se zobrazí dialogové okno s upozorněním, klikněte na tlačítko **OK** .<br />12. Projděte si všechno. V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />13. Otevřete řešení ze správy zdrojového kódu do nového umístění.|`Result from Step 12:`<br /><br /> Řešení a projekt jsou vázané na a zapsané do nového cíle v úložišti verzí.<br /><br /> Soubory řešení a projektu jsou vráceny se změnami.<br /><br /> Hierarchie projektu verze úložiště odpovídá hierarchii složek projektu na disku.<br /><br /> `Result from Step 13:`<br /><br /> Všechny položky projektu jsou staženy.|  
|Vazba na umístění, které je synchronizované s klientem|1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Vytvořte duplikát řešení a projektu v úložišti verzí (sdílení a větev, pokud používáte [!INCLUDE[vsvss](../../includes/vsvss-md.md)] ).<br />4. Otevřete dialogové okno **změnit správu zdrojového** kódu (**soubor**, Správa **zdrojového kódu**, **změnit správu zdrojového kódu**).<br />5. zrušte vazbu všech.<br />6. Kliknutím na tlačítko **OK** zavřete dialogové okno **změnit správu zdrojového kódu** .<br />7. znovu otevřít dialogové okno **změnit správu zdrojového kódu** .<br />8. Vyberte vše.<br />9. klikněte na **BIND**.<br />10. Procházejte do rozvětvené složky řešení a projektu (z kroku 3).<br />11. Kliknutím na tlačítko **OK** zavřete dialogové okno **změnit správu zdrojového kódu** .<br />12. Získejte zpětnou rekurzivní položku pro všechny položky.|Obsah souboru po získání je stejný jako před Get.|  
|Vazba na umístění, které není synchronizované s klientem|1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Vytvořte duplikát řešení a projektu v úložišti verzí (sdílení a větev, pokud používáte [!INCLUDE[vsvss](../../includes/vsvss-md.md)] ).<br />4. Upravte soubory v rozvětvených projektech v úložišti verzí.<br />5. Otevřete dialogové okno **změnit správu zdrojového** kódu (**soubor**, Správa **zdrojového**kódu, **změnit správu zdrojového kódu**).<br />6. zrušte vazbu všech.<br />7. Kliknutím na tlačítko **OK** zavřete dialogové okno **změnit správu zdrojového kódu** .<br />8. znovu otevřít dialogové okno **změnit správu zdrojového kódu** .<br />9. Vyberte vše.<br />10. klikněte na **BIND**.<br />11. Procházejte do větvení umístění pro řešení a projekt.<br />12. Kliknutím na tlačítko **OK** zavřete dialogové okno **změnit správu zdrojového kódu** .<br />13. Pokud se zobrazí dialogové okno s upozorněním, potvrďte ho.<br />14. Získejte nejnovější rekurzivní pro všechny položky.|Soubory, které byly upraveny v kroku 4, jsou také místně změněny.|  
|Vázání řešení, které nikdy nebylo pod správou zdrojových kódů|1. Vytvořte prázdnou složku ve správě zdrojového kódu.<br />2. Vytvořte projekt klienta.<br />3. Otevřete dialogové okno **změnit správu zdrojového** kódu (**soubor**, Správa **zdrojového kódu**, **změnit správu zdrojového kódu**).<br />4. Připojte řešení k prázdnému umístění ve správě zdrojového kódu.<br />5. Kliknutím na tlačítko **OK** zavřete dialogové okno **změnit správu zdrojového kódu** .<br />6. v potvrzovacím dialogovém okně klikněte na **pokračovat s těmito vazbami** .<br />7. Pokud se zobrazí dialogové okno s upozorněním, klikněte na tlačítko **OK** .|Řešení je přidáno do správy zdrojového kódu.<br /><br /> Řešení a projekt jsou rezervovány.|  
|Zrušit vázání|1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Otevřete dialogové okno změnit správu zdrojového kódu.<br />4. zrušte vazbu všech.<br />5. Kliknutím na tlačítko **OK** zavřete dialogové okno. V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />6. znovu otevřete dialogové okno **změnit správu zdrojového kódu** .<br />7. vytvoří se vazba na nesouvisející umístění.<br />8. klikněte na tlačítko **Storno**.|`Result from Step 5:`<br /><br /> Řešení již není pod správou zdrojových kódů<br /><br /> `Result from Step 8:`<br /><br /> Řešení ještě není pod správou zdrojových kódů.|  
  
### <a name="case-5b-unbind"></a>Případ 5b: zrušení vazby  
 Zrušení vazby odebere z projektů a jejich řešení informace o správě zdrojového kódu. Ovlivněné projekty a řešení jsou založeny na kombinaci výběru uživatele a způsobu, jakým byly položky přidány do správy zdrojového kódu.  
  
|Akce|Testovací kroky|Očekávané výsledky k ověření|  
|------------|----------------|--------------------------------|  
|Zrušit vazbu řešení obsahující jeden systém souborů nebo místní webový projekt služby IIS a jeden klientský projekt|1. Vytvořte systém souborů nebo místní webový projekt služby IIS.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte do řešení nový projekt klienta.<br />4. Pokud se zobrazí výzva, přijměte rezervaci řešení.<br />5. Otevřete dialogové okno **změnit správu zdrojového kódu** .<br />6. klikněte na zrušit **vazbu**.<br />7. dialogové okno zavřete kliknutím na tlačítko **OK** .<br />8. Pokuste se rezervovat řešení, projekt, položky řešení, položky projektu.|Řešení a projekty nejsou pod správou zdrojových kódů.<br /><br /> Příkazy nabídky správy zdrojového kódu se nezobrazí.|  
|Zrušit vazbu|1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Otevřete dialogové okno **změnit správu zdrojového kódu** .<br />4. klikněte na zrušit **vazbu vše**.<br />5. klikněte na tlačítko **Storno**.|Řešení je pod správou zdrojových kódů.|  
  
### <a name="case-5c-rebind"></a>Případ 5c: Obnova vazby  
 Rebind je jednoduše kombinací zrušení vazby a vazby – proces převázání projektu nebo řešení, které bylo dříve pod správou zdrojových kódů a byl bez vazby.  
  
|Akce|Testovací kroky|Očekávané výsledky k ověření|  
|------------|----------------|--------------------------------|  
|Obnova vazby řešení a projektů bez zavření dialogového okna **změnit správu zdrojů**|1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Otevřete dialogové okno **změnit správu zdrojového kódu** .<br />4. klikněte na zrušit **vazbu**.<br />5. Vyberte všechny řádky.<br />6. klikněte na **BIND**.<br />7. Kliknutím na tlačítko **OK** zavřete dialogové okno **změnit správu zdrojového kódu** .<br />8. Pokud se zobrazí výzva, přijměte rezervaci.|Řešení a projekt jsou pod správou zdrojových kódů.|  
|Znovu vytvořit vazby projektu bez dialogového okna **změnit správu zdrojového kódu**|1. Vytvořte projekt.<br />2. Přidejte do správy zdrojových kódů pouze projekt pomocí ovládacího prvku Správa zdrojového kódu (soubor->– >přidat vybrané projekty do správy zdrojových kódů.<br />3. Otevřete dialogové okno změnit správu zdrojového kódu.<br />4. zrušte vazbu pouze na projekt.<br />5. vytvořte pouze projekt.|Řešení zůstává neřízené.<br /><br /> Projekt zůstane řízený.|  
|Obnovit vazby pouze bez dialogového okna **změnit správu zdrojového kódu**|1. Vytvořte projekt.<br />2. přidejte pouze řešení do správy zdrojů pomocí (**soubor**, **Správa zdrojového kódu**, **přidejte vybrané projekty do správy zdrojových kódů**.<br />3. Otevřete dialogové okno **změnit správu zdrojového kódu** .<br />4. zrušte vazbu jenom na řešení (Nezavírejte dialogové okno **změnit správu zdrojového kódu** ).<br />5. Vytvořte vazby jenom na řešení.<br />6. Kliknutím na tlačítko **OK** zavřete dialogové okno.<br />7. Podívejte se na položky řešení a řešení (pokud existují).|Řešení zůstává řízené.<br /><br /> Projekt zůstává neřízený.|  
|Znovu vytvořit vazby řešení/projektu pouze v případě, že je ve stejném adresáři|1. Vytvořte projekt.<br />2. Přidejte do správy zdrojů pouze projekt pomocí (**soubor**, **Správa zdrojového kódu**, **přidejte vybrané projekty do správy zdrojových kódů**.<br />3. Zavřete řešení.<br />4. Vytvořte nové řešení s alespoň dvěma projekty.<br />5. Přidejte řešení do správy zdrojového kódu.<br />6. Přidejte projekt vytvořený v kroku 1 ze správy zdrojového kódu.<br />7. Pokud se zobrazí výzva, přijměte rezervaci řešení.<br />8. Vraťte se do celého řešení.<br />9. Otevřete dialogové okno **změnit správu zdrojového kódu** .<br />10. vyberte přidaný projekt (z kroku 6) a klikněte na zrušit **vazbu**.<br />11. Kliknutím na tlačítko **OK** zavřete dialogové okno.<br />12. Pokud se zobrazí výzva, přijměte rezervaci.<br />13. znovu otevřít dialogové okno **změnit správu zdrojového kódu** .<br />14. vyberte přidaný projekt (z kroku 6) a klikněte na **BIND**.<br />15. Vyberte původní umístění.|Řešení a projekty zůstávají řízené.|  
  
## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
