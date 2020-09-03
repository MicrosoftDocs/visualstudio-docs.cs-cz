---
title: Správa kontrolerů testů a testovacích agentů
ms.date: 09/18/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78bd0143ee2584bcabb5e8ed4946818ee2590789
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286697"
---
# <a name="manage-test-controllers-and-test-agents"></a>Správa kontrolerů testů a testovacích agentů

Pokud chcete použít aplikaci Visual Studio ke vzdálenému spuštění testů, distribuovat testy mezi více počítači nebo spustit zátěžové testy, je nutné nakonfigurovat testovací kontrolér, testovací agenty a soubor nastavení testu. Toto téma popisuje, jak spravovat testovací kontroléry a testovací agenty poté, co je nainstalujete a nakonfigurujete poprvé.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Pokud používáte Microsoft Test Manager ke spuštění testů v testovacích prostředích, můžete spravovat testovací kontroléry a jejich agenty pomocí **Test Controller Manageru** v **testovacím centru** pro Microsoft Test Manager. Toto téma je použitelné pouze v případě, že používáte aplikaci Visual Studio ke spuštění testů.
::: moniker-end

Informace o instalaci a konfiguraci testovacích agentů a testovacích kontrolérů pro spuštění testů v aplikaci Visual Studio naleznete v tématu [Configure test Agents and Controllers](../test/configure-test-agents-and-controllers-for-load-tests.md).

Chcete-li nakonfigurovat a monitorovat testovací kontrolér a všechny registrované agenty, musíte mít soubor nastavení testu v testovacím projektu, který obsahuje testy, které chcete spustit. Otevřete soubor nastavení testu, vyberte **role** a v rozevíracím seznamu pro pole **Controller** vyberte **Spravovat testovací kontroléry** .

V případě projektu zátěžového testu můžete také zvolit možnost **Spravovat testovací kontroléry** z nabídky **zátěžový test** .

## <a name="add-a-test-agent-to-a-test-controller"></a>Přidání testovacího agenta do testovacího kontroléru

Můžete chtít přidat testovacího agenta k jinému testovacímu kontroleru nebo může být nutné přidat testovacího agenta k testovacímu kontroléru, který jste právě nainstalovali.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Přidání testovacího agenta do testovacího kontroléru

1. Vyberte možnost **Spustit**  >  **Nástroj pro konfiguraci testovacího agenta**.

     Zobrazí se dialogové okno **konfigurovat testovacího agenta** .

    > [!NOTE]
    > Abyste mohli přidat testovacího agenta do testovacího kontroléru, je nutné, aby byl již nainstalován. Další informace o tom, jak nainstalovat testovacího agenta, najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

