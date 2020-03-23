---
title: Vzdálené ladění projektu Jazyka C# nebo VB | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302096"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Vzdálené ladění projektu jazyka C# nebo Visual Basic v sadě Visual Studio
Chcete-li ladit aplikaci sady Visual Studio, která byla nasazena v jiném počítači, nainstalujte a spusťte vzdálené nástroje v počítači, ve kterém jste aplikaci nasadili, nakonfigurujte projekt tak, aby se připojil ke vzdálenému počítači z visual studia, a spusťte aplikaci.

![Součásti vzdáleného ladicího programu](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Informace o vzdáleném ladění univerzálních aplikací pro Windows (UPW) naleznete [v tématu Ladění nainstalovaného balíčku aplikací](debug-installed-app-package.md).

## <a name="requirements"></a>Požadavky

Vzdálený ladicí program je podporován v systému Windows 7 a novějších (nikoli telefonu) a verzích systému Windows Server počínaje aktualizací Windows Server 2008 Service Pack 2. Úplný seznam požadavků naleznete v tématu [Požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Ladění mezi dvěma počítači připojenými prostřednictvím serveru proxy není podporováno. Ladění přes připojení s vysokou latencí nebo nízkou šířkou pásma, jako je například telefonický Internet nebo přes Internet v různých zemích, se nedoporučuje a může selhat nebo být nepřijatelně pomalé.

## <a name="download-and-install-the-remote-tools"></a>Stažení a instalace vzdálených nástrojů

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> V některých případech může být nejúčinnější spustit vzdálený ladicí program ze sdílené složky. Další informace naleznete [v tématu Spuštění vzdáleného ladicího programu ze sdílené složky](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Nastavení vzdáleného ladicího programu

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změnit režim ověřování nebo číslo portu pro vzdálený ladicí program, přečtěte si informace [o konfiguraci vzdáleného ladicího programu](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a>Vzdálené ladění projektu
Ladicí program nemůže nasadit aplikace Visual C# nebo Visual Basic desktop do vzdáleného počítače, ale stále je můžete vzdáleně ladit následujícím způsobem. Následující postup předpokládá, že chcete ladit v počítači s názvem **MJO-DL**, jak je znázorněno na obrázku níže.

1. Vytvořte projekt WPF s názvem **MyWpf**.

2. Nastavte zarážku někde v kódu, který je snadno dostupný.

    Můžete například nastavit zarážku v obslužné rutině tlačítka. Chcete-li to provést, otevřete MainWindow.xaml a přidejte ovládací prvek Button z panelu nástrojů a poklepáním na tlačítko otevřete obslužnou rutinu.

3. V Průzkumníku řešení klepněte pravým tlačítkem myši na projekt a zvolte **Vlastnosti**.

4. Na stránce **Vlastnosti** zvolte kartu **Ladění.**

    ![VzdálenéDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "VzdálenéDebuggerCSharp")

5. Zkontrolujte, zda je textové pole **Pracovní adresář** prázdné.

6. Zvolte **Použít vzdálený počítač**a do textového pole zadejte **název_počítače:port.** (Číslo portu se zobrazí v okně vzdáleného ladicího programu. Číslo portu se v každé verzi sady Visual Studio ztohočí 2).

    V tomto příkladu použijte:
    ::: moniker range=">=vs-2019"
    **MJO-DL:4024** ve Visual Studiu 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **MJO-DL:4022** v sadě Visual Studio 2017
    ::: moniker-end

7. Ujistěte **se, že není vybráno povolit ladění nativního kódu.**

8. Sestavte projekt.

9. Vytvořte ve vzdáleném počítači složku, která má stejnou cestu jako složka **Ladění** v počítači sady Visual Studio: ** \<zdrojová cesta>\MyWPF\MyWPF\bin\Debug**.

10. Zkopírujte spustitelný soubor, který jste právě vytvořili z počítače sady Visual Studio, do nově vytvořené složky ve vzdáleném počítači.

    > [!CAUTION]
    > Neprovázte změny v kódu ani znovu sestavit (nebo je nutné tento krok zopakovat). Spustitelný soubor, který jste zkopírovali do vzdáleného počítače, se musí přesně shodovat s místním zdrojem a symboly.

    Projekt můžete zkopírovat ručně, použít Xcopy, Robocopy, Powershell nebo jiné možnosti.

11. Ujistěte se, že vzdálený ladicí program běží na cílovém počítači (Pokud tomu tak není, vyhledejte **vzdálený ladicí program** v nabídce **Start).** Okno vzdáleného ladicího programu vypadá takto.

     ![Vzdálené debuggerokno](../debugger/media/remotedebuggerwindow.png "Vzdálené debuggerokno")

12. V sadě Visual Studio spusťte ladění (**ladění > spuštění ladění**nebo **F5**).

13. Po zobrazení výzvy zadejte síťová pověření pro připojení ke vzdálenému počítači.

     Požadovaná pověření se liší v závislosti na konfiguraci zabezpečení sítě. Například v počítači domény můžete zadat název domény a heslo. V počítači, který není v doménovém počítači, můžete <strong>MJO-DL\name@something.com</strong>zadat název počítače a platný název uživatelského účtu, například , spolu se správným heslem.

     Měli byste vidět, že hlavní okno aplikace WPF je otevřeno ve vzdáleném počítači.

14. V případě potřeby akci provést přístupovou chvíli. Měli byste vidět, že zarážka je aktivní. Pokud tomu tak není, symboly pro aplikaci nebyly načteny. Opakujte akci, a pokud to nefunguje, získejte informace o načítání symbolů a o tom, jak je řešit v [tématu Principy souborů symbolů a nastavení symbolů sady Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. V počítači Visual Studio, měli byste vidět, že spuštění se zastavil na zarážky.

    Pokud máte všechny soubory bez kódu, které musí být použity v aplikaci, je třeba zahrnout do projektu Sady Visual Studio. Vytvořte složku projektu pro další soubory (v **Průzkumníku řešení**klepněte na **tlačítko Přidat > novou složku**). Pak přidejte soubory do složky (v **Průzkumníku řešení**klepněte na **přidat > existující položku**a vyberte soubory). Na stránce **Vlastnosti** pro každý soubor nastavte vždy možnost **Kopírovat do výstupního adresáře** na **Kopírovat**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení ladění pomocí vzdálených symbolů

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby a řešení potíží se vzdáleným laděním](../debugger/remote-debugging-errors-and-troubleshooting.md)