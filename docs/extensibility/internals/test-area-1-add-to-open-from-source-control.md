---
title: 'Testovací oblast 1: Přidat otevření ze správy zdrojového kódu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ac7b8e5a60fe25ac22272cc28fc3ed6f903b058
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704684"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Testovací oblast 1: Přidat do/otevřít ze správy zdrojového kódu
Tato testovací oblast modulu plug-in pro správu zdrojového kódu zahrnuje umístění řešení nebo projektů pod správu zdrojového kódu a jejich načítání ze správy zdrojového kódu.

## <a name="command-menu-access"></a>Přístup k nabídce příkazů
 Následující [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cesty nabídky integrované vývojové prostředí se používají v testovacích případech:

- Pro [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], otevřít ze správy zdrojového kódu: **Soubor**, **Otevřít**, **Projektové**/**řešení**; podívejte se [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] na místo.

- Pro ostatní moduly plug-in správy zdrojového kódu otevřete ze správy zdrojového kódu: **Soubor**, **Řízení zdrojového kódu**, **Otevřít ze správy zdrojového kódu**.

- Přidat do správy zdrojového kódu: **Soubor**, **Řízení zdrojového kódu**, Přidat řešení do **souboru správy zdrojového kódu**, Řízení **zdrojového kódu**, Přidat vybrané **projekty do správy zdrojového kódu**.

- Místní nabídka (projekt/řešení), **přidat řešení do správy zdrojového kódu**.

- Přidat ze správy zdrojového kódu: **Soubor**, **Řízení zdrojového kódu**, Přidat projekt ze správy **zdrojového kódu**.

- Pro [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], přidat ze správy zdrojového kódu je také k dispozici ze **souboru**, **Přidat**, **Existující projekt**; podívejte se [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] na místo.

  > [!NOTE]
  > V tomto testu lze použít cestu k místnímu souboru nebo místnímu službě IIS (webový server).

## <a name="expected-behavior"></a>Očekávané chování

- Pro každý podporovaný typ projektu by měl být uživatel schopen "Přidat do" a "Otevřít z" správy zdrojového kódu.

- Při přidání projektu do správy zdrojového kódu je vytvořen odpovídající \<soubor *ProjectName*>.vspscc (soubor nápovědy projektu). Obsahuje seznam souborů vyloučení a informace o připojení. Neodstraňujte tento soubor, protože obsahuje informace specifické pro projekt.

- Při přidání řešení do správy zdrojového kódu je vytvořen odpovídající \<soubor *SolutionName*>.vssscc (triple S). Textový soubor obsahuje informace o připojení a seznam souborů vyloučení, podobně jako soubor nápovědy projektu. Tento soubor je dočasný a existuje pouze v databázi správy zdrojového kódu.

- Při otevření řešení ze správy \<zdrojového kódu je soubor *SolutionName*>.vsscc (double S), který existuje pouze v databázi správy zdrojového kódu, vytvořen místně v dočasném souboru. Tento soubor obsahuje cestu ze složky připojení řešení do souboru řešení. Tento soubor je dočasný a místní kopie je odstraněna po dokončení operace "Otevřít ze správy zdrojového kódu".

- Po přidání projektu do ovládacího prvku zdroj ového kódu můžete provádět všechny akce správy zdrojového kódu na něm (Rezervovat, Získat a tak dále).

## <a name="test-cases"></a>Testovací případy
 Následují specifické testovací případy pro testovací oblast Přidat do/Otevřít ze správy zdrojového kódu.

### <a name="case-1a-add-solution-to-source-control"></a>Případ 1a: Přidat řešení do správy zdrojového kódu
 Tento testovací případ se zaměřuje na přidání řešení do správy zdrojového kódu.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Přidání řešení obsahujícího projekt klienta do správy zdrojového kódu|1. Vytvořte klientský projekt.<br />2. Přidejte řešení do správy**zdrojového**kódu (Soubor , **Řízení zdrojového kódu**, Přidat řešení do správy **zdrojového kódu).**|Řešení nebo projekt byl přidán do správy zdrojového kódu.|
|Přidání řešení obsahujícího systém souborů nebo místní webový projekt služby IIS do správy zdrojového kódu|1. Vytvořte systém souborů nebo místní webový projekt služby IIS (pomocí tlačítka Procházet přejděte na umístění projektu; cesta určuje, jaký typ webového projektu je vytvořen).<br />2. Přidejte řešení do správy**zdrojového**kódu (Soubor , **Řízení zdrojového kódu**, Přidat řešení do správy **zdrojového kódu).**|Řešení nebo projekt byl přidán do správy zdrojového kódu.|
|Přidání řešení obsahujícího webový projekt vzdáleného webu do správy zdrojového kódu|1. Vytvořte webový projekt vzdáleného webu.<br />2. Přidejte řešení do správy**zdrojového**kódu (Soubor , **Řízení zdrojového kódu**, Přidat řešení do správy **zdrojového kódu).**<br />3. Klepněte na **tlačítko OK** v dialogovém okně upozornění aplikace FrontPage Access.|Řešení bylo přidáno do správy zdrojového kódu.<br /><br /> Projekt vzdálenélokality není pod sohledem zdroje. (Vzdálené projekty webu musí být řízeny z vlastního serveru Služby IIS.)|
|Přidejte jedno projektové řešení do správy zdrojového kódu pomocí **funkce Přidat vybrané projekty do správy zdrojového kódu**.|1. Vytvořte jedno projektové řešení.<br />2. Přidejte pouze řešení do správy zdrojového kódu jako výběr **(soubor**, **řízení zdrojového kódu**, **přidat vybrané projekty do správy zdrojového kódu).** Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />3. Přidejte projekt do správy zdrojového kódu jako výběr **(soubor**, **řízení zdrojového kódu**, **přidat vybrané projekty do správy zdrojového kódu).**<br />4. Chcete-li projekt přidat do stejného umístění, klepněte na tlačítko **Ano.**<br />5. Klikněte na **Rezervovat** v **dialogovém okně Rezervovat pro úpravy.**|`Result from Step 2:`<br /><br /> Projekt a všechny soubory v rámci projektu mají zaškrtnutý indikátor správy zdrojového kódu a popis ek "Není pod smělou sloužnou zdrojovou kontrolou".<br /><br /> `Result from Step 5:`<br /><br /> Soubor projektu a řešení jsou ve stejné složce ve složce zdrojového kódu.|
|Zrušení přidání řešení do správy zdrojového kódu|1. Vytvořte jedno projektové řešení.<br />2. Pokuste se přidat projekt a řešení do správy zdrojového kódu. Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />3. Zrušte jej poté, co jste v systému správy zdrojového kódu.|`Result from Step 2:`<br /><br /> Dialogové okno Nastavit řízení umístění projektu se zobrazí pouze jednou.<br /><br /> `Result from Step 3:`<br /><br /> Přidání projektu zrušeno, projekt/řešení není pod správou zdrojového kódu a všechny nabídky přidat do správy zdrojového kódu stále k dispozici.|

### <a name="case-1b-open-solution-from-source-control"></a>Případ 1b. Otevřít řešení ze správy zdrojového kódu
 Tento testovací případ se zaměřuje na otevření řešení ze správy zdrojového kódu.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Otevření řešení obsahujícího projekt klienta ze správy zdrojového kódu|1. Vytvořte klientský projekt.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Uzavřete roztok.<br />4. Otevřete řešení ze správy zdrojového kódu do nového umístění.|Řešení/Projekt otevřen ze správy zdrojového kódu.|
|Otevření řešení obsahujícího místní webový projekt nebo webový projekt služby IIS ze správy zdrojového kódu|1. Vytvořte místní webový projekt nebo webový projekt služby IIS.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Uzavřete roztok.<br />4. Otevřete řešení ze správy zdrojového kódu do nového umístění.|Řešení/Projekt otevřen ze správy zdrojového kódu.|
|Otevření řešení obsahujícího webový projekt vzdáleného webu ze správy zdrojového kódu|1. Vytvořte webový projekt vzdáleného webu.<br />2. Přidejte řešení do správy zdrojového kódu. Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />3. Uzavřete roztok.<br />4. Otevřete řešení ze správy zdrojového kódu do nového umístění.|`Result from Step 2:`<br /><br /> Vzdálený web webu není pod sohledem zdroje.<br /><br /> `Result from Step 4:`<br /><br /> Řešení otevřené ze správy zdrojového kódu.<br /><br /> Projekt vzdálenélokality je načten, ale není pod shodou zdrojového kódu.|

### <a name="case-1c-add-solution-from-source-control"></a>Případ 1c: Přidat řešení ze správy zdrojového kódu
 Tento testovací případ se zaměřuje na přidání řešení ze správy zdrojového kódu.

|Akce|Testovací kroky|Očekávané výsledky k ověření|
|------------|----------------|--------------------------------|
|Přidat do prázdného řešení – jedno projektové řešení|1. Vytvořte jedno projektové řešení.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Uzavřete roztok.<br />4. Vytvořte druhý prázdný roztok.<br />5. Přidejte dříve řízené řešení ze správy zdrojového kódu **(Soubor**, **Řízení zdrojového kódu**, **Přidat projekt ze správy zdrojového kódu).**|Přidaný projekt se zobrazí v **Průzkumníku řešení** a je se změnami.|
|Přidat k řešení s jedním projektem – jeden projekt|1. Vytvořte řešení s jedním projektem.<br />2. Přidejte řešení do správy zdrojového kódu.<br />3. Uzavřete roztok.<br />4. Vytvořte druhý prázdný roztok.<br />5. Přidejte dříve řízené řešení ze správy zdrojového kódu **(Soubor**, **Řízení zdrojového kódu**, **Přidat projekt ze správy zdrojového kódu).**|Přidaný projekt se zobrazí v **Průzkumníku řešení** a je se změnami.|
|Přidat do řešení – řešení přidané do správy zdrojového kódu výběrem|1. Vytvořte řešení s projektem.<br />2. Přidejte pouze řešení do správy zdrojového kódu jako výběr. Pokud je tento krok úspěšný, pokračujte dalším krokem.<br />3. Uzavřete roztok.<br />4. Vytvořte nové řešení.<br />5. Přidejte dříve řízené řešení ze správy zdrojového kódu **(Soubor**, **Řízení zdrojového kódu**, **Přidat projekt ze správy zdrojového kódu).**|`Result from Step 2:`<br /><br /> Projekt není pod smělou směřovanou zdroj.<br /><br /> `Result from Step 5:`<br /><br /> Pokud první řešení mělo položky řešení, nelze je přidat ze správy zdrojového kódu, takže se nezobrazí.<br /><br /> Projekt z prvního řešení se zobrazí jako nedostupný.|

## <a name="see-also"></a>Viz také
- [Testovací příručka pro moduly plug-in správy zdrojového kódu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
