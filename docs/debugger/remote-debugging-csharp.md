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
ms.openlocfilehash: 5f147acae956ad380c6e85984de29d5316394c0a
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409406"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Vzdálené ladění projektu C# nebo Visual Basic v sadě Visual Studio
Ladění aplikace Visual Studio, který byl nasazen na jiný počítač, nainstalovat a spustit nástroje remote tools v počítači, kam jste nasadili aplikaci, nakonfigurujte projekt tak, aby připojení ke vzdálenému počítači ze sady Visual Studio a spusťte aplikaci.

![Komponenty vzdáleného ladicího programu](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Informace o vzdáleném ladění univerzálních aplikací pro Windows (UWP) najdete v tématu [ladění nainstalovaného balíčku aplikace](debug-installed-app-package.md).

## <a name="requirements"></a>Požadavky

Vzdálený ladicí program podporuje se ve Windows 7 a novější (ne telefon) a verze systému Windows Server od verze Windows Server 2008 Service Pack 2. Úplný seznam požadavků najdete v tématu [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Ladění mezi dvěma počítači připojený prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latencí nebo připojení s malou šířkou pásma, jako je například telefonického Internetu, nebo přes Internet napříč zeměmi se nedoporučuje a může selhat nebo být příliš pomalé.

## <a name="download-and-install-the-remote-tools"></a>Stáhněte a nainstalujte nástroje remote tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> V některých případech může být nejúčinnější pro spuštění vzdáleného ladicího programu ze sdílené složky. Další informace najdete v tématu [spuštění vzdáleného ladicího programu ze sdílené složky](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="BKMK_setup"></a>Nastavení vzdáleného ladicího programu

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změňte režim ověřování nebo číslo portu vzdáleného ladicího programu. Další informace najdete v tématu [Konfigurace vzdáleného ladicího programu](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_csharp"></a>Vzdálené ladění projektu
Ladicí program nemůže nasadit Visual C# nebo Visual Basic desktopové aplikace ke vzdálenému počítači, ale můžete stále ladit vzdáleně následujícím způsobem. Následující postup předpokládá, že ho chcete ladit v počítači s názvem **mjo-DL**, jak je znázorněno na následujícím obrázku.

1. Vytvořte projekt WPF s názvem **MyWpf**.

2. Nastavte zarážku někde v kódu, který je snadno dosaženo.

    Může například nastavit zarážku v rutině tlačítka. Uděláte to tak, otevřete soubor MainWindow.xaml a přidejte ovládací prvek tlačítko z panelu nástrojů a potom dvakrát klikněte na tlačítko otevřít její obslužná rutina.

3. V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.

4. Na stránce **vlastnosti** klikněte na kartu **ladění** .

    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")

5. Ujistěte se, že je textové pole **pracovní adresář** prázdné.

6. Vyberte možnost **použít vzdálený počítač**a do textového pole zadejte **yourmachinename: port** . (Číslo portu se zobrazí v okně vzdáleného ladicího programu. Číslo portu zvýší 2 v každé verzi sady Visual Studio).

    V tomto příkladu použijte:
    ::: moniker range=">=vs-2019"
    **Mjo-DL: 4024** v aplikaci Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **Mjo-DL: 4022** v aplikaci Visual Studio 2017
    ::: moniker-end

7. Ujistěte se, že není vybraná **možnost Povolit ladění nativního kódu** .

8. Sestavte projekt.

9. Vytvořte složku na vzdáleném počítači, která je stejná jako složka pro **ladění** v počítači se systémem Visual Studio: **\<zdrojová cesta > \MyWPF\MyWPF\bin\Debug**.

10. Zkopírujte spustitelný soubor, který jste právě sestavili ze sady Visual Studio do nově vytvořené složky na vzdáleném počítači.

    > [!CAUTION]
    > Nedovolte, aby byly změny v kódu nebo opětovné sestavení (nebo je nutné tento krok opakovat). Spustitelný soubor, který jste zkopírovali do vzdáleného počítače se musí přesně odpovídat, místní zdroje a symbolů.

    Můžete zkopírovat projektu ručně, pomocí příkazu Xcopy, Robocopy, Powershellu nebo jiné možnosti.

11. Ujistěte se, že je na cílovém počítači spuštěný vzdálený ladicí program (Pokud není, vyhledejte v nabídce **Start** **vzdálený ladicí program** ). V okně vzdáleného ladicího programu vypadá takto.

     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")

12. V aplikaci Visual Studio spusťte ladění (**ladění > spustit ladění**nebo **F5**).

13. Pokud se zobrazí výzva, zadejte přihlašovací údaje k síti pro připojení ke vzdálenému počítači.

     Požadované přihlašovací údaje se liší v závislosti na konfiguraci zabezpečení vaší sítě. V počítači domény, můžete například zadat název domény a heslo. Na počítači, který není doménou, můžete zadat název počítače a platný název uživatelského účtu, například <strong>MJO-DL\name@something.com</strong>, spolu se správným heslem.

     Měli byste vidět, že hlavní okno aplikace WPF je otevřít na vzdáleném počítači.

14. V případě potřeby proveďte akce na zarážce. Měli byste vidět, že zarážka je aktivní. Pokud tomu tak není, ještě nebyly načteny symboly pro aplikaci. Zkuste to znovu, a pokud to nefunguje, Získejte informace o načítání symbolů a o tom, jak je řešit, v tématu [Principy souborů symbolů a nastavení symbolů sady Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Na počítač s Visual Studio měli byste vidět, že vykonávání se zastavilo na zarážku.

    Pokud máte jakékoli souborům bez kódu, které je potřeba v aplikaci použít, budete muset zahrnout je do projektu sady Visual Studio. Vytvořte složku projektu pro další soubory (v **Průzkumník řešení**klikněte na **Přidat > Nová složka**). Pak přidejte soubory do složky (v **Průzkumník řešení**klikněte na **Přidat > existující položku**a pak vyberte soubory). Na stránce **vlastnosti** pro každý soubor nastavte vždy hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení se vzdálený symboly ladění

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také:
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány firewall ve Windows pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)