2. Máte k dispozici dvě možnosti, jak lze spustit testovacího agenta:

   - **Služba**: Pokud nemusíte spouštět automatizované testy, které spolupracují s plochou, jako jsou programové testy uživatelského rozhraní nebo vytváření záznamu videa při spuštění testu, v části **spustit testovacího agenta jako**vyberte **Služba**. Testovací agent bude spuštěn jako služba. Zvolte **Další**.

      Nyní můžete zadat podrobné informace o uživateli, když se testovací agent spustí jako služba.

      1. Zadejte název do pole **uživatelské jméno**.

      2. Do pole **heslo**zadejte heslo.

        |**Důležité informace o uživatelském účtu**|
        |-|
        |– Hesla s hodnotou null nejsou pro uživatelské účty podporována.|
        |– Pokud chcete použít kolektor IntelliTrace nebo emulaci sítě, musí být uživatelský účet členem skupiny Administrators.|
        |– Pokud uživatelské jméno agenta není ve službě agenta, pokusí se ho přidat, což vyžaduje oprávnění k testovacímu kontroléru.|
        |– Uživatel, který se pokouší použít testovací kontrolér, musí být v účtu uživatele testovacího kontroléru nebo nebude moci spustit testy na řadiči.|

   - **Interaktivní proces**: Pokud chcete spustit automatizované testy, které musí komunikovat s plochou, jako jsou kódované testy uživatelského rozhraní nebo vytváření záznamu videa, když test běží, vyberte **interaktivní proces**. Testovací agent bude spuštěn jako interaktivní proces namísto služby.

      Na další stránce zadejte podrobné informace o uživateli, když se testovací agent spustí jako proces, a další možnosti.

      1. Zadejte název do pole **uživatelské jméno**.

      2. Do pole **heslo**zadejte heslo.

        > [!NOTE]
        > Pokud nakonfigurujete testovacího agenta tak, aby běžel jako interaktivní proces s jiným uživatelem, který není aktuálně aktivním uživatelem, je nutné restartovat počítač a přihlásit se jako tento jiný uživatel, aby bylo možné agenta spustit. Kromě toho se u uživatelských účtů nepodporují hesla s hodnotou null. Pokud chcete použít kolektor IntelliTrace nebo emulaci sítě, musí být uživatelský účet členem skupiny Administrators.

      3. Chcete-li se ujistit, že počítač s testovacím agentem může po restartu spustit testy, můžete nastavit počítač pro automatické přihlášení jako testovací agent. Vyberte **automaticky přihlásit**se. Tím se uživatelské jméno a heslo uloží do šifrovaného formuláře v registru.

      4. Chcete-li se ujistit, že je spořič obrazovky zakázán, protože to může narušit všechny automatizované testy, které musí s plochou pracovat, vyberte možnost **zkontrolovat, zda je spořič obrazovky zakázán**.

        > [!WARNING]
        > Pokud se přihlašujete automaticky nebo zakážete šetřič obrazovky, dojde k bezpečnostnímu riziku. Povolením automatického přihlášení povolíte ostatním uživatelům spustit tento počítač a budete moci používat účet, který se automaticky přihlašuje. Pokud vypnete šetřič obrazovky, počítač nemusí vyzvat uživatele k přihlášení, aby mohl počítač odemknout. To umožňuje komukoli přístup k počítači, pokud mají fyzický přístup k počítači. Pokud tyto funkce povolíte v počítači, měli byste se ujistit, že tyto počítače jsou fyzicky zabezpečené. Například tyto počítače se nacházejí ve fyzicky zabezpečeném testovacím prostředí. (Pokud zrušíte zaškrtnutí políčka **Ujistěte se, že je spořič obrazovky zakázaný**, nepovolíte spořič obrazovky.)

3. Chcete-li zaregistrovat tohoto agenta s jiným řadičem testu, vyberte možnost **registrovat v rámci kontroleru testů.** Zadejte název kontroleru testů následovaný **:** a číslem portu, který používáte v **registraci testovacího agenta s následujícím testovým kontrolérem**. Zadejte například **obdrží agent1:6901**.

    > [!NOTE]
    > Výchozí číslo portu je 6901.

4. Pokud chcete změny uložit, vyberte **použít nastavení**. Zavřete dialogové okno **Souhrn konfigurace** a potom zavřete **Nástroj pro konfiguraci testovacího agenta**.

> [!WARNING]
> Pokud je agent aktuálně nakonfigurován tak, aby běžel na jiném kontroleru testů, je nutné odebrat testovacího agenta z tohoto kontroleru.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Odebrat testovacího agenta z kontroleru testů

Testovací agent musí být nastaven do stavu offline, aby jej bylo možné odebrat.

::: moniker range="vs-2017"
> [!NOTE]
> Tento postup nemůžete použít k odebrání agentů registrovaných na řadiči jako součást testovacího prostředí. Chcete-li odebrat tyto agenty z kontroleru, je nutné prostředí odebrat pomocí Microsoft Test Manager.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Tento postup nemůžete použít k odebrání agentů registrovaných na řadiči jako součást testovacího prostředí.
::: moniker-end

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Odebrání testovacího agenta z kontroleru testů

::: moniker range=">=vs-2019"
V aplikaci Visual Studio 2019 nelze odebrat testovacího agenta, pokud je testovací kontrolér zaregistrován v projektu.
::: moniker-end
Pokud kontroler testů není zaregistrován u projektu, postupujte podle těchto kroků.

1. V aplikaci Visual Studio otevřete soubor nastavení testu pro projekt testů, vyberte možnost **role** a v rozevíracím seznamu pro pole **Controller** vyberte možnost **Spravovat testovací kontroléry** .

   Zobrazí se dialogové okno **spravovat Test Controller** .

