---
title: Ladění kódu Pythonu na vzdálených počítačích se systémem Linux
description: Pomocí sady Visual Studio můžete ladit kód Pythonu běžící na vzdálených počítačích se systémem Linux, včetně nezbytných kroků konfigurace, zabezpečení a řešení potíží.
ms.date: 05/12/2020
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5307684bde56955f2a4ed77d2ac66b6b30cb1c1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541066"
---
Visual Studio může spouštět a ladit aplikace v Pythonu místně a vzdáleně na počítači s Windows (viz [vzdálené ladění](../../../debugger/remote-debugging.md)). Můžete ho také vzdáleně ladit na jiném operačním systému, zařízení nebo implementaci Pythonu než CPython pomocí [knihovny debugpy](https://pypi.org/project/debugpy/).

Při použití debugpy kód Pythonu, který se právě ladí, hostuje ladicí Server, ke kterému se může připojit Visual Studio. Toto hostování vyžaduje pro import a povolení serveru malou úpravu kódu a může vyžadovat konfiguraci sítě nebo brány firewall na vzdáleném počítači, aby bylo možné povolit připojení TCP.

> [!NOTE]
> Pro Visual Studio 2019 verze 16,4 a starší se použila [Knihovna ptvsd](https://pypi.python.org/pypi/ptvsd) . Knihovna debugpy nahradila ptvsd 4 ve Visual Studiu 2019 verze 16,5.

## <a name="set-up-a-linux-computer"></a>Nastavení počítače se systémem Linux

Následující položky jsou potřebné k provedení tohoto návodu:

- Vzdálený počítač, na kterém běží Python, v operačním systému, jako je Mac OSX nebo Linux.
- Port 5678 (příchozí) otevřený v bráně firewall tohoto počítače, což je výchozí nastavení pro vzdálené ladění.

> [!NOTE]
> Tento návod vychází ze sady Visual Studio 2019 verze 16,6.

V Azure můžete snadno vytvořit [virtuální počítač se systémem Linux](/azure/virtual-machines/linux/creation-choices) a [získat k němu přístup pomocí vzdálené plochy](/azure/virtual-machines/linux/use-remote-desktop) z Windows. Ubuntu pro virtuální počítač je pohodlné, protože ve výchozím nastavení je Python nainstalovaný. v opačném případě se podívejte na seznam pro [instalaci interpretu Python dle vašeho výběru](../../installing-python-interpreters.md) pro další umístění pro stažení v Pythonu.

Podrobnosti o vytvoření pravidla brány firewall pro virtuální počítač Azure najdete v tématu [otevření portů k virtuálnímu počítači v Azure pomocí Azure Portal](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Příprava skriptu pro ladění

1. Na vzdáleném počítači vytvořte soubor Pythonu s názvem *guessing-Game.py* s následujícím kódem:

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

1. Nainstalujte `debugpy` balíček do svého prostředí pomocí `pip3 install debugpy` .
   >[!NOTE]
   >Je vhodné si zaznamenat verzi debugpy, která je nainstalována pro případ, že ji budete potřebovat k řešení potíží. [seznam debugpy](https://pypi.org/project/debugpy/) také zobrazuje dostupné verze.

1. Povolte vzdálené ladění přidáním kódu níže v nejbližším možném bodě *guessing-Game.py*, než je jiný kód. (I když to není přísné požadavky, není nemožné ladit všechna vlákna na pozadí vytvořená před `listen` voláním funkce.)

   ```python
   import debugpy
   debugpy.listen(5678)
   ```

1. Uložte soubor a spusťte příkaz `python3 guessing-game.py` . Volání, které se `listen` spustí na pozadí a čeká na příchozí připojení, když jinak budete pracovat s programem. V případě potřeby `wait_for_client` lze funkci volat po `listen` zablokování programu, dokud se ladicí program nepřipojí.

> [!Tip]
> Kromě `listen` a `wait_for_client` , debugpy také poskytuje pomocnou funkci `breakpoint` , která slouží jako programová zarážka, pokud je připojen ladicí program. K dispozici je také `is_client_connected` funkce, která vrátí, `True` Pokud je připojen ladicí program (Všimněte si, že tento výsledek není nutné kontrolovat před voláním jiných `debugpy` funkcí).

## <a name="attach-remotely-from-python-tools"></a>Vzdálené připojení z nástrojů Pythonu

V tomto postupu nastavíme jednoduchou zarážku pro zastavení vzdáleného procesu.

1. Vytvořte kopii vzdáleného souboru v místním počítači a otevřete ji v aplikaci Visual Studio. Nezáleží na tom, kde se soubor nachází, ale jeho název by měl odpovídat názvu skriptu na vzdáleném počítači.

1. Volitelné Pokud chcete mít IntelliSense pro debugpy v místním počítači, nainstalujte do prostředí Python balíček debugpy.

1. Vyberte **ladit**  >  **připojit k procesu**.

1. V dialogu **připojit k procesu** , který se zobrazí, nastavte **Typ připojení** na standard **Python Remote (debugpy)**.

1. Do pole **cíl připojení** zadejte, `tcp://<ip_address>:5678` kde `<ip_address>` je adresa vzdáleného počítače (což může být buď explicitní adresa, nebo název jako myvm.cloudapp.NET) a `:5678` číslo portu vzdáleného ladění.

1. Stisknutím klávesy **ENTER** naplňte seznam dostupných debugpy procesů na tomto počítači:

    ![Zadání cílů připojení a procesů výpisu](../../media/remote-debugging-attach.png)

    Pokud po naplnění tohoto seznamu spustíte jiný program na vzdáleném počítači, vyberte tlačítko **aktualizovat** .

1. Vyberte proces, který se má ladit a pak **Připojte**, nebo poklikejte na proces.

1. Visual Studio se pak přepne do režimu ladění, zatímco skript pokračuje v běhu na vzdáleném počítači a poskytuje všechny běžné možnosti [ladění](../../debugging-python-in-visual-studio.md) . Můžete například nastavit zarážku na `if guess < number:` řádku, přepnout na vzdálený počítač a zadat další odhad. Až to uděláte, Visual Studio v místním počítači se zastaví v této zarážce, zobrazí místní proměnné a tak dále:

    ![Visual Studio pozastaví ladění, když je dosaženo zarážky.](../../media/remote-debugging-breakpoint-hit.png)

1. Když zastavíte ladění, Visual Studio se odpojí od programu, který je nadále spuštěný ve vzdáleném počítači. debugpy také nadále naslouchá pro připojení ladicího programu, takže se můžete znovu připojit k procesu kdykoli znovu.

### <a name="connection-troubleshooting"></a>Řešení potíží s připojením

1. Ujistěte se, že jste vybrali možnost **debugpy (Python Remote)** pro **Typ připojení** .
1. Ověřte, zda tajný klíč v **cíli připojení** přesně odpovídá tajnému klíči ve vzdáleném kódu.
1. Ověřte, zda IP adresa v **cíli připojení** odpovídá vzdálenému počítači.
1. Ověřte, zda jste otevřeli port vzdáleného ladění na vzdáleném počítači a zda jste v cíli připojení zahrnuli příponu portu, například `:5678` .
    - Pokud potřebujete použít jiný port, můžete ho zadat v nástroji `listen` , jako v `debugpy.listen((host, port))` . V takovém případě otevřete tento konkrétní port v bráně firewall.
1. Ověřte, zda je ve vzdáleném počítači nainstalovaná verze debugpy, jakou vrátila `pip3 list` shoda, kterou používá verze nástrojů Pythonu, které používáte v aplikaci Visual Studio v následující tabulce. V případě potřeby aktualizujte debugpy na vzdáleném počítači.

    | Verze sady Visual Studio | Python Tools/verze debugpy |
    | --- | --- |
    | 2019 16,6 | 1.0.0 B5 |
    | 2019 16,5 | 1.0.0 B1 |

> [!NOTE]
> Visual Studio 2019 verze 16.0-16.4 využívá ptvsd, ne debugpy. Proces v tomto průvodci pro tyto verze je podobný, ale názvy funkcí se liší. Visual Studio 2019 verze 16,5 používá debugpy, ale názvy funkcí byly stejné jako v ptvsd. Místo byste `listen` mohli použít `enable_attach` . Místo byste `wait_for_client` mohli použít `wait_for_attach` . Místo byste `breakpoint` mohli použít `break_into_debugger` .

## <a name="using-ptvsd-3x-for-legacy-debugging"></a>Použití ptvsd 3. x pro ladění starší verze
Visual Studio 2017 verze 15,8 a novější používají ladicí program založený na ptvsd verze 4.1 +. Visual Studio 2019 verze 16,5 a novější používají ladicí program založený na debugpy. Tyto verze ladicího programu jsou kompatibilní s Pythonem 2,7 a Python 3.5 +. Pokud používáte Python 2,6, 3,1 až 3,4 nebo Ironpythonu, Visual Studio zobrazí chybu, **ladicí program nepodporuje toto prostředí Pythonu**. Následující informace platí pouze pro vzdálené ladění s ptvsd 3. x.

1. V ptvsd 3. x je `enable_attach` funkce nutná, abyste předali "tajný klíč" jako první argument, který omezuje přístup ke spuštěnému skriptu. Tento tajný klíč zadáte při připojování vzdáleného ladicího programu. I když se to nedoporučuje, můžete všem uživatelům umožnit, aby se připojili, používali `enable_attach(secret=None)` .

1. Adresa URL cíle připojení je `tcp://<secret>@<ip_address>:5678` tam, kde `<secret>` je řetězec předaný `enable_attach` v kódu Pythonu.

Ve výchozím nastavení je připojení ke vzdálenému ladicímu serveru ptvsd 3. x zabezpečené pouze tajným klíčem a všechna data jsou předána do prostého textu. Pro bezpečnější připojení ptvsd 3. x podporuje SSL pomocí `tcsp` protokolu, který jste nastavili takto:

1. Ve vzdáleném počítači generujte samostatný certifikát podepsaný svým držitelem a soubory klíčů pomocí OpenSSL:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Po zobrazení výzvy pomocí OpenSSL použijte název hostitele nebo IP adresu (podle toho, co se používá pro připojení) pro **běžný název** .

    (Další podrobnosti najdete v tématu [certifikáty podepsané svým držitelem](https://docs.python.org/3/library/ssl.html#self-signed-certificates) v `ssl` dokumentaci modulu Pythonu. Všimněte si, že příkaz v těchto dokumentech generuje jenom jeden kombinovaný soubor.)

1. V kódu změňte volání na `enable_attach` k zahrnutí `certfile` a `keyfile` argumentů za použití názvů souborů jako hodnot (tyto argumenty mají stejný význam jako pro standardní `ssl.wrap_socket` funkci Pythonu):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Stejnou změnu můžete provést také v souboru s kódem v místním počítači, ale vzhledem k tomu, že tento kód není skutečně spuštěn, není nezbytně nutné.

1. Restartujte program Pythonu na vzdáleném počítači a připravte ho pro ladění.

1. Zabezpečte kanál přidáním certifikátu do důvěryhodné kořenové certifikační autority na počítači s Windows pomocí sady Visual Studio:

    1. Zkopírujte soubor certifikátu ze vzdáleného počítače do místního počítače.
    1. Otevřete **Ovládací panely** a přejděte na **Nástroje pro správu**  >  **Správa certifikátů počítačů**.
    1. V okně, které se zobrazí, rozbalte položku **Důvěryhodné kořenové certifikační autority** na levé straně, klikněte pravým tlačítkem na položku **certifikáty**a vyberte možnost **všechny úkoly**  >  **importovat**.
    1. Přejděte na a vyberte soubor *. cer* zkopírovaný ze vzdáleného počítače a potom kliknutím na dialogová okna dokončete import.

1. Opakujte proces připojení v aplikaci Visual Studio, jak je popsáno dříve, a teď použijte `tcps://` jako protokol pro **cíl připojení** (nebo **kvalifikátor**).

    ![Výběr přenosu vzdáleného ladění s protokolem SSL](../../media/remote-debugging-qualifier-ssl.png)

1. Visual Studio vás vyzve k problémům s certifikátem při připojení přes protokol SSL. Můžete ignorovat upozornění a pokračovat, ale kanál je i nadále zašifrovaný proti odposlouchávání, a proto je možné je otevřít útokům prostředníkem.

    1. Pokud se zobrazí zpráva **vzdálený certifikát není důvěryhodný** , znamená to, že jste nepřidali certifikát do důvěryhodné kořenové certifikační autority. Proveďte tyto kroky a zkuste to znovu.

        ![Důvěryhodné upozornění certifikátu SSL](../../media/remote-debugging-ssl-warning.png)

    1. Pokud se zobrazuje **název vzdáleného certifikátu neshoduje** s upozorněním na název hostitele níže, znamená to, že při vytváření certifikátu nepoužíváte jako **běžný název správný název** hostitele nebo IP adresu.

        ![Upozornění na název hostitele certifikátu SSL](../../media/remote-debugging-ssl-warning2.png)
