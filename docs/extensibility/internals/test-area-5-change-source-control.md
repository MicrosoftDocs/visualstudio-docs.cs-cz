---
title: 'Testovací oblast 5: Změna správy zdrojového kódu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c0df31fbecd532e6a5f7f317730cd995cd8225
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704523"
---
# <a name="test-area-5-change-source-control"></a>Testovací oblast 5: Změna správy zdrojového kódu
Tato testovací oblast modulu plug-in pro řízení zdrojového kódu zahrnuje změnu správy zdrojového kódu pomocí příkazu **Změnit správě zdrojového kódu.**

 **Příkaz Change Source Control** poskytuje uživateli čtyři základní funkce:

- **Vázat:**

   Umožňuje uživateli vytvořit nebo obnovit propojení správy zdrojového kódu mezi řešením nebo projektem a úložištěm verzí.

- **Odpojení:**

   Odebere projekt/řešení ze správy zdrojového kódu na základě připojení.

- **Připojit/odpojit:**

  Přepíná připojený nebo offline stav řízeného řešení, který je pokryt oblastí 3. Další informace naleznete v [tématu Test Area 3: Check Out/Redo Checkout](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesta nabídky integrované vývojové prostředí se používá v testovacích případech.

 Změnit smělý zdroj:**Soubor**, **Řízení zdrojového kódu**, **Změnit smělé řízení zdrojového kódu**.

## <a name="test-cases"></a>Testovací případy
 Následují specifické testovací případy pro testovací oblast příkazu **Změnit řízení zdrojového kódu.**

### <a name="case-5a-bind"></a>Případ 5a: Bind
 Vazba umožňuje uživateli přidat informace o řízení zdrojového kódu do vybraných projektů a řešení. Uživatel je obvykle vyzván k identifikaci projektu ve zdrojovém ovládacím prvku, do kterého mají být přidány. Uživatel nesmí vytvořit nový projekt ve zdrojovém ovládacím prvku jako součást této operace (na rozdíl od přidat do správy zdrojového kódu).

| Akce | Testovací kroky | Očekávané výsledky k ověření |
| - | - | - |
| Vazba na prázdné umístění | 1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Otevřít dialogové okno **Otevřít změnu zdrojového kódu** **(Soubor,** **Řízení zdrojového kódu**, Změnit **směřovat zdroj).**<br />4. Klepněte na tlačítko **Zrušit vazbu**.<br />5. Pokud se zobrazí dialogové okno S upozorněním, přijměte dialogové okno s upozorněním.<br />6. Vyberte všechny položky.<br />7. Klepněte na tlačítko **Svázat**.<br />8. Přejděte do prázdného umístění v úložišti správy zdrojového kódu.<br />9. Klepnutím na **tlačítko OK** zavřete dialogové okno **Změnit správou zdrojového kódu.**<br />10. Klepněte na tlačítko **Pokračovat s těmito vazbami** v potvrzovacím dialogovém okně.<br />11. Pokud se zobrazí, klepněte v dialogovém okně upozornění na tlačítko **OK.**<br />12. Zkontrolujte vše. Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />13. Otevřete řešení ze správy zdrojového kódu do nového umístění. | `Result from Step 12:`<br /><br /> Řešení a projekt jsou vázány a zapsány do nového cíle v úložišti verzí.<br /><br /> Soubory řešení a projektu jsou se změnami.<br /><br /> Hierarchie projektu úložiště verzí odpovídá hierarchii složek projektu na disku.<br /><br /> `Result from Step 13:`<br /><br /> Všechny položky projektu jsou staženy. |
| Vazba na umístění, které je synchronizované s klientem | 1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Vytvořte duplikát řešení a projektu v [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]úložišti verzí (Share a Branch při použití).<br />4. Otevřít dialogové okno **Otevřít změnu zdrojového kódu** **(Soubor,** **Řízení zdrojového kódu**, Změnit **směřovat zdroj).**<br />5. Odvažte vše.<br />6. Klepnutím na **tlačítko OK** zavřete dialogové okno **Změnit správou zdrojového kódu.**<br />7. Znovu otevřete dialogové okno **Změnit směřovat zdroj.**<br />8. Vyberte vše.<br />9. Klepněte na **tlačítko Svázat**.<br />10. Vyhledejte rozvětvené umístění řešení a projektu (od kroku 3)<br />11. Klepnutím na **tlačítko OK** zavřete dialogové okno **Změnit správou zdrojového kódu.**<br />12. Získejte nejnovější rekurzivně pro všechny položky. | Obsah souboru po získání je stejný jako před získáním. |
| Vazba na umístění, které není synchronizováno s klientem | 1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Vytvořte duplikát řešení a projektu v [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]úložišti verzí (Share a Branch při použití).<br />4. Upravte soubory v rozvětvené projektu v úložišti verzí.<br />5. Otevřít dialogové okno **Otevřít změnu zdrojového kódu** **(Soubor,** **Řízení zdrojového kódu**, Změnit **směřovat zdroj).**<br />6. Odvažte vše.<br />7. Klepnutím na **tlačítko OK** zavřete dialogové okno **Změnit správou zdrojového kódu.**<br />8. Znovu otevřete dialogové okno **Změnit sřízení zdrojového kódu.**<br />9. Vyberte vše.<br />10. Klepněte na **tlačítko Svázat**.<br />11. Vyhledejte rozvětvené místo pro řešení a projekt.<br />12. Klepnutím na **tlačítko OK** zavřete dialogové okno **Změnit správou zdrojového kódu.**<br />13. Pokud se zobrazí dialogové okno Přijmout upozornění,<br />14. Získejte nejnovější rekurzivní pro všechny položky. | Soubory, které byly změněny v kroku 4 jsou také upraveny místně. |
| Vazby řešení, které nebylo nikdy pod spouštění zdrojového kódu | 1. Vytvořte prázdnou složku ve zdrojovém ovládacím prvku.<br />2. Vytvořte klientský projekt.<br />3. Otevřít dialogové okno **Otevřít změnu zdrojového kódu** **(Soubor,** **Řízení zdrojového kódu**, Změnit **směřovat zdroj).**<br />4. Spojte roztok s prázdným umístěním ve zdrojové směřování.<br />5. Klepnutím na **tlačítko OK** zavřete dialogové okno **Změnit správou zdrojového kódu.**<br />6. V potvrzovacím dialogovém okně klepněte na tlačítko **Pokračovat s těmito vazbami.**<br />7. Pokud se zobrazí, klepněte v dialogovém okně upozornění na tlačítko **OK.** | Řešení je přidándo správy zdrojového kódu.<br /><br /> Řešení a projekt jsou rezervovány. |
| Zrušit vazbu | 1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Otevřete dialogové okno Změnit snědnou zdrojovou kontrolu.<br />4. Odvažte vše.<br />5. Klepnutím na tlačítko **OK** zavřete dialogové okno. Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />6. Znovu otevřete dialogové okno **Změnit snědno zdroje.**<br />7. Spojte se s nesouvisejícím umístěním.<br />8. Klepněte na tlačítko **Storno**. | `Result from Step 5:`<br /><br /> Řešení již není pod kontrolou zdrojového zdroje<br /><br /> `Result from Step 8:`<br /><br /> Řešení stále není pod spouštění zdrojového kódu. |

### <a name="case-5b-unbind"></a>Případ 5b: Zrušení vazby
 Unbind odebere informace o spouštění zdrojového kódu z projektů a jejich řešení. Ovlivněné projekty a řešení jsou založeny na kombinaci výběru uživatele a jak byly položky přidány do správy zdrojového kódu.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Zrušit vazbu řešení obsahujícího jeden systém souborů nebo místní webový projekt služby IIS a jeden klientský projekt|1. Vytvořte systém souborů nebo místní webový projekt služby IIS.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Přidejte do řešení nový klientský projekt.<br />4. Přijměte check-out řešení, pokud je výzva.<br />5. Otevřete dialogové okno **Změnit snědnou zdrojovou kontrolu.**<br />6. Klepněte na tlačítko **Zrušit vazbu**.<br />7. Klepnutím na **tlačítko OK** zavřete dialogové okno.<br />8. Pokus o prohlášení řešení, projektu, položek řešení, položek projektu.|Řešení a projekty nejsou pod smytem zdroj.<br /><br /> Příkazy nabídky Správy zdrojového kódu se nezobrazují.|
|Zrušit vazbu|1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Otevřete dialogové okno **Změnit snědnou zdrojovou kontrolu.**<br />4. Klepněte na tlačítko **Zrušit vazbu všech**.<br />5. Klepněte na tlačítko **Storno**.|Řešení je pod spouštění zdrojového kódu.|

### <a name="case-5c-rebind"></a>Případ 5c: Rebind
 Rebind je jednoduše kombinací rozvázat a vázat – proces opětovného vazby projektu nebo řešení, který byl dříve pod smyčkem zdrojového kódu a byl nevázaný.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Znovu navazovat řešení a projekty bez zavření dialogového okna **Změnit slučující zdroj**|1. Vytvořte projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Otevřete dialogové okno **Změnit snědnou zdrojovou kontrolu.**<br />4. Klepněte na tlačítko **Zrušit vazbu**.<br />5. Vyberte všechny řádky.<br />6. Klepněte na **tlačítko Svázat**.<br />7. Klepnutím na **tlačítko OK** zavřete dialogové okno **Změnit správou zdrojového kódu.**<br />8. Přijměte pokladnu, pokud se zobrazí výzva.|Řešení a projekt jsou pod smytem zdrojového kódu.|
|Změnit vazbu projektu pouze bez **zavření dialogového okna Změnit slučující zdroj**|1. Vytvořte projekt.<br />2. Přidejte pouze projekt do správy zdrojového kódu pomocí (>zdrojové správy->Přidat vybrané projekty do správy zdrojového kódu.<br />3. Otevřete dialogové okno Změnit snědnou zdrojovou kontrolu.<br />4. Odvažte pouze projekt.<br />5. Svázat pouze projekt.|Řešení zůstává nekontrolované.<br /><br /> Projekt zůstává pod kontrolou.|
|Změnit vazbu řešení pouze bez **zavření dialogového okna Změnit slučující zdroj**|1. Vytvořte projekt.<br />2. Přidejte pouze řešení pro slučovací systém pomocí **(Soubor**, **Řízení zdrojového kódu**, **Přidat vybrané projekty do správy zdrojového kódu**.<br />3. Otevřete dialogové okno **Změnit snědnou zdrojovou kontrolu.**<br />4. Zrušit vazbu pouze řešení (Nezavírejte **změnit slučovací skříň.)**<br />5. Spojte pouze roztok.<br />6. Klepnutím na **tlačítko OK** zavřete dialogové okno.<br />7. Podívejte se na řešení a položky řešení (pokud existuje.)|Řešení zůstává pod kontrolou.<br /><br /> Projekt zůstává nekontrolovaný.|
|Znovu navázat řešení/projekt pouze ve stejném adresáři|1. Vytvořte projekt.<br />2. Přidejte pouze projekt do správy zdrojového kódu pomocí **(Soubor**, **Řízení zdrojového kódu**, **Přidat vybrané projekty do správy zdrojového kódu**.<br />3. Uzavřete roztok.<br />4. Vytvořte nové řešení s nejméně dvěma projekty.<br />5. Přidejte řešení do správy zdrojového kódu.<br />6. Přidejte projekt vytvořený v kroku 1 ze správy zdrojového kódu.<br />7. Přijměte pokladnu řešení, pokud je výzva.<br />8. Zkontrolujte celý roztok.<br />9. Otevřete dialogové okno **Změnit snědnou zdrojovou kontrolu.**<br />10. Vyberte přidaný projekt (z kroku 6) a klepněte na tlačítko **Zrušit vazbu**.<br />11. Klepnutím na **tlačítko OK** zavřete dialogové okno.<br />12. Přijměte pokladnu, pokud se zobrazí výzva.<br />13. Znovu otevřete dialogové okno **Změnit směřovat zdroj.**<br />14. Vyberte přidaný projekt (z kroku 6) a klepněte na **tlačítko Vytvořit vazbu**.<br />15. Vyberte původní umístění.|Řešení a projekty zůstávají pod kontrolou.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