2. V rozevíracím seznamu **kontrolér** zadejte název počítače, na kterém jste nastavili kontroler testů. Pokud jste dříve pomohli spravovat konkrétní kontroler testů, můžete název vybrat ze seznamu.

3. V podokně **agenti** vyberte název testovacího agenta. Pokud je agent stále online, vyberte možnost **offline.** Pokud ho chcete odebrat, klikněte na **Odebrat**.

   > [!NOTE]
   > Odebrání testovacího agenta stačí zrušit jeho přidružení od kontroleru testů. Chcete-li kompletně odinstalovat testovacího agenta, použijte ovládací panel  **programy a funkce** v počítači testovacího agenta.

::: moniker range="vs-2017"
Pokud je testovací kontrolér zaregistrován v projektu, odeberte agenta pomocí Microsoft Test Manager.
::: moniker-end

## <a name="change-the-settings-for-a-test-agent"></a>Změna nastavení pro testovacího agenta

Stav agenta testu může mít jednu z následujících hodnot:

|Status|Popis|
|-|-----------------|
|Spuštění testu|Spouštění testů|
|Připraveno|K dispozici pro spuštění testů nebo shromažďování dat a diagnostiky|
|Offline|K dispozici pro spuštění testů nebo shromažďování dat a diagnostiky|
|Propojení|Testovací agent není spuštěný.|

Můžete změnit stav a další nastavení testovacího agenta pomocí následujících postupů.

### <a name="to-change-the-settings-of-a-test-agent"></a>Změna nastavení testovacího agenta

::: moniker range="vs-2017"
> [!NOTE]
> Pokud je testovací agent zaregistrován pro testovací kontrolér, který je zaregistrován v projektu, změňte nastavení v Microsoft Test Manager.
::: moniker-end

1. Chcete-li nakonfigurovat a monitorovat testovací kontrolér a všechny registrované agenty pro zátěžový test, zvolte nabídku **zátěžový test** v aplikaci Visual Studio a pak zvolte možnost **Spravovat testovací kontroléry**. Pro všechny ostatní testy otevřete soubor nastavení testu pro projekt testů v aplikaci Visual Studio, vyberte možnost **role** a v rozevíracím seznamu pro pole **Controller** vyberte možnost **Spravovat testovací kontroléry** .

   Otevře se dialogové okno **spravovat Test Controller** .

1. Vyberte název kontroleru testů, jehož testovací agenty chcete změnit v seznamu kontroleru testů. Pokud se řadič testů v seznamu nezobrazí, zkontrolujte, zda je testovací kontrolér správně zaregistrován. Další informace najdete v následujícím postupu, jak nakonfigurovat testovací kontrolér.

1. Volitelné V podokně **testovací agenti** vyberte počítač testovacího agenta, pro který chcete změnit vlastnosti.

1. Zvolte **Properties** (Vlastnosti).

1. Změňte následující vlastnosti testovacího agenta podle potřeby:

