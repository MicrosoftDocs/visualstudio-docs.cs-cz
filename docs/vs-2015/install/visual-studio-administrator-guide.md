---
title: Příručka správce sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 25d6655969245adf1b2a28df2b3327561d149983
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722822"
---
# <a name="visual-studio-administrator-guide"></a>Příručka administrátora sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci pro sadu Visual Studio 2017, najdete v článku [příručce pro správce sady Visual Studio 2017](/visualstudio/install/visual-studio-administrator-guide).

Visual Studio 2015 můžete nasadit v síti, tak dlouho, dokud každý cílový počítač splňuje [minimální požadavky na instalaci](http://www.microsoft.com/visualstudio/eng/products/2013-editions). Sdílené síťové složky můžete vytvořit spuštěním instalační soubor s přepínačem/Layout (jak je popsáno na [vytvoření v režimu Offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) stránky) a následným kopírováním z místního počítače do sdílené síťové složky. Pokud použijete Image ISO, můžete připojit bitovou kopii ISO a sdílet ho nebo zkopírovat bitovou kopii ISO do sdílené síťové složky.  
  
 Všimněte si, že instalace ze sdílené síťové složky "nezapomeňte" umístění zdroje, které pocházejí. To znamená, že oprava klientského počítače může být nutné se vraťte do sdílené síťové složky, které klient původně nainstalovali. Pečlivě vašemu umístění v síti tak, aby se budou přizpůsobovat dostupnému prostoru životního cyklu, které plánujete mít Visual Studio 2015 klientů se systémy ve vaší organizaci.  
  
## <a name="detection-and-servicing-keys"></a>Detekce a obsluha klíčů  
 Detekce podklíčů v registru můžete použít k určení, zda je v počítači již nainstalován produkt Visual Studio. Automatizované nasazení můžete využít tyto klíče detekce k určení, zda to bylo nezbytné, aby bylo možné pokračovat v instalaci aplikace.  Zobrazit [zjištění požadavků na systém](../extensibility/internals/detecting-system-requirements.md)[zjištění požadavků na systém].  
  
## <a name="avoiding-reboots"></a>Vyhnout se restartování počítače  
 Restartování počítače můžete snížit a ujistěte se, že splňujete požadavky odpovídající sady Visual Studio před nasazením aplikace Visual Studio. Pro rozhraní .NET Framework může být nutné restartování počítačů, na kterých běží Windows 8, pokud provádíte nasazení sady Visual Studio 2015 na nich bez první instalace rozhraní .NET Framework 4.6.  
  
 Pro emulaci zařízení Windows a Androidem může být nutné restartování počítačů, pokud již nemáte Windows funkce, kterou technologie Hyper-V zapnutá. Pro vývoj webů budete muset restartovat počítače, pokud již nemáte funkci Windows, které webový Server zapnutý. Pro vývoj pro Office budete muset restartovat počítače, pokud již nemáte funkce Windows Foundation identifikovat Windows zapnuté. Pokud již nemáte funkci Windows, které webový Server zapnutý, až po restartování počítače. Pro vývoj pro Office budete muset restartovat počítače, pokud již nemáte funkce Windows Foundation identifikovat Windows zapnuté. Další informace o tom, jak automatizovat zjišťování a instalaci funkcí Windows, naleznete v tématu [instalaci role serveru na serveru s instalací jádra serveru systému Windows Server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Návratové kódy chyb  
 Následující tabulka obsahuje seznam důležitých kódů chyb. Tyto kódy chyb ve vaší službě automation můžete rozhodnout, jestli je vyžadován restart a v případě, instalace proběhla úspěšně. Pokud se zobrazí kód chyby, zvažte kroky pro řešení potíží na [instalace sady Visual Studio](../install/install-visual-studio-2015.md) stránky.  
  
|Stav instalace|Restartování není požadováno|Vyžadováno restartování|Popis|  
|------------------|--------------------------|----------------------|-----------------|  
|Úspěch|0x00000000 [0]|0x00000bc2 [3010]|Úspěšná instalace.|  
|Blok|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Pokud uváděné pouze blok "Čeká na restartování", vrácená hodnota je hodnota nekompletní restart (0x80048bc7).|  
|Zrušit|0x00000642 [1602]|0x80048642 [-2147187134]|Pokud je vrácena hodnota Reboot, návratový kód bude 1602.|  
|Neúplné restart|Není k dispozici|0x80048bc7 [-2147185721]|Před pokračováním instalace je vyžadováno restartování.|  
|selhání|0x00000643 [1603]|0x80048643 [-2147187133]|Pokud je vrácena hodnota Reboot, návratový kód je 1603.|  
  
## <a name="interactive-administrator-installer"></a>Instalační program interaktivní správce  
 Pokud vytváříte interaktivní instalační program na instalaci sady Visual Studio, můžete zobrazit průběh v instalačním programu sady Visual Studio. Visual Studio 2015, které instalační program je založená na open source technologie chainer XML Instalační služby systému Windows (WiX), označované také jako "pracovní tempo." Pracovní tempo technologie podporuje dva komunikační protokoly: pracovní tempo a netfx4. Krátký odkaz, najdete v tématu Popis v dokumentaci pro element ExePackage v atributu protokolu [wixtoolset.org](http://wixtoolset.org/). Přehled WiX opensourcová implementace tohoto atributu protokol může být nutný pro integraci.  
  
## <a name="controlling-what-is-installed"></a>Řízení, co je nainstalována  
 Pokud chcete řídit, co koncový uživatel může nainstalovat, existují dvě možnosti: Správce souborů instalaci a možnosti příkazového řádku. Vyberte souboru instalace správce, pokud je vaším cílem je omezit, co koncový uživatel můžete vybrat z jejich prostředí instalačního programu sady Visual Studio. Pokud chcete vytvořit počáteční konfiguraci, ale povolit váš koncový uživatel vybrat své vlastní prostředí instalačního programu sady Visual Studio, vyberte parametry příkazového řádku.  
  
 Další informace o souboru prostředí správce, naleznete v tématu [postupy: vytvoření a spuštění bezobslužné instalace sady Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) a [postupy: automatické použití kódů product key při nasazení sady Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Další informace o řízení příkazového řádku, najdete v článku [použití parametrů příkazového řádku instalace sady Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) stránky.  
  
## <a name="specifying-customer-feedback-settings"></a>Určení nastavení zpětné vazby zákazníka  
 Ve výchozím nastavení instalaci sady Visual Studio umožňuje zpětné vazby od zákazníků. Visual Studio a zakázání zpětné vazby od zákazníků v jednotlivých počítačích změnou hodnoty následujícího klíče registru na řetězec "0", můžete nakonfigurovat:  
  
 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
 (Třeba, změňte ho na HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn = "0")  
  
## <a name="related-topics"></a>Související témata  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Postupy: Instalace konkrétní verze sady Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|Popisuje postup instalace konkrétní konfigurace k aktuální verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Postupy: Vytvoření a spuštění bezobslužné instalace sady Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Popisuje postup instalace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v bezobslužném režimu.|  
|[Postupy: Automatické použití kódů Product Key při nasazení sady Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Popisuje způsob použití kódů product key při nasazení do více počítačů.|  
|[Příručka správce Help Vieweru](../ide/help-viewer-administrator-guide.md)|Poskytuje informace o tom, jak spravovat místní instalace nápovědy pro síťové prostředí, které mají nebo nemají přístup k Internetu.|  
|[Instalace sady Visual Studio](../install/install-visual-studio-2015.md)|Poskytuje pokyny a odkazy na témata, která popisují, jak nainstalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|