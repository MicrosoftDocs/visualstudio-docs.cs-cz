---
title: Instalace certifikátů pro instalaci offline
description: Naučte se instalovat certifikáty pro instalaci sady Visual Studio v režimu offline.
ms.date: 03/29/2021
ms.custom: seodec18, SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6dc4137157e2fa5136a0b8c86c5cf72f284a9eb7
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307373"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Instalace certifikátů vyžadovaných pro instalaci sady Visual Studio offline

Aplikace Visual Studio je primárně navržena pro instalaci na počítač připojený k Internetu, protože mnoho komponent je pravidelně aktualizováno. Nicméně s některými dalšími kroky je možné nasadit aplikaci Visual Studio do prostředí, kde není k dispozici funkční připojení k Internetu.

Instalační modul sady Visual Studio nainstaluje jenom důvěryhodný obsah. Provede to tak, že zkontroluje podpisy Authenticode obsahu, který se stahuje, a před instalací ověří, jestli je veškerý obsah důvěryhodný. Tím se prostředí udržuje v bezpečí před útoky, při kterých dojde k ohrožení bezpečnosti umístění pro stahování. Instalační program sady Visual Studio proto vyžaduje, aby bylo v počítači uživatele nainstalováno několik standardních a zprostředkujících certifikátů společnosti Microsoft. Pokud je počítač v aktuálním stavu web Windows Update, podpisové certifikáty jsou obvykle aktuální. Pokud je počítač připojen k Internetu, může během instalace aplikace Visual Studio aktualizovat certifikáty podle potřeby pro ověření podpisů souborů. Pokud je počítač v režimu offline, musí být certifikáty obnoveny jiným způsobem.

## <a name="how-to-refresh-certificates-when-offline"></a>Postup aktualizace certifikátů v režimu offline

Existují tři možnosti instalace nebo aktualizace certifikátů v prostředí offline.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Možnost 1 – Ruční instalace certifikátů ze složky rozložení

::: moniker range="vs-2017"

Když vytvoříte [rozložení sítě](../install/create-a-network-installation-of-visual-studio.md) nebo [místní mezipaměť offline](../install/create-an-offline-installation-of-visual-studio.md), stáhnou se nezbytné certifikáty do složky certifikáty. Certifikáty pak můžete ručně nainstalovat tak, že dvakrát kliknete na jednotlivé soubory certifikátů a potom kliknete na Průvodce správcem certifikátů. Pokud se zobrazí výzva k zadání hesla, ponechte prázdné.

**Aktualizace**: pro Visual Studio 2017 verze 15,8 Preview 2 nebo novější můžete certifikáty nainstalovat ručně tak, že kliknete pravým tlačítkem na jednotlivé soubory certifikátů, vyberete nainstalovat certifikát a potom kliknete na Průvodce správcem certifikátů.

::: moniker-end

::: moniker range=">=vs-2019"

Když vytvoříte [rozložení sítě](../install/create-a-network-installation-of-visual-studio.md) nebo [místní mezipaměť offline](../install/create-an-offline-installation-of-visual-studio.md), stáhnou se nezbytné certifikáty do složky certifikáty. Certifikáty můžete nainstalovat ručně tak, že kliknete pravým tlačítkem na jednotlivé soubory certifikátů, vyberete nainstalovat certifikát a pak kliknete na Průvodce správcem certifikátů. Pokud se zobrazí výzva k zadání hesla, ponechte prázdné.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Možnost 2 – distribuce důvěryhodných kořenových certifikátů v podnikovém prostředí

Pro podniky s offline počítači, které nemají nejnovější kořenové certifikáty, může správce pomocí pokynů na stránce [Konfigurace důvěryhodných kořenů a nepovolených certifikátů](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) tyto informace aktualizovat.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Možnost 3 – Instalace certifikátů v rámci skriptu nasazení sady Visual Studio

Pokud provádíte skriptování nasazení sady Visual Studio v prostředí offline na klientských pracovních stanicích, měli byste postupovat podle následujících kroků:

