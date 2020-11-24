---
title: Vytvoření nastavení testu pro distribuovaný zátěžový test
description: Naučte se konfigurovat nastavení testu pro zátěžové testy, abyste mohli distribuovat tyto testy napříč více počítači pomocí testovacích agentů a testovacích kontrolérů.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b52fad24cf0772099e619b08ad877bae891365c3
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439963"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Postupy: vytvoření souboru nastavení testu pro distribuovaný zátěžový test

Nakonfigurujte *nastavení testu* pro zátěžové testy, abyste mohli distribuovat tyto testy napříč více počítači pomocí testovacích agentů a testovacích kontrolérů. Můžete také nakonfigurovat nastavení testu pro použití *adaptérů diagnostických dat*, které určují typy dat, která chcete shromažďovat, nebo jak ovlivnit testovací počítače při spuštění testů zatížení ze sady Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete například použít adaptér diagnostiky dat profileru ASP.NET ke shromáždění rozpisu výkonu kódu. Kromě toho je možné pomocí adaptérů diagnostických dat simulovat potenciální slabá místa na testovacím počítači nebo snížit dostupnou systémovou paměť.

Nastavení testu pro Visual Studio jsou uložená v souboru. Nastavení testu definuje následující informace o jednotlivých rolích:

- Sada rolí, které jsou požadovány pro vaši aplikaci v rámci testu

- Role, která se má použít ke spuštění testů

- Adaptéry diagnostických dat, které se mají použít pro každou roli

Při spuštění testů vyberte nastavení testu, které chcete použít jako aktivní nastavení testu v závislosti na tom, co požadujete pro konkrétní testovací běh. Soubor nastavení testu je uložen jako součást řešení. Název souboru má příponu *. testsettings*.

Když přidáte projekt testů výkonnosti webu a zatížení do řešení, je vytvořen soubor *Default. testsettings* . Soubor je automaticky přidán do řešení ve složce **položky řešení** . Tento soubor spustí testy lokálně bez adaptérů diagnostických dat. Můžete přidat další soubor *. testsettings* nebo upravit soubor *. testsettings* pro určení adaptérů diagnostických dat a řadičů testů.