|Vlastnost testovacího agenta|Popis|
|-|-----------------|
|**Váhu**|Používá se k distribuci zatížení při použití testovacích agentů s různými úrovněmi výkonu. Například testovací agent s vážením 100 obdrží dvakrát zatížení jako testovací agent s vážením 50.|
|**Přepínání IP**|Slouží ke konfiguraci přepínání protokolu IP. Přepínání IP umožňuje testovacímu agentovi odesílat požadavky na server pomocí rozsahu IP adres. To simuluje volání, která pocházejí z různých klientských počítačů.<br /><br /> Přepínání IP je důležité, pokud zátěžový test přistupuje k webové farmě. Většina nástrojů pro vyrovnávání zatížení vytváří spřažení mezi klientem a konkrétním webovým serverem pomocí IP adresy klienta. Pokud se všechny požadavky zdají vypadat jako z jednoho klienta, nástroj pro vyrovnávání zatížení nebude zatížení vyrovnávat. Chcete-li dosáhnout správného vyrovnávání zatížení ve webové farmě, ujistěte se, že požadavky pocházejí z rozsahu IP adres. **Poznámka:**  Můžete určit síťový adaptér nebo použít **(všechny nepřiřazené)** k automatickému výběru toho, který aktuálně není používán. <br /><br /> Chcete-li použít funkci přepínání protokolu IP, musí být služba Visual Studio Test Agent spuštěna jako uživatel ve skupině Administrators pro daný počítač agenta. Tento uživatel je vybraný při instalaci agenta, ale můžete ho změnit úpravou vlastností služby a restartováním.<br /><br /> Chcete-li ověřit, zda funkce přepínání IP funguje správně, povolte protokolování služby IIS na webovém serveru, pomocí funkce protokolování služby IIS ověřte, zda požadavky pocházejí z IP adres, které jste nakonfigurovali.|
|**Atributy**|Sada párů název/hodnota, které lze použít ve výběru testovacího agenta. Test může například vyžadovat konkrétní operační systém. Můžete přidat atributy na kartě **role** v souboru nastavení testu a lze je použít k výběru testovacího agenta, který má odpovídající atributy. Pokud chcete spustit test na více počítačích, vytvořte atribut v roli nastavení testu, která je nakonfigurována pro spuštění testů, a poté nakonfigurujte odpovídající atribut pro každého testovacího agenta, který chcete v této roli použít.. **Poznámka:**  Toto nastavení je k dispozici pouze pro testovací agenty, kteří jsou registrováni s testovacím kontrolérem, který není registrován v projektu, protože tyto atributy se používají pouze v nastaveních testu pro aplikaci Visual Studio.|

Výsledek testovacího agenta a změny atributu testovacího agenta se projeví okamžitě, ale neovlivňují testy, které jsou spuštěny. Rozsah IP adres se projeví po restartování kontroleru testů.

Volitelné Chcete-li změnit stav testovacího agenta, vyberte v seznamu agenta a pak vyberte akci z dostupných možností na základě aktuálního stavu agenta.

> [!NOTE]
> Pokud je testovací agent spuštěn jako proces, spravujte stav testovacího agenta z ikony oznamovací oblasti, která je spuštěna v počítači, kde je nainstalován testovací agent. Zobrazuje stav testovacího agenta. Můžete spustit, zastavit nebo restartovat agenta, pokud je spuštěn jako proces pomocí tohoto nástroje.

## <a name="configure-a-test-controller"></a>Konfigurace kontroleru testů

Chcete-li nakonfigurovat testovací kontrolér, je nutné použít **Nástroj pro konfiguraci kontroleru Team test**. Při konfiguraci kontroleru testů můžete zaregistrovat testovací kontrolér s jinou kolekcí projektu nebo zrušit registraci testovacího kontroléru z kolekce projektu.

Pokud chcete zaregistrovat kontroler testů pomocí kolekce projektu Team Foundation Server, účet, který používáte pro službu testovacího kontroléru, musí být členem skupiny účtů služeb testování kolekce projektů pro kolekci projektu, nebo účet, který použijete ke spuštění nástroje pro konfiguraci testovacího kontroléru, musí být správce kolekce projektu.

> [!NOTE]
> Pokud zrušíte registraci testovacího kontroléru z kolekce projektu, která obsahuje existující prostředí v kolekci projektu, prostředí jsou stále udržována, pokud jste tuto kolekci projektů přesunuli a znovu zaregistrovali řadič testu na tuto přesunutou kolekci projektů.

### <a name="to-configure-a-test-controller"></a>Konfigurace kontroleru testů

1. Chcete-li spustit nástroj a kdykoli znovu nakonfigurovat testovací kontrolér, klikněte na tlačítko **Spustit**  >  **Nástroj pro konfiguraci Test Controller**.

     Zobrazí se dialogové okno **konfigurace Test Controller** .

2. Vyberte uživatele, který chcete použít jako přihlašovací účet pro službu testovacího kontroléru.

    > [!NOTE]
    > Hesla s hodnotou null nejsou pro uživatelské účty podporována.

4. Volitelné Pokud nechcete použít testovací kontrolér s testovacím prostředím, ale pouze ke spuštění testů ze sady Visual Studio, zrušte zaškrtnutí políčka **Registrovat Test Controller s kolekcí týmových projektů**.

5. Volitelné Chcete-li nakonfigurovat testovací kontrolér pro zátěžové testování, vyberte možnost **Konfigurovat kontroler testů pro zátěžové testování**. Zadejte instanci SQL Server v části **vytvořit databázi výsledků zátěžového testu v následující instanci SQL Server**.