1. Zkopírujte [Nástroj Certificate Manager](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) do umístění pro instalaci rozložení sítě nebo do místní mezipaměti. Certmgr.exe není součástí samotného systému Windows, ale je k dispozici jako součást [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Vytvořte dávkový soubor s následujícími příkazy:

   ```shell
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root
   ```
   
   Případně můžete vytvořit dávkový soubor, který používá certutil.exe, který je dodáván se systémem Windows, s následujícími příkazy:
   
      ```shell
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Nasaďte dávkový soubor do klienta. Tento příkaz by měl být spuštěný z procesu se zvýšenými oprávněními.

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Jaké jsou soubory certifikátů ve složce certifikáty?

* **manifestRootCertificate. cer** obsahuje:
  * Kořenový certifikát: **Kořenová certifikační autorita společnosti Microsoft 2011**
* **manifestCounterSignRootCertificate. cer** a **vs_installer_opc. RootCertificate. cer** obsahuje:
  * Kořenový certifikát: **Kořenová certifikační autorita společnosti Microsoft 2010**
 
Instalační program pro Visual Studio vyžaduje, aby byly v systému nainstalovány pouze kořenové certifikáty. Všechny tyto certifikáty jsou vyžadovány pro systémy Windows 7 Service Pack 1, které nemají nainstalované nejnovější aktualizace systému Windows.

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Proč se certifikáty ze složky certifikáty nenainstalovaly automaticky?

Když je podpis ověřený v online prostředí, používají se k stažení a přidání certifikátů do systému rozhraní API systému Windows. Ověření, že certifikát je důvěryhodný a povolený prostřednictvím nastavení správy, probíhá během tohoto procesu. Tento proces ověřování nemůže být ve většině prostředí offline. Ruční instalace certifikátů umožní správcům rozlehlých sítí zajistit důvěryhodnost certifikátů a splňovat zásady zabezpečení jejich organizace.

## <a name="checking-if-certificates-are-already-installed"></a>Probíhá kontrola, zda jsou již certifikáty nainstalovány.

Jedním ze způsobů, jak ověřit instalaci systému, je postup:

1. Spusťte **mmc.exe**.<br/>
  a. Klikněte na **soubor** a pak vyberte **Přidat nebo odebrat modul snap-in**.<br/>
  b. Poklikejte na **certifikáty**, vyberte **účet počítače** a pak klikněte na **Další**.<br/>
  c. Vyberte možnost **místní počítač**, klikněte na tlačítko **Dokončit** a pak klikněte na tlačítko **OK**.<br/>
  d. Rozbalte položku **certifikáty (místní počítač)**.<br/>
  e. Rozbalte položku **Důvěryhodné kořenové certifikační autority** a pak vyberte možnost **certifikáty**.<br/>
    * V tomto seznamu vyhledejte nezbytné kořenové certifikáty.<br/>

   f. Rozbalte **zprostředkující certifikační autority** a pak vyberte **certifikáty**.<br/>
    * V tomto seznamu najdete požadované zprostředkující certifikáty.<br/>

2. Klikněte na **soubor** a pak vyberte **Přidat nebo odebrat modul snap-in**.<br/>
  a. Dvakrát klikněte na **certifikáty**, vyberte **Můj uživatelský účet**, klikněte na **Dokončit** a pak klikněte na **OK**.<br/>
  b. Rozbalte položku **Certifikáty – aktuální uživatel**.<br/>
  c. Rozbalte **zprostředkující certifikační autority** a pak vyberte **certifikáty**.<br/>
    * V tomto seznamu najdete požadované zprostředkující certifikáty.<br/>

Pokud názvy certifikátů nebyly ve sloupcích **vydaných** , musí být nainstalovány.  Pokud byl zprostředkující certifikát pouze v úložišti zprostředkujících certifikátů **aktuálního uživatele** , je k dispozici pouze pro uživatele, který je přihlášen. Je možné, že ho budete muset nainstalovat pro ostatní uživatele.

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

Po instalaci certifikátů na klientském počítači jste připraveni k [instalaci sady Visual Studio z místní mezipaměti](../install/create-an-offline-installation-of-visual-studio.md#step-3---install-visual-studio-from-the-local-cache)nebo k [nasazení sady Visual Studio ze sdílené složky rozložení sítě](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) do klientského počítače.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Vytvoření síťové instalace sady Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
* [Vytvoření offline instalace sady Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)

