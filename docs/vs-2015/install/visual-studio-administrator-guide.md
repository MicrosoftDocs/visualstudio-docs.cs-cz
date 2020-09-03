---
title: Příručka pro správce sady Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a59f9f2cb2548d6d40670832e66d4df5c83680df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295913"
---
# <a name="visual-studio-administrator-guide"></a>Příručka administrátora sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v příručce pro [správce sady Visual Studio](/visualstudio/install/visual-studio-administrator-guide).

Můžete nasadit Visual Studio 2015 v síti, pokud každý cílový počítač splňuje [minimální požadavky na instalaci](https://visualstudio.microsoft.com/vs/older-downloads/). Sdílenou síťovou složku můžete vytvořit spuštěním instalačního souboru s přepínačem/Layout (jak je popsáno na stránce [vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) ) a následným zkopírováním z místního počítače do sdílené síťové složky. Pokud používáte ISO, můžete připojit bitovou kopii ISO a sdílet ji nebo zkopírovat bitovou kopii ISO do sdílené síťové složky.  
  
 Instalace ze sdílené síťové složky si zapamatuje zdrojové umístění, ze kterého pocházejí. To znamená, že se může vyžadovat, aby se oprava klientského počítače vrátila do síťové sdílené složky, ze které klient původně nainstaloval. Vyberte své síťové umístění pečlivě, aby odpovídalo životnosti, kterou očekáváte, aby klienti sady Visual Studio 2015 ve vaší organizaci běželi.  
  
## <a name="detection-and-servicing-keys"></a>Klíče detekce a údržby  
 Pomocí zjišťování podklíčů v registru můžete zjistit, zda je produkt Visual Studio již nainstalován v počítači. Tyto detekční klíče byste použili v automatizovaném nasazení, abyste zjistili, jestli bylo nutné pokračovat v instalaci.  Viz [zjišťování požadavků na systém](../extensibility/internals/detecting-system-requirements.md)[zjištění požadavků na systém].  
  
## <a name="avoiding-reboots"></a>Zamezení restartování  
 Můžete snížit počet restartování tím, že před nasazením sady Visual Studio splníte příslušné předpoklady sady Visual Studio. Pro .NET Framework může být nutné restartovat počítače se systémem Windows 8, pokud nasadíte aplikaci Visual Studio 2015, aniž byste nejprve nainstalovali .NET Framework 4,6.  
  
 Pro emulaci zařízení s Windows a Androidem může být potřeba restartovat počítače, pokud ještě nemáte zapnutou funkci Hyper-V pro Windows. V případě vývoje webu může být nutné restartovat počítače, pokud ještě nemáte webový server funkce systému Windows zapnutý. V případě vývoje pro Office může být nutné restartovat počítače, pokud ještě nemáte funkci Windows Feature Foundation, která je zapnutá. Restartujte počítače, pokud ještě nemáte webový server funkcí systému Windows zapnutý. V případě vývoje pro Office může být nutné restartovat počítače, pokud ještě nemáte funkci Windows Feature Foundation, která je zapnutá. Další informace o tom, jak automatizovat detekci a instalaci funkcí Windows, najdete v tématu [instalace role serveru na serveru s instalací jádra serveru systému Windows server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Návratové kódy chyb  
 V následující tabulce jsou uvedeny důležité kódy chyb. Tyto kódy chyb v automatizaci můžete použít k určení, jestli je nutné restartovat počítač a jestli se instalace úspěšně dokončila. Pokud obdržíte kód chyby, zvažte postup řešení potíží na stránce [instalace sady Visual Studio](../install/install-visual-studio-2015.md) .  
  
|Stav instalace|Restartování není vyžadováno|Vyžadováno restartování|Popis|  
|------------------|--------------------------|----------------------|-----------------|  
|Success|0x00000000 [0]|0x00000bc2 [3010]|Úspěšná instalace.|  
|Blok|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Pokud je pouze hlášený blok "čeká na restartování", vrácená hodnota je povinná hodnota nedokončeného restartování (0x80048bc7).|  
|Zrušit|0x00000642 [1602]|0x80048642 [-2147187134]|Po vrácení hodnoty restart je návratový kód 1602.|  
|Nedokončeno – vyžadováno restartování|–|0x80048bc7 [-2147185721]|Aby mohla instalace pokračovat, je nutné restartovat počítač.|  
|Selhání|0x00000643 [1603]|0x80048643 [-2147187133]|Po vrácení hodnoty restart je návratový kód 1603.|  
  
## <a name="interactive-administrator-installer"></a>Interaktivní instalační program Správce  
 Pokud vytváříte interaktivní instalační program na začátku instalace sady Visual Studio, můžete zobrazit průběh z instalačního programu sady Visual Studio. Instalační program sady Visual Studio 2015 je založený na technologii Open Source Instalační služba systému Windows XML (WiX) chainer, která se označuje také jako "vypálit". Technologie pro vypalování podporuje dva komunikační protokoly: vypálit a netfx4. Stručný přehled naleznete v popisu atributu Protocol v dokumentaci pro element ExePackage na [wixtoolset.org](https://wixtoolset.org/). Pro integraci může být nutná kontrola implementace WiX Open Source tohoto atributu Protocol.  
  
## <a name="controlling-what-is-installed"></a>Řízení, co je nainstalováno  
 Pokud chcete určit, co může koncový uživatel instalovat, máte dvě možnosti: instalace souboru správce a možnosti příkazového řádku. Pokud je vaším cílem omezit, co si koncový uživatel může vybrat z instalačního programu sady Visual Studio, vyberte soubor správce nainstalovat. Vyberte parametry příkazového řádku, pokud chcete vytvořit počáteční konfiguraci, ale umožněte koncovému uživateli zvolit si vlastní instalační program sady Visual Studio.  
  
 Další informace o prostředí souborů správce najdete v tématu [Postup: vytvoření a spuštění bezobslužné instalace aplikace Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) a [Postup: automatické použití kódů Product Key při nasazení sady Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Další informace o ovládacích prvcích příkazového řádku naleznete na stránce [použití parametrů příkazového řádku pro instalaci sady Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) .  
  
## <a name="specifying-customer-feedback-settings"></a>Určení nastavení zpětné vazby od zákazníka  

Ve výchozím nastavení umožňuje instalace sady Visual Studio zpětnou vazbu od zákazníků. Sadu Visual Studio můžete nakonfigurovat tak, aby na jednotlivé počítače nemohly na jednotlivých počítačích změnit hodnotu následujícího klíče registru na řetězec "0":  
  
**HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
(Například změňte na HKEY_LOCAL_MACHINE \SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn = "0")  
  
## <a name="related-topics"></a>Související témata  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Postupy: Instalace konkrétní verze sady Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|V této části najdete popis postupu instalace konkrétních konfigurací aktuální verze nástroje  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|[Postupy: Vytvoření a spuštění bezobslužné instalace sady Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Popisuje instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v bezobslužném režimu.|  
|[Postupy: Automatické použití kódů Product Key při nasazení sady Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Popisuje způsob použití kódů Product Key při nasazení na více počítačů.|  
|[Příručka správce Help Vieweru](../ide/help-viewer-administrator-guide.md)|Obsahuje informace o tom, jak spravovat místní instalace aplikace Help pro síťová prostředí, která mají buď nebo nemají přístup k Internetu.|  
|[Instalace sady Visual Studio](../install/install-visual-studio-2015.md)|Obsahuje pokyny a odkazy na témata, která popisují, jak nainstalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|