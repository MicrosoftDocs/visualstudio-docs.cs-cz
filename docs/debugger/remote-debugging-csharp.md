---
title: Vzdálené ladění C# nebo projektu VB | Dokumentace Microsoftu
ms.custom:
- remotedebugging"=
- seodec18
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3490cab7c902dcdf1a7d0095eb69dd44de47a727
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211124"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Vzdálené ladění projektu C# nebo Visual Basic v sadě Visual Studio
Ladění aplikace Visual Studio, který byl nasazen na jiný počítač, nainstalovat a spustit nástroje remote tools v počítači, kam jste nasadili aplikaci, nakonfigurujte projekt tak, aby připojení ke vzdálenému počítači ze sady Visual Studio a spusťte aplikaci.

![Vzdálený ladicí program komponenty](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Informace o vzdáleném ladění aplikací pro univerzální aplikace Windows (UPW) najdete v tématu [ladit nainstalovaný balíček aplikace](debug-installed-app-package.md).

## <a name="requirements"></a>Požadavky

Vzdálený ladicí program podporuje se ve Windows 7 a novější (ne telefon) a verze systému Windows Server od verze Windows Server 2008 Service Pack 2. Úplný seznam požadavků, najdete v části [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Ladění mezi dvěma počítači připojený prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latencí nebo připojení s malou šířkou pásma, jako je například telefonického Internetu, nebo přes Internet napříč zeměmi se nedoporučuje a může selhat nebo být příliš pomalé.

## <a name="download-and-install-the-remote-tools"></a>Stáhněte a nainstalujte nástroje remote tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> V některých případech může být nejúčinnější pro spuštění vzdáleného ladicího programu ze sdílené složky. Další informace najdete v tématu [spuštění vzdáleného ladicího programu ze sdílené složky](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="BKMK_setup"></a> Nastavení vzdáleného ladicího programu

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změnit režim ověřování, nebo číslo portu pro vzdálené ladění, naleznete v tématu [konfigurovat vzdálený ladicí program](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_csharp"></a> Vzdálené ladění projektu
Ladicí program nemůže nasadit Visual C# nebo Visual Basic desktopové aplikace ke vzdálenému počítači, ale můžete stále ladit vzdáleně následujícím způsobem. Následující postup předpokládá, že chcete ladit v počítači s názvem **MJO DL**, jak je znázorněno na obrázku níže.

1. Vytvoření projektu WPF s názvem **MyWpf**.

2. Nastavte zarážku někde v kódu, který je snadno dosaženo.

    Může například nastavit zarážku v rutině tlačítka. Uděláte to tak, otevřete soubor MainWindow.xaml a přidejte ovládací prvek tlačítko z panelu nástrojů a potom dvakrát klikněte na tlačítko otevřít její obslužná rutina.

3. V Průzkumníku řešení klikněte pravým tlačítkem na projekt a zvolte **vlastnosti**.

4. Na **vlastnosti** zvolte **ladění** kartu.

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Ujistěte se, **pracovní adresář** textové pole je prázdné.

6. Vyberte možnost **použít vzdálený počítač**a do textového pole zadejte **yourmachinename: port** . (Číslo portu se zobrazí v okně vzdáleného ladicího programu. Číslo portu zvýší 2 v každé verzi sady Visual Studio).

    V tomto příkladu použijte:
    ::: moniker range=">=vs-2019"
    **Mjo-DL: 4024** v aplikaci Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **Mjo-DL: 4022** v aplikaci Visual Studio 2017
    ::: moniker-end

7. Ujistěte se, že **povolit ladění nativního kódu** není vybraná.

8. Sestavte projekt.

9. Vytvoření složky na vzdáleném počítači, který se stejnou cestou jako **ladění** složky v počítači aplikace Visual Studio:  **\<zdrojová_cesta_operačního_systému > \MyWPF\MyWPF\bin\Debug**.

10. Zkopírujte spustitelný soubor, který jste právě sestavili ze sady Visual Studio do nově vytvořené složky na vzdáleném počítači.

    > [!CAUTION]
    > Nedovolte, aby byly změny v kódu nebo opětovné sestavení (nebo je nutné tento krok opakovat). Spustitelný soubor, který jste zkopírovali do vzdáleného počítače se musí přesně odpovídat, místní zdroje a symbolů.

    Můžete zkopírovat projektu ručně, pomocí příkazu Xcopy, Robocopy, Powershellu nebo jiné možnosti.

11. Ujistěte se, že vzdálený ladicí program je spuštěn na cílovém počítači (Pokud není, vyhledejte **vzdálený ladicí program** v **Start** nabídky). V okně vzdáleného ladicího programu vypadá takto.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. V sadě Visual Studio spustit ladění (**ladit > Spustit ladění**, nebo **F5**).

13. Pokud se zobrazí výzva, zadejte přihlašovací údaje k síti pro připojení ke vzdálenému počítači.

     Požadované přihlašovací údaje se liší v závislosti na konfiguraci zabezpečení vaší sítě. V počítači domény, můžete například zadat název domény a heslo. Na počítači mimo doménu, můžete například zadat název počítače a platné uživatelské jméno účtu, jako je třeba <strong>MJO-DL\name@something.com</strong>, spolu s správné heslo.

     Měli byste vidět, že hlavní okno aplikace WPF je otevřít na vzdáleném počítači.

14. V případě potřeby proveďte akce na zarážce. Měli byste vidět, že zarážka je aktivní. Pokud tomu tak není, ještě nebyly načteny symboly pro aplikaci. Zkuste to znovu a pokud to nepomůže, získejte informace o načítání symbolů a jak řešit je na [soubory symbolů principy a sady Visual Studio symbol nastavení](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Na počítač s Visual Studio měli byste vidět, že vykonávání se zastavilo na zarážku.

    Pokud máte jakékoli souborům bez kódu, které je potřeba v aplikaci použít, budete muset zahrnout je do projektu sady Visual Studio. Vytvořte složku projektu pro další soubory (v **Průzkumníka řešení**, klikněte na tlačítko **Přidat > Nová složka**). Pak přidejte soubory do složky (v **Průzkumníka řešení**, klikněte na tlačítko **Přidat > existující položku**, vyberte soubory). Na **vlastnosti** stránky pro každý soubor, nastavte **kopírovat do výstupního adresáře** k **vždy Kopírovat**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení se vzdálený symboly ladění

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány firewall ve Windows pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)