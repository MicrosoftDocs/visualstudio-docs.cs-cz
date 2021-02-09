---
title: 'Testovací oblast 1: Přidání To-Open ze správy zdrojového kódu | Microsoft Docs'
description: Tato testovací oblast modulu plug-in zdrojového ovládacího prvku pokrývá umístění řešení nebo projektů pod správou zdrojových kódů a jejich načítání ze správy zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbcbc197a610f7caf2a1641a291db18fcea9dbda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898321"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Testovací oblast 1: Přidání nebo otevření ze správy zdrojového kódu
Tato testovací oblast modulu plug-in zdrojového ovládacího prvku pokrývá umístění řešení nebo projektů pod správou zdrojových kódů a jejich načítání ze správy zdrojového kódu.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]V testovacích případech se používají následující cesty nabídky integrovaného vývojového prostředí:

- Pro [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] otevřete ze správy zdrojového kódu: **soubor**, **otevřít**,  / **řešení** projektu; Podívejte se do [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] umístění.

- Pro jiné moduly plug-in správy zdrojového kódu otevřete ze správy zdrojového kódu: **soubor**, Správa **zdrojového kódu**, **Otevřít ze správy zdrojového kódu**.

- Přidat do správy zdrojového kódu: **soubor**, Správa **zdrojového kódu**, **Přidat řešení do souboru správy zdrojového** kódu, **Správa zdrojového kódu**, **Přidat vybrané projekty do správy zdrojových kódů**.

- Místní nabídka (projekt/řešení), **Přidat řešení do správy zdrojového kódu**.

- Přidat ze správy zdrojového kódu: **soubor**, Správa **zdrojového kódu**, **Přidat projekt ze správy zdrojových kódů**.

- Pro [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] je k dispozici také příkaz Přidat ze správy zdrojového kódu ze **souboru**, **Přidat**, **existující projekt**; Podívejte se do [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] umístění.

  > [!NOTE]
  > V tomto testu lze použít cestu k místnímu souboru nebo místní službě IIS (webový server).

## <a name="expected-behavior"></a>Očekávané chování

- U každého podporovaného typu projektu by měl být uživatel schopný "přidat do" a "otevřít z" správy zdrojového kódu.

- Když je projekt přidán do správy zdrojových kódů, \<*ProjectName*> je vytvořen odpovídající soubor. vspscc (soubor s nápovědou projektu). Obsahuje seznam souborů vyloučení a informace o připojení. Tento soubor neodstraňujte, protože obsahuje informace specifické pro projekt.

- Při přidání řešení do správy zdrojového kódu \<*SolutionName*> se vytvoří odpovídající soubor. vssscc (troje). Textový soubor obsahuje informace o připojení a seznam souborů vyloučení, podobně jako soubor nápovědy k projektu. Tento soubor je dočasný a existuje pouze v databázi správy zdrojů.

- Když je řešení otevřeno ze správy zdrojového kódu, \<*SolutionName*> soubor. vsscc (Double S), který existuje pouze v databázi správy zdrojů, je místně vytvořen v dočasném souboru. Tento soubor obsahuje cestu ze složky pro připojení řešení k souboru řešení. Tento soubor je dočasný a po dokončení operace "otevřít ze správy zdrojového kódu" je místní kopie odstraněna.

- Po přidání projektu do správy zdrojového kódu můžete provádět libovolné akce správy zdrojového kódu (rezervovat, získat a tak dále).

## <a name="test-cases"></a>Testovací případy
 Níže jsou uvedené konkrétní testovací případy pro přidání do a otevření z testovací oblasti správy zdrojového kódu.

### <a name="case-1a-add-solution-to-source-control"></a>Případ 1a: Přidání řešení do správy zdrojového kódu
 Tento testovací případ se zaměřuje na přidání řešení do správy zdrojového kódu.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Přidat řešení obsahující klientský projekt do správy zdrojového kódu|1. Vytvořte projekt klienta.<br />2. Přidejte řešení do správy zdrojového kódu (**soubor**, Správa **zdrojového kódu**, **přidejte řešení do správy zdrojových kódů**).|Řešení/projekt bylo přidáno do správy zdrojového kódu.|
