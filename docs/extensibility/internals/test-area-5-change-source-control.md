---
title: 'Testovací oblast 5: Změna správy zdrojového kódu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed7093d50290c4c0612faf6c7691f90e62a08267
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847354"
---
# <a name="test-area-5-change-source-control"></a>Testovací oblast 5: Změna správy zdrojového kódu
Tento modul plug-in testu oblast správy zdrojového kódu obsahuje informace o změnou správy zdrojových kódů prostřednictvím **změnit správu zdrojových kódů** příkazu.  

 **Změna správy zdrojového kódu** příkaz poskytuje čtyři základní funkce pro uživatele:  

- **Vázání:**  

   Umožňuje uživateli vytvořit nebo obnovit zdrojový ovládací prvek propojení mezi řešení nebo projektu a úložiště verzí.  

- **Zrušení vazby:**  

   Odebere projekt či řešení ze správy zdrojového kódu na základě jednotlivých připojení.  

- **Připojení/odpojení:**  

  Přepíná připojen nebo offline stav řízené řešení, které jsou obsaženy v oblasti 3. Další informace najdete v tématu [testovací oblast 3: Podívejte se na / rezervace](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  

## <a name="command-menu-access"></a>Přístup do příkazu nabídky  
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí nabídky Cesta se používá v testovacích procesech.  

 Změnit správu zdrojových kódů:**souboru**, **správy zdrojového kódu**, **Změna správy zdrojového kódu**.  

## <a name="test-cases"></a>Testovací případy  
 Toto jsou pro konkrétní testovací případy **změnit správu zdrojových kódů** příkaz Testovací oblast.  

### <a name="case-5a-bind"></a>Malá a velká 5a: vytvoření vazby  
 Vazba umožňuje uživateli přidat informace o řízení zdrojového kódu pro vybrané projekty a řešení. Obvykle bude uživatel vyzván k identifikaci projektu ve správě zdrojového kódu, ke kterému jde přidat. Uživatele nelze vytvořit nový projekt ve správě zdrojového kódu jako součást této operace (kontrastu u přidat do správy zdrojového kódu).  


| Akce | Testovací kroky | Chcete-li ověřit očekávané výsledky |
| - | - | - |
| Vytvoření vazby na prázdné umístění | 1.  Vytvoření projektu.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Otevřít **změnit správu zdrojových kódů** dialogové okno (**souboru**, **správy zdrojových kódů**, **změnit správu zdrojových kódů**).<br />4.  Klikněte na tlačítko **odpojit**.<br />5.  Dialogové okno upozornění přijměte, pokud se zobrazí.<br />6.  Vyberte všechny položky.<br />7.  Klikněte na tlačítko **svázat**.<br />8.  Přejděte na prázdné místo v úložiště správy zdrojových kódů.<br />9. Klikněte na tlačítko **OK** zavřete **změnit správu zdrojových kódů** dialogové okno.<br />10. Klikněte na tlačítko **pokračovat s těmito vazbami** v potvrzovacím dialogovém okně.<br />11. Klikněte na tlačítko **OK** v dialogovém okně upozornění, pokud se zobrazí.<br />12. Vše se změnami. Pokud tento krok úspěšný, pokračujte dalším krokem.<br />13. Otevřít řešení ze správy zdrojového kódu do nového umístění. | `Result from Step 12:`<br /><br /> Řešení a projektu jsou vázána na a zapsána do nového cíle v úložišti verzí.<br /><br /> Soubory řešení a projekt se změnami.<br /><br /> Hierarchie projektu úložiště verze odpovídá hierarchii složek projektu na disku.<br /><br /> `Result from Step 13:`<br /><br /> Všechny položky projektu budou staženy. |
| Připojení k umístění, které se synchronizuje s klientem | 1.  Vytvoření projektu.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Vytvořit duplikát řešení a projektu ve verzi úložiště (sdílené složky a větve, pokud používáte [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Otevřít **změnit správu zdrojových kódů** dialogové okno (**souboru**, **správy zdrojových kódů**, **změnit správu zdrojových kódů**).<br />5.  Odpojit vše.<br />6.  Klikněte na tlačítko **OK** zavřete **změnit správu zdrojových kódů** dialogové okno.<br />7.  Znovu otevřít **změnit správu zdrojových kódů** dialogové okno.<br />8.  Vyberte vše.<br />9. Klikněte na tlačítko **svázat**.<br />10. Přejděte k rozvětvenému umístění řešení a projektu (z kroku 3)<br />11. Klikněte na tlačítko **OK** zavřete **změnit správu zdrojových kódů** dialogové okno.<br />12. Získejte nejnovější rekurzivní pro všechny položky. | Obsah souboru po get je stejná jako před get. |
| Připojení k umístění, které je synchronizovaný s klientem | 1.  Vytvoření projektu.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Vytvořit duplikát řešení a projektu ve verzi úložiště (sdílené složky a větve, pokud používáte [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Upravte soubory v projektu větve v úložišti verzí.<br />5.  Otevřít **změnit správu zdrojových kódů** dialogové okno (**souboru**, **správy zdrojových kódů**, **změnit správu zdrojových kódů**).<br />6.  Odpojit vše.<br />7.  Klikněte na tlačítko **OK** zavřete **změnit správu zdrojových kódů** dialogové okno.<br />8.  Znovu otevřít **změnit správu zdrojových kódů** dialogové okno.<br />9. Vyberte vše.<br />10. Klikněte na tlačítko **svázat**.<br />11. Přejděte na větev vytvořená umístění řešení a projektu.<br />12. Klikněte na tlačítko **OK** zavřete **změnit správu zdrojových kódů** dialogové okno.<br />13. Dialogové okno upozornění přijměte, pokud se zobrazí.<br />14. Získejte nejnovější rekurzivní pro všechny položky. | Soubory, které byly změněny v kroku 4 jsou také upravena místně. |
| Vytvoření vazby řešení, které se nikdy pod správou zdrojových kódů | 1.  Vytvořte prázdnou složku ve správě zdrojového kódu.<br />2.  Vytvoření projektu klienta.<br />3.  Otevřít **změnit správu zdrojových kódů** dialogové okno (**souboru**, **správy zdrojových kódů**, **změnit správu zdrojových kódů**).<br />4.  Vytvoření vazby řešení na prázdné místo ve správě zdrojového kódu.<br />5.  Klikněte na tlačítko **OK** zavřete **změnit správu zdrojových kódů** dialogové okno.<br />6.  Klikněte na tlačítko **pokračovat s těmito vazbami** v potvrzovacím dialogovém okně.<br />7.  Klikněte na tlačítko **OK** v dialogovém okně upozornění, pokud se zobrazí. | Přidání řešení do správy zdrojového kódu.<br /><br /> Řešení a projektu jsou rezervovány. |
| Zrušení vazby | 1.  Vytvoření projektu.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Otevření dialogu změnit správu zdrojových kódů.<br />4.  Odpojit vše.<br />5.  Klikněte na tlačítko **OK** tlačítka zavřete dialogové okno. Pokud tento krok úspěšný, pokračujte dalším krokem.<br />6.  Znovu otevřít **změnit správu zdrojových kódů** dialogové okno.<br />7.  Vytvořit vazbu na nesouvisejících umístění.<br />8.  Klikněte na tlačítko **zrušit**. | `Result from Step 5:`<br /><br /> Řešení již není pod správou zdrojových kódů<br /><br /> `Result from Step 8:`<br /><br /> Řešení je stále není v kategorii Správa zdrojového kódu. |

### <a name="case-5b-unbind"></a>Malá a velká 5b: odpojení  
 Zrušení vazby odebere zdrojového kódu informace o řízení z projektů a jejich řešení. Ovlivněné projekty a řešení jsou založeny na výběru uživatele i jak byly přidány do správy zdrojového kódu.  

|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Odpojit řešení obsahující jeden systému souborů nebo místní služby IIS webový projekt a jeden klientský projekt|1.  Vytvořte systém souborů nebo místní projekt webové služby IIS.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Přidání nového projektu klienta do řešení.<br />4.  Pokud se zobrazí výzva, přijměte zkontrolujte z řešení.<br />5.  Otevřít **změnit správu zdrojových kódů** dialogové okno.<br />6.  Klikněte na tlačítko **odpojit**.<br />7.  Klikněte na tlačítko **OK** zavřete dialogové okno.<br />8.  Pokuste se podívejte se na řešení, projektů, položky řešení, položky projektu.|Řešení a projekty nejsou pod správou zdrojových kódů.<br /><br /> Příkazy nabídky ovládací prvek zdroje se nezobrazují.|  
|Zrušit odpojení|1.  Vytvoření projektu.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Otevřít **změnit správu zdrojových kódů** dialogové okno.<br />4.  Klikněte na tlačítko **odpojit všechny**.<br />5.  Klikněte na tlačítko **zrušit**.|Řešení je pod správou zdrojových kódů.|  

### <a name="case-5c-rebind"></a>Malá a velká 5c: obnovení vazby  
 Obnovení vazby je jednoduše kombinací zrušit vazbu a vazby – proces obnovení vazby projektu/řešení, které dříve bylo pod správou zdrojových kódů a nevázaného.  

|Akce|Testovací kroky|Chcete-li ověřit očekávané výsledky|  
|------------|----------------|--------------------------------|  
|Rebind řešení a projekty bez zavření **změnit správu zdrojových kódů** dialogové okno|1.  Vytvoření projektu.<br />2.  Přidáte řešení do správy zdrojového kódu.<br />3.  Otevřít **změnit správu zdrojových kódů** dialogové okno.<br />4.  Klikněte na tlačítko **odpojit**.<br />5.  Vyberte všechny řádky.<br />6.  Klikněte na tlačítko **svázat**.<br />7.  Klikněte na tlačítko **OK** zavřete **změnit správu zdrojových kódů** dialogové okno.<br />8.  Pokud se zobrazí výzva, přijměte checkout.|Řešení a projektu jsou pod správou zdrojových kódů.|  
|Znovu připojit projekt pouze bez zavření **změnit správu zdrojových kódů** dialogové okno|1.  Vytvoření projektu.<br />2.  Přidat do zdrojového ovládacího prvku pomocí pouze projekt (Soubor -> zdroje ovládacího prvku -> Přidat vybrané projekty do správy zdrojového kódu.<br />3.  Otevření dialogu změnit správu zdrojových kódů.<br />4.  Nejprve zrušte vazbu jenom projektu.<br />5.  Vytvořit vazbu jenom projektu.|Řešení zůstane nespravovaný.<br /><br /> Projekt zůstává řízené.|  
|Rebind řešení pouze bez zavření **změnit správu zdrojových kódů** dialogové okno|1.  Vytvoření projektu.<br />2.  Přidejte pouze řešení do zdrojového ovládacího prvku pomocí (**souboru**, **správy zdrojových kódů**, **přidat vybrané projekty do správy zdrojových kódů**.<br />3.  Otevřít **změnit správu zdrojových kódů** dialogové okno.<br />4.  Nejprve zrušte vazbu jenom řešení (nezavírejte **změnit správu zdrojových kódů** dialogové okno.)<br />5.  Vytvořit vazbu jenom řešení.<br />6.  Klikněte na tlačítko **OK** zavřete dialogové okno.<br />7.  Podívejte se na řešení a položky řešení (pokud existuje)|Řešení zůstane řízené.<br /><br /> Projekt zůstává nespravovaný.|  
|Rebind řešení nebo projektu pouze pokud ve stejném adresáři|1.  Vytvoření projektu.<br />2.  Přidat pouze projekt do zdrojového ovládacího prvku pomocí (**souboru**, **správy zdrojových kódů**, **přidat vybrané projekty do správy zdrojových kódů**.<br />3.  Zavřete řešení.<br />4.  Vytvořte nové řešení s alespoň dva projekty.<br />5.  Přidáte řešení do správy zdrojového kódu.<br />6.  Přidáte projekt vytvořený v kroku 1 ze správy zdrojového kódu.<br />7.  Pokud se zobrazí výzva, přijměte checkout řešení.<br />8.  Vrátit se změnami celé řešení.<br />9. Otevřít **změnit správu zdrojových kódů** dialogové okno.<br />10. Přidání projektu (z kroku 6) vyberte a klikněte na tlačítko **zrušit vazbu**.<br />11. Klikněte na tlačítko **OK** zavřete dialogové okno.<br />12. Pokud se zobrazí výzva, přijměte rezervace.<br />13. Znovu otevřít **změnit správu zdrojových kódů** dialogové okno.<br />14. Přidání projektu (z kroku 6) vyberte a klikněte na tlačítko **svázat**.<br />15. Vyberte původní umístění.|Řešení a projekty zůstanou řízené.|  

## <a name="see-also"></a>Viz také  
 [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)