---
title: Ladění kódu Pythonu na vzdálených počítačích s Linuxem
description: Pomocí sady Visual Studio můžete ladit kód Pythonu spuštěný ve vzdálených počítačích s Linuxem, včetně nezbytných kroků konfigurace, zabezpečení a řešení potíží.
ms.date: 12/06/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e718a5610d9539e3e2a89af0a9de502ebfd168a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62962522"
---
# <a name="remotely-debug-python-code-on-linux"></a>Vzdálené ladění kódu Pythonu v Linuxu

Visual Studio může spouštět a ladit aplikace Pythonu místně a vzdáleně v počítači se systémem Windows (viz [Vzdálené ladění).](../debugger/remote-debugging.md) Může také ladit vzdáleně na jiný operační systém, zařízení nebo Python implementace než CPython pomocí [knihovny ptvsd](https://pypi.python.org/pypi/ptvsd).

Při použití ptvsd, kód Pythonu, který je laděn, hostuje ladicí server, ke kterému se může aplikace Visual Studio připojit. Tento hosting vyžaduje malou změnu kódu pro import a povolení serveru a může vyžadovat konfiguraci sítě nebo brány firewall ve vzdáleném počítači, aby bylo možné povolit připojení TCP.

|   |   |
|---|---|
| ![ikona filmové kamery pro video](../install/media/video-icon.png "Podívejte se na video") | Úvod do vzdáleného ladění najdete [v tématu Deep Dive: Vzdálené ladění napříč platformami](https://youtu.be/y1Qq7BrV6Cc) (youtube.com, 6m22s), které je použitelné pro Visual Studio 2015 a 2017. |

## <a name="set-up-a-linux-computer"></a>Nastavení počítače s Linuxem

Následující položky jsou potřebné pro tento návod:

- Vzdálený počítač se systémem Python v operačním systému, jako je Mac OSX nebo Linux.
- Port 5678 (příchozí) byl otevřen v bráně firewall tohoto počítače, což je výchozí pro vzdálené ladění.

[Virtuální počítač S Linuxem](/azure/virtual-machines/linux/creation-choices) můžete snadno vytvořit v Azure a [přistupovat k němu pomocí vzdálené plochy](/azure/virtual-machines/linux/use-remote-desktop) z Windows. Ubuntu pro Virtuální měje je výhodné, protože Python je ve výchozím nastavení nainstalován; v opačném případě se seznam najdete v seznamu [Instalace interpretu Pythonu podle vašeho výběru](installing-python-interpreters.md) pro další umístění stahování Pythonu.

Podrobnosti o vytvoření pravidla brány firewall pro virtuální počítač Azure najdete v tématu [Otevření portů na virtuální počítač v Azure pomocí portálu Azure](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Příprava skriptu pro ladění

1. Ve vzdáleném počítači vytvořte soubor Pythonu s názvem *guessing-game.py* s následujícím kódem:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. Nainstalujte `ptvsd` balíček do `pip3 install ptvsd`vašeho prostředí pomocí .
   >[!NOTE]
   >Je vhodné zaznamenat verzi ptvsd, která je nainstalována v případě, že ji potřebujete pro řešení potíží; [ptvsd výpis](https://pypi.python.org/pypi/ptvsd) také zobrazuje dostupné verze.

1. Povolte vzdálené ladění přidáním níže uvedeného kódu v nejbližším možném bodě *v guessing-game.py*před jiným kódem. (Ačkoli to není přísný požadavek, není možné ladit všechna vlákna `enable_attach` na pozadí, která byla zplozena před voláním funkce.)

   ```python
   import ptvsd
   ptvsd.enable_attach()
   ```

1. Uložte soubor `python3 guessing-game.py`a spusťte . Volání spustí `enable_attach` na pozadí a čeká na příchozí připojení, jak jinak pracovat s programem. V případě `wait_for_attach` potřeby může být `enable_attach` funkce volána po zablokování programu, dokud se ladicí program nepřipojí.

> [!Tip]
> Kromě `enable_attach` a `wait_for_attach`, ptvsd také poskytuje `break_into_debugger`pomocnou funkci , která slouží jako programová zarážka, pokud je připojen ladicí program. K dispozici `is_attached` je také `True` funkce, která vrátí, pokud ladicí program je připojen (všimněte si, že není nutné zkontrolovat tento výsledek před voláním jiné `ptvsd` funkce).

## <a name="attach-remotely-from-python-tools"></a>Připojení vzdáleně z nástrojů Pythonu

V těchto krocích nastavíme jednoduchou zarážku pro zastavení vzdáleného procesu.

1. Vytvořte kopii vzdáleného souboru v místním počítači a otevřete ji v sadě Visual Studio. Nezáleží na tom, kde je soubor umístěn, ale jeho název by měl odpovídat názvu skriptu ve vzdáleném počítači.

1. (Nepovinné) Chcete-li mít intelliSense pro ptvsd v místním počítači, nainstalujte balíček ptvsd do prostředí Pythonu.

1. Vyberte **možnost Připojit k procesu** > **Attach to Process**.

1. V zobrazeném dialogovém okně **Připojit k procesu** nastavte **typ připojení** na **vzdálené (ptvsd)**. (Ve starších verzích sady Visual Studio se tyto příkazy nazývají **Transport** a **vzdálené ladění Pythonu**.)

1. V poli **Cíl připojení** (**Kvalifikátor** ve starších verzích) `tcp://<ip_address>:5678` zadejte, kde `<ip_address>` je to `:5678` vzdálený počítač (což může být buď explicitní adresa nebo název, jako je myvm.cloudapp.net) a je číslo vzdáleného ladicího portu.

1. Stisknutím **klávesy Enter** naplníte seznam dostupných procesů ptvsd v tomto počítači:

    ![Zadání cíle připojení a výpis procesů](media/remote-debugging-qualifier.png)

    Pokud po vyplnění tohoto seznamu spustíte jiný program ve vzdáleném počítači, vyberte tlačítko **Aktualizovat.**

1. Vyberte proces, který chcete ladit, a potom **připojit**nebo poklepejte na proces.

1. Visual Studio se pak přepne do režimu ladění, zatímco skript bude nadále spuštěn ve vzdáleném počítači a poskytne všechny obvyklé možnosti [ladění.](debugging-python-in-visual-studio.md) Nastavte například zarážku `if guess < number:` na řádku, přepněte do vzdáleného počítače a zadejte jiný odhad. Poté se visual studio v místním počítači zastaví na této zarážky, zobrazí místní proměnné a tak dále:

    ![Visual Studio pozastaví ladění při zásahu zarážky](media/remote-debugging-breakpoint-hit.png)

1. Když zastavíte ladění, Visual Studio odpojí od programu, který pokračuje v běhu ve vzdáleném počítači. ptvsd také pokračuje v poslechu pro připojení ladicích programů, takže můžete znovu připojit k procesu znovu kdykoliv.

### <a name="connection-troubleshooting"></a>Poradce při potížích s připojením

1. Ujistěte se, že jste vybrali **dálkové ovládání Pythonu (ptvsd)** pro **typ připojení** **(vzdálené ladění Pythonu** pro **přenos** se staršími verzemi.)
1. Zkontrolujte, zda tajný klíč v **cíli připojení** (nebo **kvalifikátor)** přesně odpovídá tajný klíč ve vzdáleném kódu.
1. Zkontrolujte, zda adresa IP v **cíli připojení** (nebo **kvalifikátoru)** odpovídá adrese vzdáleného počítače.
1. Zkontrolujte, zda jste otevřeli vzdálený ladicí port ve vzdáleném počítači a zda jste do cíle `:5678`připojení zahrnuli příponu portu, například .
    - Pokud potřebujete použít jiný port, můžete jej `enable_attach` zadat v `address` volání pomocí `ptvsd.enable_attach(address = ('0.0.0.0', 8080))`argumentu, jako v . V takovém případě otevřete tento konkrétní port v bráně firewall.
1. Zkontrolujte, zda verze ptvsd nainstalovaná ve `pip3 list` vzdáleném počítači, která byla vrácena shodami, které používají verze nástrojů Pythonu, které používáte v sadě Visual Studio, v následující tabulce. V případě potřeby aktualizujte ptvsd ve vzdáleném počítači.

    | Verze sady Visual Studio | Python tools/ptvsd verze |
    | --- | --- |
    | 2017 15.8 | 4.1.1a9 (starší ladicí program: 3.2.1.0) |
    | 2017 15.7 | 4.1.1a1 (starší ladicí program: 3.2.1.0) |
    | 2017 15.4, 15.5, 15.6 | 3.2.1.0 |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="using-ptvsd-3x"></a>Použití ptvsd 3.x

Následující informace platí pouze pro vzdálené ladění pomocí ptvsd 3.x, které obsahuje určité funkce, které byly odebrány v ptvsd 4.x.

1. S ptvsd `enable_attach` 3.x, funkce vyžaduje, abyste předat "tajný klíč" jako první argument, který omezuje přístup ke spuštěnéskript. Tento tajný klíč zadáte při připojování vzdáleného ladicího programu. I když se nedoporučuje, můžete povolit komukoli připojit, použijte `enable_attach(secret=None)`.

1. Cílová adresa `tcp://<secret>@<ip_address>:5678` URL `<secret>` připojení je `enable_attach` místo, kde je řetězec předaný v kódu Pythonu.

Ve výchozím nastavení je připojení ke vzdálenému ladicímu serveru ptvsd 3.x zabezpečeno pouze tajným kódem a všechna data jsou předávána ve formátu prostého textu. Pro bezpečnější připojení podporuje ptvsd 3.x protokol `tcsp` SSL, který jste nastavili takto:

1. Ve vzdáleném počítači vygenerujte samostatný certifikát podepsaný svým držitelem a soubory klíčů pomocí openssl:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Po zobrazení výzvy použijte název hostitele nebo ADRESU IP (podle toho, co používáte pro připojení) pro **běžný název,** když se zobrazí výzva openssl.

    (Další podrobnosti najdete v `ssl` [tématu Certifikáty podepsané svým](https://docs.python.org/3/library/ssl.html#self-signed-certificates) držitelem v dokumentech modulu Pythonu. Všimněte si, že příkaz v těchto dokumentech generuje pouze jeden kombinovaný soubor.)

1. V kódu upravte volání `enable_attach` tak, aby zahrnovalo `certfile` a `keyfile` argumenty používající názvy souborů jako hodnoty `ssl.wrap_socket` (tyto argumenty mají stejný význam jako pro standardní funkci Pythonu):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Můžete také provést stejnou změnu v souboru kódu v místním počítači, ale protože tento kód není ve skutečnosti spuštěn, není nezbytně nutné.

1. Restartujte program Pythonu ve vzdáleném počítači a připravte ho na ladění.

1. Zabezpečte kanál přidáním certifikátu do důvěryhodné ho schu a kcertifikačníautority v počítači se systémem Windows s aplikací Visual Studio:

    1. Zkopírujte soubor certifikátu ze vzdáleného počítače do místního počítače.
    1. Otevřete **Ovládací panely** a přejděte na **Nástroje pro správu** > Správa**certifikátů počítače**.
    1. V okně, které se zobrazí, rozbalte položku **Důvěryhodné kořenové certifikační úřady** na levé straně, klikněte pravým tlačítkem myši na **certifikáty**a vyberte**import** **ovat všechny úkoly** > .
    1. Přejděte do souboru *CER* zkopírovaného ze vzdáleného počítače a vyberte jej a import dokončete klepnutím v dialogových oknech.

1. Opakujte proces připojení v sadě Visual Studio, jak je popsáno výše, nyní používá `tcps://` jako protokol pro cíl **připojení** (nebo **kvalifikátor).**

    ![Výběr vzdáleného přenosu ladění pomocí technologie SSL](media/remote-debugging-qualifier-ssl.png)

1. Visual Studio zobrazí výzvy k potenciálním problémům s certifikáty při připojování přes SSL. Můžete ignorovat varování a pokračovat, ale i když je kanál stále šifrován proti odposlechu, může být otevřen útokům man-in-the-middle.

    1. Pokud se níže zobrazí **vzdálené upozornění na vzdálený certifikát,** znamená to, že jste certifikát do důvěryhodného kořenového certifikačního autority nepřidali správně. Zkontrolujte tyto kroky a zkuste to znovu.

        ![Upozornění na důvěryhodné certifikáty SSL](media/remote-debugging-ssl-warning.png)

    1. Pokud se zobrazí **název vzdáleného certifikátu neodpovídá** upozornění názvu hostitele níže, znamená to, že jste při vytváření certifikátu nepoužili správný název hostitele nebo adresu IP jako **běžný název.**

        ![Upozornění na název hostitele certifikátu SSL](media/remote-debugging-ssl-warning2.png)
