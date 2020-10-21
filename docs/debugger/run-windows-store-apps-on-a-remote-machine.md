---
title: Ladění aplikací pro UWP na vzdálených počítačích | Microsoft Docs
ms.date: 10/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: c8e8305cb454bfc9f0fb0be4b9964ac1a7e4fe96
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2020
ms.locfileid: "92298715"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Ladění aplikací pro UWP na vzdálených počítačích ze sady Visual Studio

Můžete použít Visual Studio ke spouštění, ladění, profilování a testování aplikace Univerzální platforma Windows (UWP) na jiném počítači nebo zařízení. Spuštění aplikace UWP na vzdáleném počítači je zvlášť užitečné, pokud počítač s aplikací Visual Studio nepodporuje funkce specifické pro UWP, jako je dotykové ovládání, geografické umístění nebo fyzická orientace.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Požadovaný

Ladění aplikace UWP na vzdáleném zařízení ze sady Visual Studio:

- Projekt sady Visual Studio musí být nakonfigurován pro vzdálené ladění.
- Vzdálený počítač a počítač se systémem Visual Studio musí být připojeny přes síť nebo připojeny přímo přes kabel USB nebo Ethernet. Ladění po Internetu není podporováno.
- [Vývojářský režim](/windows/uwp/get-started/enable-your-device-for-development) je nutné zapnout jak na počítači aplikace Visual Studio, tak na vzdáleném počítači.
- Na vzdálených počítačích musí být spuštěný Remote Tools for Visual Studio.
  - Některé verze Windows 10 spouští a spouštějí vzdálené nástroje automaticky. V opačném případě [nainstalujte a spusťte Remote Tools for Visual Studio](#BKMK_download).
  - Zařízení se systémem Windows Mobile 10 nevyžadují nebo nepodporují nástroje Remote Tools.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Konfigurace projektu Visual studia pro vzdálené ladění
<a name="BKMK_DirectConnect"></a>**Vlastnosti** projektu můžete použít k určení vzdáleného zařízení, ke kterému se chcete připojit. Nastavení se liší v závislosti na programovacím jazyce.

> [!CAUTION]
> Ve výchozím nastavení stránka vlastností nastaví **univerzální (nešifrovaný protokol)** jako **typ ověřování** pro vzdálená připojení Windows 10. Možná budete muset nastavit **žádné ověřování** pro připojení ke vzdálenému ladicímu programu. **Univerzální (nešifrovaný protokol)** a **žádné ověřovací** protokoly neobsahují zabezpečení sítě, takže data předaná mezi vývojem a vzdálenými počítači jsou zranitelná. Tyto typy ověřování vyberte jenom pro důvěryhodné sítě, které jste si jisti, že nehrozí riziko škodlivých nebo nepřátelských přenosů.
>
>Pokud pro **typ ověřování**zvolíte **ověřování systému Windows** , bude nutné se přihlásit ke vzdálenému počítači při ladění. Vzdálený ladicí program musí být spuštěný v režimu **ověřování systému Windows** se stejným uživatelským účtem jako na počítači sady Visual Studio.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Konfigurace projektu v jazyce C# nebo Visual Basic pro vzdálené ladění

1. V aplikaci Visual Studio vyberte projekt C# nebo Visual Basic **Průzkumník řešení** a vyberte ikonu **vlastnosti** , stiskněte klávesu **ALT** + **ENTER**nebo klikněte pravým tlačítkem myši a zvolte možnost **vlastnosti**.

1. Vyberte kartu **ladit** .

1. V části **cílové zařízení**vyberte **vzdálený** počítač pro vzdálený počítač nebo **zařízení** pro zařízení s Windows Mobile 10 připojené přímo.

1. U vzdáleného počítače zadejte do pole **vzdálený počítač** název sítě nebo IP adresu, nebo vyberte **Najít** pro vyhledání zařízení v [dialogovém okně vzdálené připojení](#remote-connections).

    ![Vlastnosti spravovaného projektu pro vzdálené ladění](../debugger/media/vsrun_managed_projprop_remote.png "Vlastnosti spravovaného projektu ladění")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Konfigurace projektu C++ pro vzdálené ladění

1. Vyberte projekt C++ v aplikaci Visual Studio **Průzkumník řešení** a vyberte ikonu **vlastnosti** , stiskněte klávesu **ALT** + **ENTER**nebo klikněte pravým tlačítkem myši a zvolte možnost **vlastnosti**.

1. Vyberte kartu **ladění** .

3. V části **ladicí program, který se má spustit**, vyberte **vzdálený** počítač pro vzdálený počítač nebo **zařízení** pro zařízení s Windows Mobile 10 připojené přímo.

1. U vzdáleného počítače zadejte nebo vyberte název sítě nebo IP adresu v poli **název počítače** nebo rozevírací seznam a vyberte **Najít** , pokud chcete zařízení vyhledat v [dialogovém okně Vzdálená připojení](#remote-connections).

    ![Vlastnosti projektu C++ pro vzdálené ladění](../debugger/media/vsrun_cpp_projprop_remote.png "C++ – vlastnosti projektu ladění")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Použití dialogového okna Vzdálená připojení

V dialogovém okně **Vzdálená připojení** můžete vyhledat konkrétní název vzdáleného počítače nebo IP adresu nebo automaticky zjišťovat připojení tak, že vyberete ikonu s kulatou šipkou obnovit. Dialogové okno vyhledá pouze zařízení v místní podsíti, v nichž je aktuálně spuštěn vzdálený ladicí program. Ne všechna zařízení mohou být zjištěna v dialogovém okně **Vzdálená připojení** .

 ![Dialogové okno vzdálené připojení](../debugger/media/vsrun_selectremotedebuggerdlg.png "Dialogové okno vzdálených připojení")

>[!TIP]
>Pokud se nemůžete připojit ke vzdálenému zařízení podle názvu, zkuste použít jeho IP adresu. IP adresu určíte tak, že na vzdáleném zařízení zadáte **ipconfig** v příkazovém okně. IP adresa se zobrazí jako **IPv4 adresa**.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Stažení a instalace Remote Tools for Visual Studio

Aby mohla aplikace Visual Studio ladit aplikace na vzdáleném počítači, musí na vzdáleném počítači běžet Remote Tools for Visual Studio.

- Zařízení se systémem Windows Mobile 10 nevyžadují nebo nepodporují nástroje Remote Tools.
- Počítače s Windows 10, na kterých běží aktualizace autora (verze 1703) a novější, zařízení s Windows 10 Xbox, IoT a HoloLens při nasazení aplikace automaticky nainstalují vzdálené nástroje.
- Na počítačích s Windows 10, které jsou předem Creator, je nutné ručně stáhnout, nainstalovat a spustit nástroje Remote Tools na vzdáleném počítači, než začnete s laděním.

**Stažení a instalace nástrojů Remote Tools:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Konfigurace nástrojů Remote Tools

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> Vzdálené ladění aplikací pro UWP

Vzdálené ladění funguje stejně jako místní ladění.

1. V případě aktualizací verze Windows 10 předběžného autora se ujistěte, že na vzdáleném zařízení běží Sledování vzdáleného ladění (*msvsmon.exe*).

1. V počítači se systémem Visual Studio se ujistěte, že je na panelu nástrojů vedle zelené šipky zobrazen správný cíl ladění (**vzdálený počítač** nebo **zařízení**).

1. Spusťte ladění tak, že vyberete **ladění**  >  **Spustit ladění**, stisknete klávesu **F5**nebo vyberete zelenou šipku na panelu nástrojů.

   Projekt se překompiluje a pak se nasadí a spustí na vzdáleném zařízení. Ladicí program pozastaví provádění na zarážekch a můžete krokovat s kódem.

1. V případě potřeby vyberte **ladit**  >  **Zastavit ladění** nebo stiskněte **SHIFT** + **F5** , abyste zastavili ladění a zavřeli vzdálenou aplikaci.

## <a name="see-also"></a>Viz také
- [Rozšířené možnosti vzdáleného nasazení](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Testování aplikací pro UWP se sadou Visual Studio](../test/unit-test-your-code.md)
- [Ladění aplikací pro UWP v sadě Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
