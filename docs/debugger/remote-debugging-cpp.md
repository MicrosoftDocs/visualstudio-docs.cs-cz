---
title: Vzdálené ladění projektu jazyka C++ | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302110"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Vzdálené ladění projektu C++ v sadě Visual Studio
Chcete-li ladit aplikaci sady Visual Studio v jiném počítači, nainstalujte a spusťte vzdálené nástroje v počítači, ve kterém budete aplikaci nasazovat, nakonfigurujte projekt tak, aby se připojil ke vzdálenému počítači z visual studia, a potom aplikaci nasazujte a spouštějte.

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

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a>Vzdálené ladění projektu jazyka C++
 V následujícím postupu je název a cesta projektu C:\remotetemp\MyMfc a název vzdáleného počítače je **MJO-DL**.

1. Vytvořte aplikaci knihovny MFC s názvem **mymfc.**

2. Nastavte zarážku někde v aplikaci, která je snadno dosažitelná, například `CMainFrame::OnCreate`v **MainFrm.cpp**, na začátku .

3. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **vlastnosti**. Otevřete kartu **Ladění.**

4. Nastavte **ladicí program pro spuštění** do **vzdáleného ladicího programu systému Windows**.

    ![Vzdálené laděníCPlus](../debugger/media/remotedebuggingcplus.png "Vzdálené laděníCPlus")

5. Proveďte následující změny vlastností:

   |Nastavení|Hodnota|
   |-|-|
   |Vzdálený příkaz|C:\remotetemp\mymfc.exe|
   |Pracovní adresář|C:\remotetemp|
   |Název vzdáleného serveru|MJO-DL:*číslo portu*|
   |Připojení|Vzdálené ověřování systému Windows|
   |Typ ladicího programu|Pouze nativní|
   |Adresář nasazení|C:\remotetemp.|
   |Další soubory k nasazení|C:\data\mymfcdata.txt.|

    Pokud nasadíte další soubory (volitelné), složka musí existovat na obou počítačích.

6. V Průzkumníku řešení klepněte pravým tlačítkem myši na řešení a zvolte **Configuration Manager**.

7. V konfiguraci **ladění** zaškrtněte políčko **Nasadit.**

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Spusťte ladění (**ladění > spuštění ladění**nebo **F5**).

9. Spustitelný soubor je automaticky nasazen do vzdáleného počítače.

10. Po zobrazení výzvy zadejte síťová pověření pro připojení ke vzdálenému počítači.

     Požadovaná pověření jsou specifická pro konfiguraci zabezpečení sítě. Například v počítači domény můžete zvolit certifikát zabezpečení nebo zadat název domény a heslo. V počítači, který není v doménovém počítači, můžete <strong>MJO-DL\name@something.com</strong>zadat název počítače a platný název uživatelského účtu, například , spolu se správným heslem.

11. V počítači sady Visual Studio byste měli vidět, že spuštění je zastaveno na zarážky.

    > [!TIP]
    > Případně můžete nasadit soubory jako samostatný krok. V **Průzkumníku řešení** klikněte pravým tlačítkem myši na uzel **mymfc** a pak zvolte **Nasadit**.

    Pokud máte soubory, které nejsou kódové, které jsou vyžadovány aplikací, můžete je zadat v **části Další soubory k nasazení** na stránce **Vzdáleného ladicího programu systému Windows.**

    Případně můžete zahrnout soubory do projektu a nastavit vlastnost **Content** na **Ano** na stránce **Vlastnosti** pro každý soubor. Tyto soubory jsou zkopírovány do **adresáře nasazení** určeného na stránce **Vzdálené ho ladicího programu systému Windows.** Můžete také změnit **typ položky** na **Kopírovat soubor** a zadat další vlastnosti, pokud potřebujete soubory, které mají být zkopírovány do podsložky **adresáře nasazení**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení ladění pomocí vzdálených symbolů

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET na vzdáleném počítači se službou IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby a řešení potíží se vzdáleným laděním](../debugger/remote-debugging-errors-and-troubleshooting.md)