> [!NOTE]
> Další potíže s vyhledáním informací o testovacích kontrolérech najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Spravovat agenty při spuštění testů s testovacím kontrolérem

Při přidávání rolí pro aplikaci do nastavení testu pro sadu Visual Studio můžete přidat vlastnosti agenta pro každou z vašich rolí. Tím se určuje, které testovací agenti jsou k dispozici pro tuto roli. Při spuštění testů pomocí těchto nastavení testu určuje kontroler testů, který je vybrán pro nastavení testu, dostupnost požadovaných agentů. V těchto situacích se může stát, když se zjistí dostupnost agenta:

- Pro roli, která musí spustit testy, není k dispozici žádný agent. Testy nelze spustit. Můžete provést jednu z následujících akcí a pak znovu spustit testy:

  - Můžete počkat, až bude agent k dispozici pro tuto roli pro spuštění testů.

  - Pokud existují agenti, kteří jsou v režimu offline a lze je použít pro tuto roli, můžete agenta restartovat, aby byl k dispozici.

  - Do kontroleru testů můžete přidat jiného agenta se správnými vlastnostmi agenta pro tuto roli.

  - Můžete změnit vlastnosti agenta pro tuto roli v nastavení testu pro povolení jiných agentů, které chcete použít.

- Pro jednu nebo více rolí, které spouštějí adaptéry diagnostických dat, není k dispozici žádný agent. Testy lze spustit, ale adaptér diagnostických dat nelze spustit. Testy můžete spustit bez adaptéru diagnostických dat, nebo můžete provést jednu z následujících akcí a znovu spustit testy:

  - Můžete počkat, až bude agent pro tyto role k dispozici.

  - Pokud jsou k dispozici jiní agenti, kteří jsou v režimu offline a lze je použít pro tuto roli, je nutné změnit stav agenta na online v nabídce **test** na možnost **Spravovat Test Controller** . Kromě toho může být nutné restartovat agenta, pokud byl odpojen od kontroleru.

  - Ověřte, že žádné agenty, které budete potřebovat pro tento testovací běh, nejsou zaneprázdněné spouštěním testů. Ve **správě Test Controller** v nabídce **test** můžete zkontrolovat stav všech agentů.

  - Do kontroleru testů můžete přidat jiného agenta se správnými vlastnostmi agenta pro danou roli.

  - Můžete změnit vlastnosti agenta pro roli v nastavení testu pro povolení jiných agentů, které chcete použít.

## <a name="load-tests-from-delay-signed-assemblies"></a>Zátěžové testy ze sestavení se zpožděným podpisem

Testovací kontrolér a testovací agenti mohou načíst pouze testovací sestavení, která jsou silně podepsaná sestavení nebo nepodepsaná sestavení. Některá testovací sestavení jsou podepsána opožděně, protože musí mít přístup k produkčním sestavením aplikace. Tato sestavení však nejsou silně podepsána, protože jsou pouze testovací sestavení a nejsou distribuována. Tato sestavení nelze načíst, protože jsou podepsané se zpožděním, takže je nutné zakázat ověřování silných názvů pro tato sestavení ve všech počítačích, kde bude sestavení načteno včetně počítače testovacího kontroléru. K zakázání ověřování podepsaného zpožděním použijte *sn.exe*. Token veřejného klíče sestavení se zpožděným podpisem, pro který je požadováno přeskočení ověřování silným názvem, může být také nutné zahrnout.

K zakázání ověřování podepsaného zpoždění použijte *Sn.exe* (nástroj Strong Name).

Tím se zakáže ověřování se silným názvem pouze pro zadané sestavení v počítači, na kterém příkaz spustíte. To lze provést pouze v případě, že máte dostatečná oprávnění.

Po dokončení testovacího běhu znovu povolte ověřování opožděným podepsáním pomocí příkazu *SN.exe* .

Doporučený způsob, jak zakázat a znovu povolit ověřování podepisování, je použití příkazů *SN.exe* ve skriptech. Ověřování můžete zakázat v instalačním skriptu a znovu povolit ověřování ve skriptu pro vyčištění.

## <a name="see-also"></a>Viz také

- [Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md)