Kontroler testů bude mít agenty, které lze použít pro každou roli v nastavení testu. Další informace o testovacích kontrolérech a testovacích agentech naleznete v tématu [Správa testovacích kontrolérů a testovacích agentů v aplikaci Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Pomocí těchto kroků můžete vytvořit a odebrat nastavení testu ve vašem řešení pro zátěžové testy, které chcete spustit ze sady Visual Studio.

## <a name="create-a-test-settings-file"></a>Vytvořit soubor s nastavením testu

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na **položky řešení**, přejděte na **Přidat** a pak zvolte **Nová položka**.

     Zobrazí se dialogové okno **Přidat novou položku**.

2. V podokně **Nainstalované šablony** vyberte možnost **nastavení testu**.

3. Volitelné V poli **název** změňte název souboru nastavení testu.

4. Klikněte na tlačítko **Přidat**.

     Nový soubor nastavení testu se zobrazí v **Průzkumník řešení** ve složce **položky řešení** .

5. Zobrazí se dialogové okno **nastavení testu** . Je vybrána stránka **Obecné** .

     Nyní můžete upravit a uložit hodnoty nastavení testu.

6. Do pole **název** zadejte název nastavení testu.

7. Volitelné V části **Popis** zadejte popis nastavení testu tak, aby ostatní členové týmu věděli, k čemu je určena.

8. Volitelné Pokud chcete pro testovací běhy vybrat výchozí schéma pojmenování, vyberte **výchozí schéma pojmenování**. Chcete-li definovat vlastní schéma pojmenování, vyberte **uživatelsky definované schéma** a potom zadejte požadovaný text v **textu předpony**. Chcete-li k názvu testovacího běhu připojit datum a časové razítko, vyberte možnost **připojit datum a časové razítko**.

9. Vyberte **role**.

     Zobrazí se stránka **role** .

     ![Role nastavení testu](../test/media/load_testtestrole.png)

10. Chcete-li spustit testy vzdáleně nebo spustit testy vzdáleně a shromažďovat data vzdáleně, použijte rozevírací seznam **Metoda spuštění testu** a vyberte **vzdálené spuštění**.

11. Pomocí rozevíracího seznamu **řadič** vyberte řadič testu pro testovací agenty z **kontroleru** , který se použije ke spuštění testů nebo shromažďování dat.

    > [!NOTE]
    > Pokud přidáváte řadič poprvé, nebudou v rozevíracím seznamu uvedeny žádné řadiče. Seznam je vyplněn předchozími řadiči, které jste zadali v jiných nastaveních testu. Do pole musíte zadat název kontroleru (například **TestControllerMachine1**).

12. Chcete-li přidat role, které chcete použít ke spuštění testů a sběru dat, klikněte v části **role** na možnost **Přidat**.

13. Do sloupce **název** zadejte název role. Role může být například "webový server".

14. Opakováním kroků 12 a 13 přidejte všechny požadované role.

     Každá role používá testovacího agenta, který je spravován testovacím kontrolérem.

15. Vyberte roli, pro kterou chcete spustit testy, a pak zvolte možnost **nastavit jako roli pro spouštění testů**.

    > [!IMPORTANT]
    > Další role, které vytvoříte a definujete, nebudou spouštět testy, ale budou použity pouze ke sběru dat podle dat a diagnostických adaptérů zadaných pro role na stránce **data a diagnostika** .

16. Chcete-li omezit agenty, které lze použít pro roli, vyberte roli a pak zvolte možnost **Přidat** na panelu nástrojů v části **atributy agenta pro vybranou roli**.

     Zobrazí se dialogové okno **pravidlo výběru agenta** .

     Zadejte název do pole **název atributu** a hodnota v poli **hodnota atributu** a pak zvolte **OK**. Přidejte tolik atributů, kolik budete potřebovat.

     Můžete například přidat atribut s názvem "RAM > 16GB", který má hodnotu "true" nebo "false", chcete-li filtrovat počítače testovacího agenta, které mají více než 16GB paměti. Chcete-li použít stejný atribut pro jeden nebo více testovacích agentů, použijte dialogové okno **spravovat Test Controller** . Další informace najdete v tématu [Správa testovacích kontrolérů a testovacích agentů pomocí sady Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Vyberte **data a diagnostiku**.

     Zobrazí se stránka **data a diagnostika** .

     ![Data a diagnostika nastavení testu](../test/media/load_testtest.png)

18. Na stránce **data a diagnostika** definujete význam role výběrem *adaptérů diagnostických dat* , které bude role používat ke shromažďování dat. Proto pokud je jeden nebo více datových a diagnostických adaptérů pro roli povolený, kontroler testů vybere dostupný počítač testovacího agenta pro shromažďování dat pro zadaná data a diagnostické adaptéry na základě atributů, které jste pro tuto roli definovali. Pokud chcete vybrat adaptéry dat a diagnostiky dat, které chcete shromažďovat pro každou roli, vyberte roli. Pro každou roli vyberte adaptéry diagnostických dat podle potřeb testů. Chcete-li nakonfigurovat všechny adaptéry diagnostických dat, které jste vybrali pro každou roli, vyberte možnost **Konfigurovat**.

     **Příklad rolí a adaptérů diagnostických dat:**

     Můžete například vytvořit roli klienta s názvem "Desktop Client" s atributem "používá SQL" nastaveným na hodnotu "true" a roli serveru s názvem "SQL Server" s atributem nastaveným na "RAM > 16GB". Pokud určíte, že "klient pro stolní počítače" spustí testy výběrem možnosti **nastavit jako roli pro spouštění testů** na stránce **role** , kontroler testů vybere počítače s testovacími agenty, které obsahují atribut "používá SQL" nastaven na hodnotu "pravda", na které se mají testy spouštět. Kontroler testů také vybere počítače se systémem SQL Server s testovacími agenty, které obsahují atribut "RAM > 16GB" pouze ke shromažďování dat definovaných pomocí dat a diagnostických adaptérů zahrnutých v roli. Testovací agent "klient pro stolní počítače" může také shromažďovat data pro počítače, na kterých je spuštěno, pokud vyberete možnost data a diagnostické adaptéry pro tuto roli.

     Podrobnosti o jednotlivých adaptérech diagnostiky dat a o tom, jak je nakonfigurovat, najdete v příslušném tématu v následující tabulce.

     Další informace o adaptérech diagnostických dat naleznete v tématu [shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md).

     **Adaptéry diagnostických dat pro zátěžové testy**

    |Adaptér diagnostiky dat|Použití v zátěžových testech|Přidružené téma|
    |-|-------------------------|-|
    |**ASP.NET klientského proxy serveru pro IntelliTrace a dopad testu:** Tento proxy server umožňuje shromažďovat informace o voláních http z klienta na webový server pro adaptéry diagnostických dat IntelliTrace a test vlivu.|![Informační ikona](../test/media/vc364f4.gif)<br /><br /> Pokud nemáte konkrétní potřebu shromažďovat systémové informace pro počítače testovacího agenta, tento adaptér nezahrnujte. **Upozornění:**  Nedoporučujeme používat adaptér IntelliTrace v zátěžových testech z důvodu problémů, ke kterým dochází kvůli velkému množství shromažďovaných dat. <br /><br /> Data dopadu testu nejsou shromažďována pomocí zátěžových testů.||
    |**IntelliTrace:** Můžete nakonfigurovat konkrétní informace o trasování diagnostiky, které jsou uloženy v souboru protokolu. Soubor protokolu má příponu *. TDLOG*. Když spustíte test a testovací krok neproběhne úspěšně, můžete vytvořit chybu. Soubor protokolu, který obsahuje diagnostické trasování, je automaticky připojen k této chybě. Data, která jsou shromažďována v souboru protokolu, zvyšují produktivitu ladění tím, že zkracuje dobu potřebnou k reprodukování a diagnostice chyby v kódu. Z tohoto souboru protokolu lze místní relaci znovu vytvořit v jiném počítači. Tím se snižuje riziko, že chybu nelze reprodukovat.<br /><br /> Další informace najdete v tématu [shromáždění IntelliTrace dat](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Ikona Důležité](../test/media/vc364f3.gif)<br /><br /> Nedoporučujeme používat adaptér IntelliTrace v zátěžových testech z důvodu problémů, ke kterým dochází kvůli velkému množství shromažďovaných dat a jejich zaznamenávání. Měli byste se pokusit použít adaptér IntelliTrace pouze v zátěžových testech, které neběží dlouho a nepoužívají mnoho testovacích agentů.|[Postupy: shromáždění dat IntelliTrace, která vám pomůžou ladit obtížné problémy](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**Profiler ASP.NET:** Můžete vytvořit nastavení testu, které zahrnuje profilování ASP.NET, které shromažďuje údaje o výkonu pro webové aplikace v ASP.NET.|Adaptér diagnostiky dat profileru ASP.NET profiluje proces Internetová informační služba (IIS), takže nebude fungovat na vývojovém webovém serveru. Chcete-li profilovat web v rámci zátěžového testu, je nutné nainstalovat testovacího agenta na počítači, ve kterém je služba IIS spuštěna. Testovací agent nebude generovat zátěž, ale bude to jenom agent s kolekcí. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).|[Postupy: Konfigurace profileru ASP.NET pro zátěžové testy s využitím nastavení testu](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Protokol událostí:** Můžete nakonfigurovat nastavení testu tak, aby zahrnovalo shromažďování protokolů událostí, které budou zahrnuty do výsledků testu.||[Postupy: Konfigurace shromažďování protokolů událostí pomocí nastavení testu](/previous-versions/dd504816(v=vs.110))|
    |**Emulace sítě:** Můžete určit, že chcete do testu umístit umělé zatížení sítě pomocí nastavení testu. Emulace sítě má vliv na komunikaci do a z počítače tím, že emuluje konkrétní rychlost síťového připojení, například telefonické připojení. **Poznámka:**  K zvýšení rychlosti síťového připojení nelze použít emulaci sítě.|Adaptér emulace sítě je ignorován testy zatížení. Místo toho testy zatížení používají nastavení, která jsou uvedena v síťové kombinaci scénáře zátěžového testu.<br /><br /> Další informace najdete v tématu [Určení typů virtuálních sítí](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Systémové informace:** Nastavení testu lze nastavit tak, aby obsahovalo systémové informace o počítačích, na kterých je spuštěná Diagnostika systémových informací a kolekce dat. Systémové informace jsou zadány ve výsledcích testu pomocí nastavení testu.|![Informační ikona](../test/media/vc364f4.gif)<br /><br /> Můžete shromažďovat systémové informace jak z agentů zatížení, tak z testovaného systému.|Ke shromažďování těchto informací není nutná žádná konfigurace.|
    |**Dopad testu:** Můžete shromažďovat informace o metodách kódu vaší aplikace, které byly použity při spuštění testovacího případu. To lze použít společně se změnami v kódu aplikace, které vývojáři provádějí k určení, které testy byly ovlivněny změnami vývoje.|Data dopadu testu nejsou shromažďována s testy zatížení.||
    |**Záznam videa:** Můžete vytvořit záznam videa relace plochy při spuštění automatizovaného testu. To může být užitečné k zobrazení akcí uživatele pro programový test uživatelského rozhraní. Video může pomáhat ostatním členům týmu izolovat problémy s aplikacemi, které se obtížně reprodukovaly. **Poznámka:**  Při vzdáleném spuštění testů nebude záznam videa fungovat, pokud Agent nebude spuštěn v režimu interaktivního procesu.|![Důležitá ikona ](../test/media/vc364f3.gif) **Upozornění:**  nedoporučujeme používat adaptér zapisovače videa pro zátěžové testy.|[Postupy: zahrnutí záznamů obrazovky a hlasu během testů pomocí nastavení testu](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Vyberte **nasazení**.

     Zobrazí se stránka **nasazení** .

20. Chcete-li vytvořit samostatný adresář pro nasazení pokaždé, když spustíte testy, vyberte možnost **Povolit nasazení**.

    > [!NOTE]
    > Pokud to uděláte, můžete pokračovat v sestavování aplikace při spuštění testů.

21. Chcete-li přidat soubor do adresáře, který používáte ke spuštění testů, zvolte možnost **Přidat soubor** a potom vyberte soubor, který chcete přidat.

    > [!NOTE]
    > Při spuštění testů zatížení jsou automaticky nasazena sestavení modulů plug-in, datové soubory a nahrané soubory.

22. Chcete-li přidat adresář do adresáře, který používáte ke spuštění testů, zvolte možnost **Přidat adresář** a potom vyberte adresář, který chcete přidat.

23. Chcete-li spustit skripty před a po testech, vyberte možnost **instalační a čisticí skripty**.

     Zobrazí se stránka pro **nastavení a vyčištění skriptů** .

    1. Zadejte umístění souboru skriptu ve **skriptu instalace** nebo vyberte tři tečky (**...**) a vyhledejte instalační skript.

    2. Zadejte umístění souboru skriptu do **skriptu pro vyčištění** nebo vyberte tři tečky (**...**) a vyhledejte skript pro vyčištění.

24. Chcete-li spustit testy pomocí jiného hostitele, vyberte možnost **hostitelé**.

    1. V poli **typ hostitele** ověřte, zda je vybrána možnost **výchozí** .

        > [!NOTE]
        > **ASP.NET** v **typu hostitele** není v zátěžových testech podporován.

    2. Pomocí rozevíracího seznamu **Spustit test v 32 nebo 64** zvolte, zda chcete spustit testy webového výkonu a jednotky v zátěžovém testu jako 32-bitové 64 nebo 16bitové procesy.

        > [!NOTE]
        > Pro maximální flexibilitu byste měli kompilovat projekty webového výkonu a zátěžového testu pomocí libovolné konfigurace **procesoru** . Pak můžete spustit na 32 i 64 bitových agentů. Kompilace projektů výkonnosti webu a zátěžového testu pomocí **64** konfigurace nenabízí žádnou výhodu.

25. Volitelné Chcete-li omezit čas pro každý testovací běh a jednotlivé testy, vyberte **časový limit testu.**

    1. Pokud chcete přerušit testovací běh při překročení časového limitu, vyberte možnost **přerušit testovací běh, pokud celková doba překročí** , a pak zadejte hodnotu pro toto omezení.

    2. Pro selhání individuálního testu při překročení časového limitu vyberte **Označit jednotlivý test jako neúspěšný, pokud doba běhu překročí** a zadejte hodnotu pro toto omezení.

26. Přeskočit **test jednotek** Zátěžové testy nepoužívají tato nastavení.

27. Přeskočit **webový test** Zátěžové testy nepoužívají tato nastavení.

28. Chcete-li uložit nastavení testu, vyberte možnost **Uložit jako**. Zadejte název souboru, který chcete v **názvu objektu**.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Odebrání souboru nastavení testu z řešení

Ve složce **položky řešení** v **Průzkumník řešení** klikněte pravým tlačítkem myši na nastavení testu, které chcete odebrat, a poté zvolte možnost **Odebrat**.

Soubor nastavení testu se odebere z vašeho řešení.

## <a name="see-also"></a>Viz také

- [Kontrolery testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md)
- [Shromažďování diagnostických informací pomocí nastavení testu](../test/collect-diagnostic-information-using-test-settings.md)