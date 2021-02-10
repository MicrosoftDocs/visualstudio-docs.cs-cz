---
title: Vzdálené ladění projektu v jazyce C# nebo VB | Microsoft Docs
description: Naučte se, jak ladit aplikaci Visual Studio C# nebo Visual Basic ze vzdáleného počítače pomocí následujících podrobných pokynů.
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e814e442fe740c6a5090a43a2d76fb50168ea205
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934634"
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>Vzdálené ladění projektu v jazyce C# nebo Visual Basic v aplikaci Visual Studio
Chcete-li ladit aplikaci Visual Studio, která byla nasazena v jiném počítači, nainstalujte a spusťte nástroje Remote Tools v počítači, kde jste nasadili aplikaci, nakonfigurujte projekt tak, aby se připojil ke vzdálenému počítači ze sady Visual Studio, a pak spusťte aplikaci.

![Komponenty vzdáleného ladicího programu](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Informace o vzdáleném ladění univerzálních aplikací pro Windows (UWP) najdete v tématu [ladění nainstalovaného balíčku aplikace](debug-installed-app-package.md).

## <a name="requirements"></a>Požadavky

Vzdálený ladicí program je podporován ve Windows 7 a novějších (ne v telefonu) a verzích Windows serveru počínaje verzí Windows Server 2008 Service Pack 2. Úplný seznam požadavků najdete v tématu [požadavky](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Ladění mezi dvěma počítači připojenými prostřednictvím proxy serveru není podporováno. Ladění přes vysokou latenci nebo připojení s nízkou šířkou pásma, jako je například telefonické připojení k Internetu nebo přes Internet v zemích, se nedoporučuje a může být neúspěšné nebo nepřijatelně pomalé.

## <a name="download-and-install-the-remote-tools"></a>Stažení a instalace nástrojů Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> V některých scénářích může být pro spuštění vzdáleného ladicího programu ze sdílené složky nejúčinnější. Další informace najdete v tématu [spuštění vzdáleného ladicího programu ze sdílené složky](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Nastavení vzdáleného ladicího programu

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Pokud potřebujete přidat oprávnění pro další uživatele, změňte režim ověřování nebo číslo portu vzdáleného ladicího programu. Další informace najdete v tématu [Konfigurace vzdáleného ladicího programu](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-the-project"></a><a name="remote_csharp"></a> Vzdálené ladění projektu
Ladicí program nemůže nasadit aplikace Visual C# nebo Visual Basic desktopové aplikace do vzdáleného počítače, ale můžete je vzdáleně ladit následujícím způsobem. Následující postup předpokládá, že ho chcete ladit v počítači s názvem **mjo-DL**, jak je znázorněno na následujícím obrázku.

1. Vytvořte projekt WPF s názvem **MyWpf**.

2. Nastavte zarážku někam v kódu, který je snadno dosažitelný.

    Například můžete nastavit zarážku v obslužné rutině tlačítka. Provedete to tak, že otevřete MainWindow. XAML a přidáte ovládací prvek tlačítko ze sady nástrojů a potom dvakrát kliknete na tlačítko pro otevření jeho obslužné rutiny.

3. V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.

4. Na stránce **vlastnosti** klikněte na kartu **ladění** .

    ![Snímek obrazovky karty ladění ve vlastnostech Průzkumník řešení sady Visual Studio Vlastnost použít vzdálený počítač je nastavená na MJO-DL: 4022.](../debugger/media/remotedebuggercsharp.png)

5. Ujistěte se, že je textové pole **pracovní adresář** prázdné.

6. Vyberte možnost **použít vzdálený počítač** a do textového pole zadejte **yourmachinename: port** . (Číslo portu se zobrazí v okně vzdáleného ladicího programu. Číslo portu zvýší hodnotu 2 v každé verzi sady Visual Studio).

    V tomto příkladu použijte:
    ::: moniker range=">=vs-2019"
    **Mjo-DL: 4024** v aplikaci Visual Studio 2019
    ::: moniker-end
    ::: moniker range="vs-2017"
    **Mjo-DL: 4022** v aplikaci Visual Studio 2017
    ::: moniker-end

7. Ujistěte se, že není vybraná **možnost Povolit ladění nativního kódu** .

8. Sestavte projekt.

9. Vytvořte složku na vzdáleném počítači, která je stejná jako složka **ladění** v počítači se systémem Visual Studio: **\<source path> \MyWPF\MyWPF\bin\Debug**.

10. Zkopírujte spustitelný soubor, který jste právě vytvořili z počítače se systémem Visual Studio, do nově vytvořené složky ve vzdáleném počítači.

    > [!CAUTION]
    > Neprovádějte změny kódu nebo znovu sestavte (nebo je nutné tento krok zopakovat). Spustitelný soubor, který jste zkopírovali do vzdáleného počítače, se musí přesně shodovat s vaším místním zdrojem a symboly.

    Projekt můžete kopírovat ručně pomocí příkazu XCopy, Robocopy, PowerShellu nebo jiných možností.

11. Ujistěte se, že je na cílovém počítači spuštěný vzdálený ladicí program (Pokud není, vyhledejte v nabídce **Start** **vzdálený ladicí program** ). Okno vzdáleného ladicího programu vypadá takto.

     ![Snímek obrazovky s oknem vzdáleného ladicího programu sady Visual Studio 2017 V seznamu je uvedena jedna akce, která indikuje, že na cílovém počítači je spuštěný ladicí program.](../debugger/media/remotedebuggerwindow.png)

12. V aplikaci Visual Studio spusťte ladění (**ladění > spustit ladění** nebo **F5**).

13. Pokud se zobrazí výzva, zadejte síťové přihlašovací údaje pro připojení ke vzdálenému počítači.

     Požadovaná pověření se liší v závislosti na konfiguraci zabezpečení vaší sítě. Například v počítači domény můžete zadat název domény a heslo. Na počítači, který není doménou, můžete zadat název počítače a platný název uživatelského účtu, jako <strong>MJO-DL\name@something.com</strong> je, spolu se správným heslem.

     Mělo by se zobrazit, že je hlavní okno aplikace WPF otevřeno na vzdáleném počítači.

14. V případě potřeby proveďte akci, aby se zarážka narazí. Měla by se zobrazit, že je zarážka aktivní. Pokud tomu tak není, symboly pro aplikaci se nenačte. Zkuste to znovu, a pokud to nefunguje, Získejte informace o načítání symbolů a o tom, jak je řešit, v tématu [Principy souborů symbolů a nastavení symbolů sady Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).

15. Na počítači se systémem Visual Studio by se mělo zobrazit, že se na zarážce zastavilo provádění.

    Pokud máte nějaké soubory bez kódu, které musí aplikace používat, je nutné je zahrnout do projektu aplikace Visual Studio. Vytvořte složku projektu pro další soubory (v **Průzkumník řešení** klikněte na **Přidat > nová složka**). Pak přidejte soubory do složky (v **Průzkumník řešení** klikněte na **Přidat > existující položku** a pak vyberte soubory). Na stránce **vlastnosti** pro každý soubor nastavte vždy hodnotu **Kopírovat do výstupního adresáře** na **Kopírovat**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení ladění pomocí vzdálených symbolů

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)