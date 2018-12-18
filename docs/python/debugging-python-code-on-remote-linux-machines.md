---
title: Ladění kódu v Pythonu na vzdálených Linuxových počítačích
description: Ladění kódu v Pythonu běží na vzdálených Linuxových počítačích, včetně potřebný postup konfigurace, zabezpečení a řešení potíží pomocí sady Visual Studio.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c14fb14a8941895fab473952908e6aefa2e2f14
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067943"
---
# <a name="remotely-debug-python-code-on-linux"></a>Vzdálené ladění kódu v Pythonu v Linuxu

Visual Studio můžete spustit a lokální a vzdálené ladění aplikací v Pythonu v počítači Windows (viz [vzdálené ladění](../debugger/remote-debugging.md)). To může také vzdálené ladění na různých operačních systémů, zařízení nebo implementace Python než CPython pomocí [ptvsd knihovny](https://pypi.python.org/pypi/ptvsd).

Při použití ptvsd, hostuje kód Pythonu, který se právě ladí ladění serveru, na který lze připojit sady Visual Studio. Malé změny kódu do importovat na server a může vyžadovat sítě nebo povolení brány firewall na vzdáleném počítači a povolíte připojení TCP konfigurace tohoto hostování vyžaduje.

|   |   |
|---|---|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | Úvod do vzdáleného ladění, naleznete v tématu [podrobně: vzdálené ladění napříč platformami](https://youtu.be/y1Qq7BrV6Cc) (webu youtube.com, 6m22s), která se vztahuje na Visual Studio 2015 a 2017. |

## <a name="set-up-a-linux-computer"></a>Nastavit počítač s Linuxem

Následující položky je třeba postupovat podle tohoto návodu:

- Vzdálený počítač se systémem Python v operačním systému, jako jsou Mac OS x nebo Linux.
- Port 5678 (příchozí) otevřené na tomto počítači brány firewall, což je výchozí nastavení pro vzdálené ladění.

Můžete snadno vytvořit [virtuálního počítače s Linuxem v Azure](/azure/virtual-machines/linux/creation-choices) a [přístup pomocí vzdálené plochy](/azure/virtual-machines/linux/use-remote-desktop) z Windows. Pro virtuální počítač se systémem Ubuntu je pohodlné, protože je ve výchozím nastavení; nainstalován Python v opačném případě najdete v seznamu na [nainstalujte interpret Pythonu podle vašeho výběru](installing-python-interpreters.md) pro umístění pro stahování dalších Python.

Podrobnosti o vytvoření pravidla brány firewall pro virtuální počítač Azure najdete v tématu [otevření portů k virtuálnímu počítači v Azure pomocí webu Azure portal](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Příprava ladění skriptu

1. Na vzdáleném počítači, vytvořte soubor Pythonu s názvem *opakovaně uhodnout game.py* následujícím kódem:

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

1. Nainstalujte `ptvsd` balíčku do vašeho prostředí pomocí `pip3 install ptvsd`. 
   >[!NOTE]
   >Je vhodné zaznamenat verzi ptvsd, která je nainstalována v případě, že ho budete potřebovat pro řešení potíží s; [ptvsd výpis](https://pypi.python.org/pypi/ptvsd) také zobrazuje dostupné verze.

1. Povolení vzdáleného ladění tak, že přidáte následující kód nejbližší možné v okamžiku *opakovaně uhodnout game.py*, před jiným kódem. (I když striktní požadavek, není možné ladit žádného vlákna na pozadí vytvoří podřízený proces před `enable_attach` funkce je volána.)

   ```python
   import ptvsd
   ptvsd.enable_attach()
   ```

1. Uložte soubor a spusťte `python3 guessing-game.py`. Volání `enable_attach` běží na pozadí a čeká na příchozí připojení, když pracujete v opačném případě se program. V případě potřeby `wait_for_attach` funkce lze volat po `enable_attach` Blokujte program, dokud ladicí program připojí.

> [!Tip]
> Kromě `enable_attach` a `wait_for_attach`, ptvsd také poskytuje pomocnou funkci `break_into_debugger`, který slouží jako zarážku prostřednictvím kódu programu, pokud je připojen ladicí program. K dispozici je také `is_attached` funkce, která vrací `True` Pokud je připojen ladicí program (Všimněte si, že není nutné ke kontrole tohoto výsledku před voláním jakékoli jiné `ptvsd` funkce).

## <a name="attach-remotely-from-python-tools"></a>Připojit vzdáleně z nástroje Python Tools

V následujícím postupu jsme nastavení jednoduché zarážky zastavit vzdálený proces.

1. Vytvoření kopie vzdáleného souboru na místním počítači a otevřete ho v sadě Visual Studio. Je jedno, kde je umístěn soubor, ale její název by měl odpovídat názvu souboru, který na vzdáleném počítači.

1. (Volitelné) Pokud chcete, aby IntelliSense pro ptvsd v místním počítači, nainstalujte balíček ptvsd prostředí Pythonu.

1. Vyberte **ladění** > **připojit k procesu**.

1. V **připojit k procesu** dialogové okno, které se zobrazí, nastavte **typ připojení** k **vzdálené Pythonu (ptvsd)**. (Ke starším verzím sady Visual Studio jsou pojmenovány tyto příkazy **přenosu** a **vzdálené ladění Pythonu**.)

1. V **cíl připojení** pole (**kvalifikátor** na starší verze), zadejte `tcp://<ip_address>:5678` kde `<ip_address>` je, že vzdáleného počítače (který může být explicitní adresa nebo název, například myvm.cloudapp.NET), a `:5678` je číslo portu vzdáleného ladění.

1. Stisknutím klávesy **Enter** k naplnění seznamu k dispozici ptvsd procesy v tomto počítači:

    ![Zadáním cíl připojení a seznam procesů](media/remote-debugging-qualifier.png)

    Pokud jste ke spuštění jiného programu na vzdáleném počítači po naplnění seznamu, vyberte **aktualizovat** tlačítko.

1. Vyberte proces pro ladění a pak **připojit**, nebo dvakrát klikněte na proces.

1. Visual Studio dojde k přepnutí do režimu ladění, zatímco skript stále běží na vzdáleném počítači, poskytuje všechny běžné [ladění](debugging-python-in-visual-studio.md) možnosti. Například nastavte zarážku na `if guess < number:` řádku, pak přepnutí na vzdáleném počítači a zadejte jiné odhad. Až tak učiníte, Visual Studio na váš místní počítač zastaví na zarážce, zobrazí místní proměnné a tak dále:

    ![Visual Studio pozastaví ladění při dosažení zarážky](media/remote-debugging-breakpoint-hit.png)

1. Při zastavení ladění sady Visual Studio se odpojí z programu, který zůstane spuštěný na vzdáleném počítači. ptvsd taky dál naslouchání pro připojení ladicí programy, takže můžete znovu připojit k procesu kdykoli znovu.

### <a name="connection-troubleshooting"></a>Řešení potíží s připojením

1. Ujistěte se, že jste vybrali **vzdálené Pythonu (ptvsd)** pro **typ připojení** (**vzdálené ladění Pythonu** pro **přenosu** s starší verze.)
1. Zkontrolujte, že tajný klíč v **cíl připojení** (nebo **kvalifikátor**) se přesně shoduje s tajným kódem v vzdáleného kódu.
1. Zkontrolujte, že IP adresa v **cíl připojení** (nebo **kvalifikátor**) odpovídá vzdáleného počítače.
1. Zkontrolujte, že máte otevřen port vzdáleného ladění na vzdáleném počítači a že jste zadali přípona portu v cíl připojení, jako `:5678`.
    - Pokud je potřeba použít jiný port, můžete je zadat v `enable_attach` zavolat pomocí `address` argument, jako v `ptvsd.enable_attach(address = ('0.0.0.0', 8080))`. V tomto případě otevřete určený port v bráně firewall.
1. Zkontrolujte, že verzi ptvsd nainstalovaný na vzdáleném počítači vrácené `pip3 list` odpovídá používané verzi nástroje Pythonu, který používáte v sadě Visual Studio v následující tabulce. V případě potřeby aktualizujte ptvsd na vzdáleném počítači.

    | Verze Visual Studio | Nástroje/ptvsd verze Pythonu |
    | --- | --- |
    | 2017 15.8 | 4.1.1a9 (starší verze ladicího programu: 3.2.1.0) |
    | 2017 15.7 | 4.1.1A1 (starší verze ladicího programu: 3.2.1.0) |
    | 2017 15.4, 15.5, verzi 15.6 | 3.2.1.0 |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="using-ptvsd-3x"></a>Pomocí ptvsd 3.x

Následující informace platí pouze pro vzdálené ladění pomocí ptvsd 3.x, který obsahuje některé funkce, které byly odstraněny v ptvsd 4.x.

1. S ptvsd 3.x `enable_attach` funkce vyžaduje předání "tajný klíč" jako první argument, který omezuje přístup na spouštění skriptu. Tento tajný kód zadáte při připojování vzdáleného ladicího programu. Když ale nedoporučený krok, můžete povolit všem uživatelům připojení, použijte `enable_attach(secret=None)`.

1. Cíl připojení je adresa URL `tcp://<secret>@<ip_address>:5678` kde `<secret>` se předal řetězec `enable_attach` v kódu Pythonu.

Ve výchozím nastavení je zabezpečená připojení k serveru ptvsd 3.x vzdálené ladění pouze pomocí tajný kód a všechna data předávána ve formátu prostého textu. Pro zabezpečení připojení, ptvsd 3.x podporuje používání protokolu SSL `tcsp` protokol, který nastavíte takto:

1. Na vzdáleném počítači generovat samostatný certifikát podepsaný svým držitelem a pomocí openssl soubory klíčů:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Pokud budete vyzváni, použijte název hostitele nebo IP adresa (podle toho, co použijete k připojení) pro **běžný název** po zobrazení výzvy openssl.

    (Viz [certifikáty podepsané svým držitelem](https://docs.python.org/3/library/ssl.html#self-signed-certificates) v Pythonu `ssl` modulu dokumentace pro další podrobnosti. Všimněte si, že příkaz v těchto dokumentace generuje pouze jeden soubor kombinované.)

1. V kódu, upravte volání `enable_attach` zahrnout `certfile` a `keyfile` pomocí názvů souborů jako hodnoty argumentů (tyto argumenty mají stejný význam jako u standardní `ssl.wrap_socket` funkce Pythonu):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Můžete také provést stejnou změnu v souboru kódu na místním počítači, ale protože tento kód není ve skutečnosti spuštěn, není nezbytně nutné.

1. Restartujte program v Pythonu na vzdáleném počítači, takže připravené pro ladění.

1. Zabezpečený kanál tak, že přidáte certifikát důvěryhodné kořenové certifikační Autority na počítači Windows pomocí sady Visual Studio:

    1. Zkopírujte soubor certifikátu ze vzdáleného počítače do místního počítače.
    1. Otevřít **ovládací panely** a přejděte do **nástroje pro správu** > **spravovat certifikáty počítače**.
    1. V okně, které se zobrazí, rozbalte **důvěryhodných kořenových certifikačních autorit** na levé straně, klikněte pravým tlačítkem na **certifikáty**a vyberte **všechny úkoly**  >  **Import**.
    1. Vyhledejte a vyberte *.cer* zkopírovat soubor ze vzdáleného počítače, potom klikněte na tlačítko prostřednictvím dialogových oknech se bylo možné import dokončit.

1. Postupujte stejně jako připojení v sadě Visual Studio jak je popsáno výše, teď používá `tcps://` jako protokol pro **cíl připojení** (nebo **kvalifikátor**).

    ![Výběr přenos vzdáleného ladění s protokolem SSL](media/remote-debugging-qualifier-ssl.png)

1. Visual Studio vás vyzve k o potenciálních problémech s certifikátem při připojení přes protokol SSL. Můžete upozornění ignorovat a pokračovat, ale i když před odposlechem ve chvíli je šifrovaný kanál může být otevřeno vůči útokům man-in-the-middle.

    1. Pokud se zobrazí **vzdálený certifikát není důvěryhodný** upozornění níže, to znamená, že nebyl přidán správně certifikát k důvěryhodné kořenové certifikační Autority. Zkontrolujte tyto kroky a zkuste to znovu.

        ![Upozornění důvěryhodný certifikát SSL](media/remote-debugging-ssl-warning.png)

    1. Pokud se zobrazí **vzdálený certifikát název neodpovídá názvu hostitele** upozornění níže, to znamená, že jste nepoužili správný název hostitele nebo IP adresou, jako **běžný název** při vytváření certifikátu.

        ![Upozornění na název hostitele certifikátu SSL](media/remote-debugging-ssl-warning2.png)
