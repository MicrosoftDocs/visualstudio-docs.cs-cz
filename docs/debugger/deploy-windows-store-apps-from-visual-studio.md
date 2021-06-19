---
title: Nasazení aplikací pro UPW | Microsoft Docs
description: Nasazení Univerzální platforma Windows (UPW) z Visual Studio. Zadejte místní nebo vzdálené cílové zařízení pro nasazení. Principy možností nasazení
ms.custom: SEO-VS-2020
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 0a1c1802d92beb436bbd2ac87bd1e7a39f6086f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387863"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Nasazení aplikací pro UPW ze sady Visual Studio

Funkce Visual Studio nasazení sestaví a zaregistruje aplikace pro UPW, které jsou vytvořené Visual Studio na cílovém zařízení. Přesně to, jak je aplikace zaregistrovaná, závisí na tom, jestli je cílové zařízení místní nebo vzdálené:

- Pokud je cílem místní Visual Studio, Visual Studio aplikace zaregistruje ze složky sestavení.

- Pokud je cílem vzdálené zařízení, Visual Studio požadované soubory zkopíruje do vzdáleného počítače a zaregistruje aplikaci na tomto zařízení.

Nasazení je automatické při ladění aplikace z Visual Studio  pomocí možnosti Spustit ladění (klávesnice: F5) nebo možnosti Spustit bez **ladění** (klávesnice: CTRL + F5). Aplikaci můžete nasadit také ručně. Ruční nasazení je užitečné v následujících scénářích:

- Jednorázové testování na místním nebo vzdáleném počítači.

- Nasazení aplikace, která spustí jinou aplikaci, kterou chcete ladit

- Nasazení aplikace, která se bude ladit při spuštění jinou aplikací nebo metodou

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Postup nasazení aplikace pro UPW
 Ruční nasazení aplikace je jednoduchý proces:

1. Pokud nasazujete na vzdálené zařízení, zadejte název nebo IP adresu zařízení na stránce projektu vlastností projektu po spuštění aplikace. (Postup je uvedený dále v tomto tématu.)

2. Na panelu Visual Studio ladicího programu vyberte cíl nasazení z rozevíracího seznamu vedle tlačítka **Spustit** ladění.

     ![Spuštění na místním počítači](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. V **nabídce Sestavení** zvolte **Nasadit.**

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Určení vzdáleného zařízení

**Požadavky**

Na Windows 10 zařízení musíte povolit [vývojářský režim](/windows/uwp/get-started/enable-your-device-for-development). Na Windows 10, na které běží Creator's Update nebo novější, se vzdálené nástroje automaticky nainstalují při nasazení aplikace. Další informace najdete v tématu [Ladění nainstalovaného balíčku aplikace.](../debugger/debug-installed-app-package.md)

> [!NOTE]
> V předchozích verzích sady Update Windows 10 musí být Remote Tools for Visual Studio na vzdáleném zařízení nainstalován a musí být spuštěný vzdálený ladicí program.

Nasazení používá síťový kanál vzdáleného ladicího programu k odesílání souborů aplikace do vzdáleného zařízení.

#### <a name="to-specify-a-remote-device"></a>Určení vzdáleného zařízení

1. Na stránce vlastností Ladění projektu po spuštění zadejte název nebo IP adresu cíle vzdáleného nasazení.

2. Pokud chcete otevřít stránku vlastností Ladění, zvolte projekt v Průzkumník řešení a pak **v** místní nabídce zvolte Vlastnosti.

3. Pak zvolte **uzel Ladit** v okně stránek vlastností.

4. V **oblasti Cílové zařízení** vyberte Vzdálený **počítač.**

5. V **části Vzdálený počítač** klikněte na **Najít.**

6. Můžete zadat název nebo IP adresu vzdáleného zařízení, nebo můžete zařízení zvolit v dialogovém **okně Vzdálené** připojení.

    ![Dialogové okno Vybrat připojení vzdáleného ladicího programu](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    V **dialogovém okně Vzdálené** připojení se zobrazí zařízení v podsíti místní sítě a všechna zařízení, která jsou přímo připojená k virtuálnímu počítači Visual Studio pomocí ethernetového kabelu.

   **Zadání vzdáleného zařízení na stránce projektu C++**

   ![Vlastnosti&#43;&#43; C pro vzdálené ladění](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. V **ladicím programu** zvolte Vzdálený **ladicí program, aby se spouštěl** seznam.

8. Do pole Název počítače zadejte název sítě **vzdáleného** zařízení. Nebo můžete zvolit šipku dolů v poli a vybrat zařízení z dialogového okna Vybrat připojení vzdáleného ladicího programu.

   **Určení vzdáleného zařízení v jazyce Visual C# a na Visual Basic projektu**

   ![Vlastnosti spravovaného projektu pro vzdálené ladění](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. V **seznamu Cílové** zařízení zvolte **Vzdálený** počítač.

10. Do pole Vzdálený počítač zadejte  název sítě vzdáleného zařízení nebo klikněte na Najít a zvolte zařízení v dialogovém okně Vybrat připojení vzdáleného **ladicího** programu. 

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Možnosti nasazení

Na stránce vlastností Ladění projektu po spuštění můžete nastavit následující možnosti nasazení.

**Povolit zpětné smyčky sítě**

Z bezpečnostních důvodů nesmí UPW nebo aplikace, která je nainstalovaná standardním způsobem, provádět síťová volání zařízení, [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] na které je nainstalovaná. Ve výchozím Visual Studio nasazení vytvoří výjimku z tohoto pravidla pro nasazenou aplikaci. Tato výjimka umožňuje otestovat komunikační postupy na jednom počítači. Před odesláním aplikace do [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] byste měli aplikaci otestovat bez výjimky.

Odebrání výjimky zpětné smyčky sítě z aplikace:

- Na stránce vlastností C# Visual Basic Ladění zrušte zaškrtnutí **políčka Povolit** zpětné smyčky sítě.

- Na stránce vlastností Ladění jazyka C++ nastavte hodnotu Povolit zpětné smyčky **sítě** na **Hodnotu Ne.**

**Nespouštět, ale ladit kód při spuštění (C# a Visual Basic) / Spustit aplikaci (C++)**

Konfigurace nasazení pro automatické spuštění ladicí relace při spuštění aplikace:

- Na stránce vlastností C# Visual Basic Ladění zaškrtněte  políčko Nespouštět, ale při spuštění ladit kód.

- Na stránce vlastností Ladění jazyka C++ nastavte **hodnotu Spustit** aplikaci na **Ano.**

## <a name="see-also"></a>Viz také

- [Pokročilé možnosti vzdáleného nasazení](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Ladění balíčku nainstalované aplikace](../debugger/debug-installed-app-package.md)
- [Spouštění aplikací ze sady Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
