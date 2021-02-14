---
title: Vzdálené ladění projektu C++ | Microsoft Docs
description: Naučte se, jak ladit aplikaci Visual Studio C++ ze vzdáleného počítače pomocí následujících podrobných pokynů.
ms.custom: remotedebugging
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
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: d7723a87471b8f76b9496fe8e7b01e56d1440ee2
ms.sourcegitcommit: 15109ead7991f52092502518a6f4d9061cc22cd2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2021
ms.locfileid: "100335265"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Vzdálené ladění projektu C++ v aplikaci Visual Studio
Chcete-li ladit aplikaci Visual Studio na jiném počítači, nainstalujte a spusťte nástroje Remote Tools v počítači, kde budete nasazovat aplikaci, nakonfigurujte projekt tak, aby se připojil ke vzdálenému počítači ze sady Visual Studio, a potom aplikaci nasaďte a spusťte.

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

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> Vzdálené ladění projektu C++
 V následujícím postupu je název a cesta k projektu C:\remotetemp\MyMfc a název vzdáleného počítače je **mjo-DL**.

1. Vytvořte aplikaci knihovny MFC s názvem **mymfc.**

2. Nastavte zarážku někde v aplikaci, která je snadno dostupná, například v **mainfrm. cpp** na začátku `CMainFrame::OnCreate` .

3. V Průzkumník řešení klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. Otevřete kartu **ladění** .

4. Nastavte **ladicí program na spouštění** pro **vzdálený ladicí program systému Windows**.

    ![Snímek obrazovky karty ladění ve vlastnostech Průzkumník řešení sady Visual Studio Vlastnost ladicího programu na spuštění je nastavená na vzdálený ladicí program systému Windows.](../debugger/media/remotedebuggingcplus.png)

5. Proveďte následující změny vlastností:

   |Nastavení|Hodnota|
   |-|-|
   |Vzdálený příkaz|C:\remotetemp\mymfc.exe|
   |Pracovní adresář|C:\remotetemp|
   |Název vzdáleného serveru|MJO-DL:*číslo_portu*|
   |Připojení|Vzdálený s ověřováním systému Windows|
   |Typ ladicího programu|Pouze nativní|
   |Adresář nasazení|C:\remotetemp.|
   |Další soubory k nasazení|C:\data\mymfcdata.txt.|

    Pokud nasadíte další soubory (volitelné), složka musí existovat na obou počítačích.

6. V Průzkumník řešení klikněte pravým tlačítkem na řešení a vyberte možnost **Configuration Manager**.

7. V případě konfigurace **ladění** zaškrtněte políčko **nasadit** .

    ![Snímek obrazovky Configuration Manager v Průzkumník řešení sady Visual Studio. Je zvolená konfigurace ladění a je zaškrtnuté políčko nasadit.](../debugger/media/remotedebugcplusdeploy.png)

8. Spusťte ladění (**ladění > spustit ladění** nebo **F5**).

9. Spustitelný soubor se automaticky nasadí do vzdáleného počítače.

10. Pokud se zobrazí výzva, zadejte síťové přihlašovací údaje pro připojení ke vzdálenému počítači.

     Požadovaná pověření jsou specifická pro konfiguraci zabezpečení vaší sítě. Například v počítači domény můžete zvolit certifikát zabezpečení nebo zadat název domény a heslo. Na počítači, který není doménou, můžete zadat název počítače a platný název uživatelského účtu, jako <strong>MJO-DL\name@something.com</strong> je, spolu se správným heslem.

11. V počítači se systémem Visual Studio by se mělo zobrazit, že je spuštění zastaveno na zarážce.

    > [!TIP]
    > Případně můžete soubory nasadit jako samostatný krok. V **Průzkumník řešení** klikněte pravým tlačítkem na uzel **mymfc** a pak zvolte **nasadit**.

    Pokud máte soubory bez kódu, které jsou vyžadovány aplikací, můžete je zadat v seznamu s **dalšími soubory, které mají být nasazeny** na stránce **vzdáleného ladicího programu systému Windows** .

    Alternativně můžete zahrnout soubory do projektu a nastavit vlastnost **obsah** na **hodnotu Ano** na stránce **vlastnosti** pro každý soubor. Tyto soubory jsou zkopírovány do **adresáře nasazení** zadaného na stránce **vzdáleného ladicího programu systému Windows** . Můžete také změnit **typ položky** na **Kopírovat soubor** a zadat další vlastnosti tam, kde potřebujete zkopírovat soubory do podsložky **adresáře nasazení**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení ladění pomocí vzdálených symbolů

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)