|Přidání řešení obsahujícího systém souborů nebo místní webový projekt služby IIS do správy zdrojového kódu|1. Vytvořte systém souborů nebo místní webový projekt služby IIS (pomocí tlačítka Procházet přejděte na umístění projektu; cesta Určuje, který typ webového projektu je vytvořen).<br />2. Přidejte řešení do správy zdrojového kódu (**soubor**, Správa **zdrojového kódu**, **přidejte řešení do správy zdrojových kódů**).|Řešení/projekt bylo přidáno do správy zdrojového kódu.|
|Přidat řešení obsahující webový projekt vzdálené lokality do správy zdrojového kódu|1. Vytvořte webový projekt vzdálené lokality.<br />2. Přidejte řešení do správy zdrojového kódu (**soubor**, Správa **zdrojového kódu**, **přidejte řešení do správy zdrojových kódů**).<br />3. klikněte na tlačítko **OK** v dialogovém okně upozornění přístupu aplikace FrontPage.|Řešení bylo přidáno do správy zdrojového kódu.<br /><br /> Vzdálený webový projekt není pod správou zdrojových kódů. (Vzdálené projekty webu musí být řízené z vlastního serveru služby IIS.)|
|Přidejte jedno řešení projektu do správy zdrojových kódů pomocí **Přidat vybrané projekty do správy zdrojového kódu**.|1. Vytvořte jedno projektové řešení.<br />2. přidejte pouze řešení do správy zdrojového kódu jako výběr (**soubor**, Správa **zdrojového kódu**, **Přidat vybrané projekty do správy zdrojových kódů**). V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />3. Přidejte projekt do správy zdrojových kódů jako výběr (**soubor**, Správa **zdrojového kódu**, **přidejte vybrané projekty do správy zdrojových kódů**).<br />4. Chcete-li přidat projekt do stejného umístění, klikněte na tlačítko **Ano** .<br />5. klikněte na možnost **Rezervovat** v dialogovém okně **rezervovat pro úpravy** .|`Result from Step 2:`<br /><br /> Projekt a všechny soubory v rámci projektu mají kontroler zdrojového kódu, který obsahuje popis "není pod správou zdrojových kódů".<br /><br /> `Result from Step 5:`<br /><br /> Soubor projektu a řešení jsou ve stejné složce ve správě zdrojového kódu.|
|Zrušení přidání řešení do správy zdrojového kódu|1. Vytvořte jedno projektové řešení.<br />2. pokus o přidání projektu a řešení do správy zdrojového kódu. V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />3. po dokončení v systému správy zdrojů klikněte na zrušit.|`Result from Step 2:`<br /><br /> Dialogové okno nastavení správy zdrojového umístění projektu se zobrazí pouze jednou.<br /><br /> `Result from Step 3:`<br /><br /> Projekt přidat zrušeno, projekt/řešení není pod správou zdrojových kódů a všechny nabídky přidat do správy zdrojového kódu jsou stále k dispozici.|

### <a name="case-1b-open-solution-from-source-control"></a>Případ 1b. Otevřít řešení ze správy zdrojového kódu
 Tento testovací případ se zaměřuje na otevírání řešení ze správy zdrojového kódu.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Otevření řešení obsahujícího klientský projekt ze správy zdrojového kódu|1. Vytvořte projekt klienta.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Zavřete řešení.<br />4. Otevřete řešení ze správy zdrojového kódu do nového umístění.|Řešení/projekt bylo otevřeno ze správy zdrojového kódu.|
|Otevření řešení obsahujícího místní webový projekt nebo webového projektu služby IIS ze správy zdrojového kódu|1. Vytvořte místní webový projekt nebo web služby IIS.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Zavřete řešení.<br />4. Otevřete řešení ze správy zdrojového kódu do nového umístění.|Řešení/projekt bylo otevřeno ze správy zdrojového kódu.|
|Otevření řešení, které obsahuje webový projekt vzdálené lokality ze správy zdrojového kódu|1. Vytvořte webový projekt vzdálené lokality.<br />2. Přidejte řešení do správy zdrojového kódu. V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />3. Zavřete řešení.<br />4. Otevřete řešení ze správy zdrojového kódu do nového umístění.|`Result from Step 2:`<br /><br /> Web vzdáleného webu není pod správou zdrojových kódů.<br /><br /> `Result from Step 4:`<br /><br /> Řešení se otevřelo ze správy zdrojového kódu.<br /><br /> Je načten projekt vzdálené lokality, ale není pod správou zdrojových kódů.|

### <a name="case-1c-add-solution-from-source-control"></a>Případ 1C: Přidání řešení ze správy zdrojového kódu
 Tento testovací případ se zaměřuje na přidávání řešení ze správy zdrojového kódu.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Přidat do prázdného řešení – jediné řešení projektu|1. Vytvořte jedno projektové řešení.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Zavřete řešení.<br />4. Vytvořte druhé prázdné řešení.<br />5. Přidejte dříve kontrolované řešení ze správy zdrojového kódu (**soubor**, Správa **zdrojového kódu**, **Přidat projekt ze správy zdrojových kódů**).|Přidaný projekt se zobrazí v **Průzkumník řešení** a je vrácen se změnami.|
|Přidat do řešení pomocí jednoho projektu – jeden projekt|1. Vytvořte řešení pomocí jednoho projektu.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Zavřete řešení.<br />4. Vytvořte druhé prázdné řešení.<br />5. Přidejte dříve kontrolované řešení ze správy zdrojového kódu (**soubor**, Správa **zdrojového kódu**, **Přidat projekt ze správy zdrojových kódů**).|Přidaný projekt se zobrazí v **Průzkumník řešení** a je vrácen se změnami.|
|Přidat do řešení – řešení přidané do správy zdrojového kódu podle výběru|1. Vytvořte řešení pomocí projektu.<br />2. jako výběr přidejte pouze řešení do správy zdrojového kódu. V případě úspěšného provedení tohoto kroku pokračujte dalším krokem.<br />3. Zavřete řešení.<br />4. Vytvořte nové řešení.<br />5. Přidejte dříve kontrolované řešení ze správy zdrojového kódu (**soubor**, Správa **zdrojového kódu**, **Přidat projekt ze správy zdrojových kódů**).|`Result from Step 2:`<br /><br /> Projekt není pod správou zdrojových kódů.<br /><br /> `Result from Step 5:`<br /><br /> Pokud má první řešení položky řešení, nelze je přidat ze správy zdrojových kódů, takže se nezobrazí.<br /><br /> Projekt z prvního řešení se jeví jako nedostupný.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
