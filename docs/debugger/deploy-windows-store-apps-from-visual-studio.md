---
title: Nasazení aplikací pro UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 4c58dbb32ef0a476ac7e22a840e27e389c710f97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "73188277"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Nasazení aplikací pro UPW ze sady Visual Studio

Funkce nasazení sady Visual Studio vytváří a registruje aplikace UWP vytvořené pomocí sady Visual Studio na cílovém zařízení. Přesně to, jak je aplikace zaregistrovaná, závisí na tom, jestli je cílové zařízení místní nebo vzdálené:

- Pokud je cílem místní počítač sady Visual Studio, aplikace Visual Studio zaregistruje aplikaci ze své složky sestavení.

- Pokud je cílem vzdálené zařízení, Visual Studio zkopíruje požadované soubory do vzdáleného počítače a zaregistruje aplikaci na tomto zařízení.

Nasazení je automatické při ladění aplikace ze sady Visual Studio pomocí možnosti **Spustit ladění** (klávesnice: F5) nebo možnosti **Spustit bez ladění** (klávesnice: CTRL + F5). Aplikaci můžete nasadit také ručně. Ruční nasazení je užitečné v následujících scénářích:

- Testování ad hoc na místním nebo vzdáleném počítači.

- Nasazení aplikace, která spustí jinou aplikaci, kterou chcete ladit.

- Nasazení aplikace, která se bude ladit při spuštění jinou aplikací nebo metodou

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Nasazení aplikace pro UWP
 Ruční nasazení aplikace je jednoduchý proces:

1. Pokud nasazujete na vzdálené zařízení, zadejte název nebo IP adresu zařízení na stránce projekt vlastností spouštěného projektu aplikace. (Tento postup je uveden dále v tomto tématu.).

2. Na panelu nástrojů ladicího programu sady Visual Studio v rozevíracím seznamu vedle tlačítka **Spustit ladění** vyberte cíl nasazení.

     ![Spustit na místním počítači](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. V nabídce **sestavení** klikněte na příkaz **nasadit** .

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Určení vzdáleného zařízení

**Požadavky**

Na vzdáleném zařízení s Windows 10 musíte povolit [vývojářský režim](/windows/uwp/get-started/enable-your-device-for-development). Na zařízeních s Windows 10, na kterých běží aktualizace autora nebo novější, se nástroje Remote Tools automaticky nainstalují při nasazení aplikace. Další informace najdete v tématu [ladění nainstalovaného balíčku aplikace](../debugger/debug-installed-app-package.md).

> [!NOTE]
> V případě aktualizací verze Windows 10 předběžného autora musí být na vzdáleném zařízení nainstalovaný Remote Tools for Visual Studio a musí běžet vzdálený ladicí program.

Nasazení používá síťový kanál vzdáleného ladícího programu k posílání souborů aplikace na vzdálené zařízení.

#### <a name="to-specify-a-remote-device"></a>Určení vzdáleného zařízení

1. Na stránce vlastností ladění spouštěného projektu zadejte název nebo IP adresu cíle vzdáleného nasazení.

2. Chcete-li otevřít stránku vlastností ladění, zvolte projekt v Průzkumník řešení a pak v místní nabídce zvolte možnost **vlastnosti** .

3. Pak zvolte uzel **ladění** v okně stránky vlastností.

4. V případě **cílového zařízení**vyberte možnost **vzdálený počítač**.

5. V části **vzdálený počítač**klikněte na **Najít**.

6. Můžete zadat název nebo IP adresu vzdáleného zařízení nebo můžete vybrat zařízení z dialogového okna **vzdálené připojení** .

    ![Dialogové okno vybrat připojení vzdáleného ladicího programu](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    Dialogové okno **vzdálené připojení** zobrazuje zařízení v podsíti místní sítě a všechna zařízení, která jsou přímo připojena k počítači sady Visual Studio pomocí kabelu sítě Ethernet.

   **Určení vzdáleného zařízení na stránce projektu C++**

   ![Vlastnosti projektu v jazyce C&#43;&#43; pro vzdálené ladění](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Pro spuštění seznamu vyberte možnost **vzdálený ladicí program** z **ladicího programu** .

8. Do pole **název počítače** zadejte název sítě vzdáleného zařízení. Případně můžete vybrat šipku dolů v poli a vybrat zařízení z dialogového okna Vybrat připojení vzdáleného ladicího programu.

   **Určení vzdáleného zařízení na stránce projektu Visual C# a Visual Basic**

   ![Vlastnosti spravovaného projektu pro vzdálené ladění](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. V seznamu **cílový seznam zařízení** vyberte možnost **vzdálený počítač** .

10. Zadejte síťový název vzdáleného zařízení do pole **vzdálený počítač** nebo klikněte na **Najít** a zvolte zařízení v dialogovém okně **Vybrat připojení vzdáleného ladicího programu** .

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Možnosti nasazení

Na stránce vlastností ladění spouštěného projektu můžete nastavit následující možnosti nasazení.

**Povolení zpětné smyčky sítě**

Z bezpečnostních důvodů není u UWP nebo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace, která je nainstalovaná standardním způsobem, povoleno provádět síťová volání do zařízení, na kterém je nainstalovaná. Ve výchozím nastavení vytvoří nasazení sady Visual Studio výjimku z tohoto pravidla pro nasazenou aplikaci. Tato výjimka umožňuje testovat komunikační postupy na jednom počítači. Před odesláním aplikace do nástroje [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] byste měli aplikaci otestovat bez výjimky.

Odebrání výjimky zpětné smyčky sítě z aplikace:

- Na stránce vlastností C# a Visual Basic ladění zrušte zaškrtnutí políčka **Povolení zpětné smyčky sítě** .

- Na stránce vlastností ladění v jazyce C++ nastavte hodnotu **zapnout síťovou smyčku** na **ne**.

**Nespouštět, ale ladit můj kód při spuštění (C# a Visual Basic)/spustit aplikaci (C++)**

Konfigurace nasazení tak, aby automaticky spouštěla relaci ladění při spuštění aplikace:

- Na stránce vlastností C# a Visual Basic Debug zaškrtněte políčko **nespouštět, ale při spuštění ladit můj kód** .

- Na stránce vlastností ladění v jazyce C++ nastavte hodnotu **Spustit aplikaci** na **Ano**.

## <a name="see-also"></a>Viz také

- [Rozšířené možnosti vzdáleného nasazení](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Ladění balíčku nainstalované aplikace](../debugger/debug-installed-app-package.md)
- [Spouštění aplikací ze sady Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
